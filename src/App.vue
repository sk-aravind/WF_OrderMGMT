<template>
	<div id="app" class="container">

	<nav class="navbar navbar-default">
	  <div class="container-fluid">
	    <!-- Brand and toggle get grouped for better mobile display -->
	    <div class="navbar-header">
	      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
	        <span class="sr-only">Toggle navigation</span>
	        <span class="icon-bar"></span>
	        <span class="icon-bar"></span>
	        <span class="icon-bar"></span>
	      </button>
	      <a class="navbar-brand" href="#">WindFlower</a>
	    </div>

	    <!-- Collect the nav links, forms, and other content for toggling -->
	    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
	      <ul class="nav navbar-nav">
	        <li v-on:click="view_selector='ordered'" v-bind:class="{ active: view_selector=='ordered' }" ><a>Orders</a></li>
	        <li v-on:click="view_selector='fulfilled'" v-bind:class="{ active: view_selector=='fulfilled' }"  ><a>Fullfilled</a></li>
	        <li v-on:click="view_selector='shipping'" v-bind:class="{ active: view_selector=='shipping' }"><a href="#">Shipping</a></li>
	        <li li v-on:click="view_selector='delivered'" v-bind:class="{ active: view_selector=='delivered' }"><a href="#">Delivered</a></li>
	  
	      </ul>
	      
	      <ul class="nav navbar-nav navbar-right">
	        
	        <li class="dropdown">
	          <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">Settings <span class="caret"></span></a>
	          <ul class="dropdown-menu">
	            <li><a href="#">Action</a></li>
	            <li><a href="#">Another action</a></li>
	            <li><a href="#">Something else here</a></li>
	            <li role="separator" class="divider"></li>
	            <li><a href="#">Separated link</a></li>
	          </ul>
	        </li>
	      </ul>
	    </div><!-- /.navbar-collapse -->
	  </div><!-- /.container-fluid -->
	</nav>


		<div class ="page-header">
			<h1>WindFlower Orders</h1>
			<button id="addnew" data-toggle="collapse" data-target="#demo" class="btn btn-default">Add Order</button>
		</div>

		

		<div class="panel panel-default collapse" id="demo">
			<div class="panel-heading">
				<h3>New Order</h3>
			</div>
			<div class="panel-body">

				<form id="form" class="form-horizontal" v-on:submit.prevent="addOrder">
					<div class="form-group ">
						<label class="control-label col-sm-2" for="orderFlower">Flower:</label>
						<div class="col-sm-9">
							<input type="text" id="orderFlower" class="form-control" v-model="newOrder.flower">
						</div>
					</div>
					<div class="form-group ">
						<label class="control-label col-sm-2" for="orderAddress">Address:</label>
						<div class="col-sm-9">
							<input type="text" id="orderAddress" class="form-control" v-model="newOrder.address">
						</div>	
					</div>
					<div class="form-group ">
						<label class="control-label col-sm-2" for="orderTiming">Timing:</label>
						<div class="col-sm-9">
						<div class="col-md-2">
							<input type="radio" id="one" value="9.00 - 10.30" v-model="newOrder.timing">
								<label for="one">9.00 - 10.30</label>
						</div>	
						<div class="col-md-2">	
							<input type="radio" id="two" value="10.30 - 13.00" v-model="newOrder.timing">
								<label for="two">10.30 - 13.00</label>
						</div>

						<div class="col-md-2">
							<input type="radio" id="two" value="13.30 - 15.00" v-model="newOrder.timing">
								<label for="two">13.30 - 15.00</label>
						</div>
						<div class="col-md-2">

							<input type="radio" id="two" value="15.30 - 18.00" v-model="newOrder.timing">
								<label for="two">15.30 - 18.00</label>

						</div>
						</div>
					</div>
					<div class="form-group ">
						<label class="control-label col-sm-2" for="orderCustomer">Customer:</label>
						<div class="col-sm-9">
							<input type="text" id="orderCustomer" class="form-control" v-model="newOrder.customer">
						</div>
					</div>
					<div class="form-group ">
						<label class="control-label col-sm-2" for="orderRecipient">Recipient:</label>
						<div class="col-sm-9">
							<input type="text" id="orderRecipient" class="form-control" v-model="newOrder.recipient">
						</div>
					</div>
					<div class="form-group ">
						<label class="control-label col-sm-2" for="orderID">Order ID:</label>
						<div class="col-sm-9">
							<input type="text" id="orderID" class="form-control" v-model="newOrder.orderID">
						</div>
					</div>
					<div class="form-group ">
						<label class="control-label col-sm-2" for="orderRemarks">Remarks:</label>
						<div class="col-sm-9">
							<input type="text" id="orderRemarks" class="form-control" v-model="newOrder.remarks">
						</div>
					</div>
			
					
					<input type="submit" class="btn center-block btn-primary" value="Add Order">
					
				</form>
				
			</div>
		</div>


		<div class="panel panel-default">
			<div class="panel-heading">
				<h3>Order Lists</h3>
			</div>
			<div class="panel-body">

				<table class="table table-responsive">
					<thead>

						<tr>
							<th>
								Flower
							</th>
							<th>
								Address
							</th>
							<th>
								Timing
							</th>
							<th>
								Customer
							</th>
							<th>
								Recipient
							</th>
							<th>
								Order ID
							</th>
							<th>
								Remarks
							</th>


							<th>
								Fulfilled
							</th>
							<th>
								Delete
							</th>
							
						</tr>

					</thead>
					<tbody>
						<tr v-for="order in orders" v-if="order.status==view_selector ">
							<td>
								{{order.flower}}
							<td>
								{{order.address}} 
							</td>
							<td>
								{{order.timing}} 
							</td>
							<td>
								{{order.customer}} 
							</td>
							<td>
								{{order.recipient}} 
							</td>
							<td>
								{{order.orderID}} 
							</td>
							<td>
								{{order.remarks}} 
							</td>
							
							<td>
							 <button class="btn btn-success" v-on:click="order.status='fulfilled'">Done</button>
							</td>
							<td>
								<span class="glyphicon glyphicon-trash" v-on:click="removeOrder(order)"></span>
							</td>
							
						</tr>
					</tbody>
				</table>
				
			</div>
		</div>

 
