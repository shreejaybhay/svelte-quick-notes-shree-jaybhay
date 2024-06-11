//note app
<script>
  // @ts-nocheck
  
    let day = "";
    let month = "";
    let year = "";
    let years = "--", months = "--", days = "--";
    let showResult = false;
  
    function calculateDifference() {
      if (!day || !month || !year) return;
  
      const inputDate = new Date(year, month - 1, day);
      const currentDate = new Date();
  
      let totalDays = Math.floor((currentDate - inputDate) / (1000 * 60 * 60 * 24));
  
      const totalYears = Math.floor(totalDays / 365);
      totalDays -= totalYears * 365;
  
      const totalMonths = Math.floor(totalDays / 30);
      totalDays -= totalMonths * 30;
  
      years = totalYears;
      months = totalMonths;
      days = totalDays;
    }
  
    function showResults() {
      calculateDifference();
      showResult = true;
    }
  </script>
  <div class="flex items-center justify-center w-full h-screen">
    
  <div class="max-w-md p-8 mx-auto mt-10 bg-white shadow-lg rounded-2xl rounded-br-[150px]">
    <div class="grid grid-cols-3 gap-4 mb-8">
      <div class="flex flex-col">
        <!-- svelte-ignore a11y-label-has-associated-control -->
        <label class="mb-1 text-gray-600">Day</label>
        <input type="number" bind:value={day} placeholder="DD" class="p-3 font-bold border border-gray-300 rounded-md text-start" />
      </div>
      <div class="flex flex-col">
        <!-- svelte-ignore a11y-label-has-associated-control -->
        <label class="mb-1 text-gray-600">Month</label>
        <input type="number" bind:value={month} placeholder="MM" class="p-3 font-bold border border-gray-300 rounded-md text-start" />
      </div>
      <div class="flex flex-col">
        <!-- svelte-ignore a11y-label-has-associated-control -->
        <label class="mb-1 text-gray-600">Year</label>
        <input type="number" bind:value={year} placeholder="YYYY" class="p-3 font-bold border border-gray-300 rounded-md text-start" />
      </div>
    </div>
    
    <div class="relative mb-8">
      <hr class="border-t border-gray-300" />
      <button on:click={showResults} class="absolute right-0 px-4 py-4 text-white bg-purple-500 rounded-full -top-7 focus:outline-none">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
        </svg>
      </button>
    </div>
  
    <div class="text-3xl font-bold">
      <div class="mb-2">
        <span class="text-purple-500">{showResult ? years : '--'}</span> <span class="text-gray-600">years</span>
      </div>
      <div class="mb-2">
        <span class="text-purple-500">{showResult ? months : '--'}</span> <span class="text-gray-600">months</span>
      </div>
      <div>
        <span class="text-purple-500">{showResult ? days : '--'}</span> <span class="text-gray-600">days</span>
      </div>
    </div>
  </div>
</div>
  
  <style>
    /* Optional custom styles */
  </style>
  