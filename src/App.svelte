<script>
import { link } from "fs";
  import { onMount } from "svelte";
import { each } from "svelte/internal";
  let src =
    "";
  let name = "S71211";
  let st='a';
  $: url = `data/cars?plate=${st}`;
  $: data = [{'id_car': 0, "brand": "None", "driver": "None", "tel_number": "None","plate": "c"}];
  onMount(async function() {
	  setInterval(async () => {
		const response = await fetch(url);
    const json = await response.json();
    data = json;

	  }, 2000)
  });
  function car_crud(st) {
    // console.log(st);
    // const response = fetch(`data/cars?plate=${st}`);
    // const json = response.json();
    // var strJSON =String.parseJSON(response);
    // var obj = eval( "(" + strJSON + ")" );
    // alert(obj.plate);
    // data = json;
    // console.log(st);
    document.getElementById("k").innerHTML="plate = "+data[0]['plate']+" driver = "+data[0]['driver'];
   }
</script>

<style>
  .footer {
    display: flex;
    width: 100%;
    height: 64px;
    top: 0px;
    left: 0px;
    font-size: 2em;
    background-color: aquamarine;
    justify-content: center;
    align-items: center;
  }
  .container {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 100px;
  }

  .container * {
    display: inline-block;
  }
  .led {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background-color: rgba(117, 31, 25, 0.815);
    margin-right: 80px;
  }

  .btn {
    width: 120px;
    height: 80px;
    background-color: rgba(117, 31, 25, 0.815);
  }

  .led.active {
    background-color: rgba(18, 238, 18, 0.815);
  }

  .btn.active {
    background-color: rgba(20, 238, 20, 0.815);
  }

  body {
    padding-bottom: 50px;
  }
</style>


<body>
  <div class="footer">car booking system</div>
  <br />
  <ul>
    <center>
      <img {src} alt="{name} demo" />
    </center>

  </ul>
  <div class="container">
    <div class="led" class:active={data[0]['driver']==""} />
    <div class="btn" class:active={data[0]['plate']==undefined} />
  </div>
  <div class="container" >
    <input bind:value={st}>
    <button	on:click={car_crud(st)}>search</button>
    <p id='k'></p>
  </div>

</body>






<!-- 
<script>
  import { onMount } from "svelte";
  let src =
    "";
  let name = "S71211";
  let st='st';
  export let url = `data/cars?plate=${st}`;
   let data = {"/data/cars/driver": false, "/data/cars/plate": false};
  onMount(async function() {
	  setInterval(async () => {
		  const response = await fetch(url);
    const json = await response.json();
    data = json;
    
    console.log(data.key);
	  }, 1000)
    console.log("sdfsdf");
    const response = await fetch(url);
    const json = await response.json();
    data = json;
  });
</script>

<style>
  .footer {
    display: flex;
    width: 100%;
    height: 64px;
    top: 0px;
    left: 0px;
    font-size: 2em;
    background-color: aquamarine;
    justify-content: center;
    align-items: center;
  }
  .container {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 100px;
  }

  .container * {
    display: inline-block;
  }
  .led {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background-color: rgba(117, 31, 25, 0.815);
    margin-right: 80px;
  }

  .btn {
    width: 120px;
    height: 80px;
    background-color: rgba(7, 71, 50, 0.836);
  }

  .led.active {
    background-color: rgba(245, 77, 65, 0.815);
  }

  .btn.active {
    background-color: rgba(91, 238, 189, 0.836);
  }

  body {
    padding-bottom: 50px;
  }
</style>


<body>
  <div class="footer">car booking system</div>
  <br />
  <ul>
    <center>
      <img {src} alt="{name} demo" />
    </center>

  </ul>
  <div class="container">
    <div class="led" class:active={data['/data/cars/driver']} />
    <div class="btn"  class:active={data['/data/cars/plate']} />
  </div>
  <div class="container">
  <input bind:value={st} placeholder="please enter">
  </div>

</body> -->