</template>

<script>
import Hello from './components/Hello'
import Firebase from 'firebase'
import toastr from 'toastr'


let config = {
	apiKey: "AIzaSyCbwINaGjth4CO6RmzrPetyeNAx8Tkl0dI",
	authDomain: "windflower-51a12.firebaseapp.com",
	databaseURL: "https://windflower-51a12.firebaseio.com",
	storageBucket: "windflower-51a12.appspot.com",
	messagingSenderId: "748155869507"
}

let app = Firebase.initializeApp(config);
let db = app.database();

let ordersRef = db.ref('orders');
let view_selector = 'ordered'

// console.log(booksRef) ;

export default {
	name: 'app',
	firebase: {
		orders:ordersRef
	},
	data (){
		
		return {
			view_selector: 'ordered',
			newOrder: {
				status:'ordered',
				flower:'',
				address:'',
				timing:'',
				customer:'',
				orderID:'',
				remarks:''
				
			}
		}
	},



	methods: {
		addOrder: function(){
			ordersRef.push(this.newOrder);
			this.newOrder.flower="";
			this.newOrder.address="";
			this.newOrder.timing="";
			this.newOrder.customer="";
			this.newOrder.recipient="";
			this.newOrder.orderID="";
			this.newOrder.remarks="";

		},
		removeOrder: function(order){
			console.log(order);
			ordersRef.child(order['.key']).remove();
			
		}

		

	}
}


</script>



<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;

	color: #2c3e50;
	margin-top: 60px;
}

#addnew {
	width: 28%;

}
</style>
