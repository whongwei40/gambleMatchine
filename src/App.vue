<template>
	<div id="app">
		<div class="machine">
			<h2 class="title">机器</h2>
			<div class="count count1">{{value1}}</div>
			<div class="count count2">{{value2}}</div>
			<div class="count count3">{{value3}}</div>
			<div class="count count4">{{value4}}</div>
			<div class="count count5">{{value5}}</div>
			<div class="count count6">{{value6}}</div>
			<div class="count count7">{{value7}}</div>
			<div class="count count8">{{value8}}</div>
			<div class="count count9">{{value9}}</div>
			<div class="count count10">{{value10}}</div>
			<div class="count count11">{{value11}}</div>
			<div class="count count12">{{value12}}</div>
			<div class="square-container">
				<div class="square big" id="12">12</div>
				<div class="square small" id="11">11</div>
				<div class="square big" id="10">10</div>
				<div class="square small" id="9">9</div>
				<div class="square big" id="8">8</div>
				<div class="square small" id="7">7</div>
				<div class="square big" id="6">6</div>
				<div class="square small" id="5">5</div>
				<div class="square big" id="4">4</div>
				<div class="square small" id="3">3</div>
				<div class="square big" id="2">2</div>
				<div class="square small" id="1">1</div>
				<div class="square" id="0"></div>
				<div class="square small" id="25">12</div>
				<div class="square big" id="24">11</div>
				<div class="square small" id="23">10</div>
				<div class="square big" id="22">9</div>
				<div class="square small" id="21">8</div>
				<div class="square big" id="20">7</div>
				<div class="square small" id="19">6</div>
				<div class="square big" id="18">5</div>
				<div class="square small" id="17">4</div>
				<div class="square big" id="16">3</div>
				<div class="square small" id="15">2</div>
				<div class="square big" id="14">1</div>
				<div class="square" id="13"></div>
			</div>

			<div class="buttons">
				<button v-for="i in 12" :key="i" @click="bet(i)">{{ i }}</button>
			</div>
			<button class="start" @click="game()">开始</button>
			<div class="login">
				<input type="number" v-model="amount" placeholder="请输入金额">
				<button @click="recharge">充值</button>
			</div>
			<div class="balance">余额：{{balance}}</div>
			<div class="income">收益：{{income}}</div>
		</div>
	</div>
</template>
<style>
	.count {
		font-size: 20px;
	}

	.count:nth-child(2) {
		position: absolute;
		top: 632px;
		left: 266px;
	}

	.count:nth-child(3) {
		position: absolute;
		top: 632px;
		left: 359px;
	}

	.count:nth-child(4) {
		position: absolute;
		top: 632px;
		left: 452px;
	}

	.count:nth-child(5) {
		position: absolute;
		top: 632px;
		left: 540px;
	}

	.count:nth-child(6) {
		position: absolute;
		top: 632px;
		left: 630px;
	}

	.count:nth-child(7) {
		position: absolute;
		top: 632px;
		left: 715px;
	}

	.count:nth-child(8) {
		position: absolute;
		top: 632px;
		left: 806px;
	}

	.count:nth-child(9) {
		position: absolute;
		top: 632px;
		left: 893px;
	}

	.count:nth-child(10) {
		position: absolute;
		top: 632px;
		left: 989px;
	}

	.count:nth-child(11) {
		position: absolute;
		top: 632px;
		left: 1077px;
	}

	.count:nth-child(12) {
		position: absolute;
		top: 632px;
		left: 1164px;
	}

	.count:nth-child(13) {
		position: absolute;
		top: 632px;
		left: 1259px;
	}

	.balance {
		position: absolute;
		top: 6%;
		right: 17%;
		font-size: 2em;
	}

	.login {
		position: absolute;
		top: 12%;
		right: 2%;
		display: flex;
		flex-direction: column;
	}

	.income {
		position: absolute;
		top: 6%;
		left: 25%;
		font-size: 2em;
	}

	.title {
		position: absolute;
		top: 0%;
	}

	.machine {
		height: 100vh;
		width: 100vw;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	#app {
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin: 0;
		padding: 0;
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
	}

	.buttons {
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 20px;
		position: absolute;
		bottom: 30px;
	}

	.buttons button {
		margin: 0 10px;
		font-size: 2em;
		width: 70px;
		height: 70px;
		border-radius: 0;

	}

	.start {
		width: 70px;
		height: 70px;
		position: absolute;
		right: 100px;
		bottom: 30px;
	}

	html,
	body {
		height: 100%;
		margin: 0;
		padding: 0;
	}

	.square-container {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-evenly;
		align-content: space-evenly;
		width: 1500px;
		height: 580px;
		position: relative;
	}

	.square {
		width: 100px;
		height: 100px;
		background-color: lightblue;
		border: 1px solid black;
		display: flex;
		justify-content: center;
		align-items: center;
		position: absolute;
		top: 0;
		left: 0;
		transition: background-color 0.5s ease;
	}

	.square.small {
		/* CSS 样式 */
		font-size: 20px;
	}

	.square.big {
		/* CSS 样式 */
		font-size: 32px;
	}

	.square.active {
		/* 设置变亮后的背景颜色 */
		background-color: orangered;
	}


	.square:nth-child(13) {
		top: 200px;
		left: 300px;
	}

	.square:nth-child(26) {
		top: 200px;
		left: 1200px;
	}

	.square:nth-child(12) {
		top: 100px;
		left: 300px;
	}

	.square:nth-child(11) {
		top: 0px;
		left: 300px;
	}

	.square:nth-child(10) {
		top: 0px;
		left: 400px;
	}

	.square:nth-child(9) {
		top: 0px;
		left: 500px;
	}

	.square:nth-child(8) {
		top: 0px;
		left: 600px;
	}

	.square:nth-child(7) {
		top: 0px;
		left: 700px;
	}

	.square:nth-child(6) {
		top: 0px;
		left: 800px;
	}

	.square:nth-child(5) {
		top: 0px;
		left: 900px;
	}

	.square:nth-child(4) {
		top: 0px;
		left: 1000px;
	}

	.square:nth-child(3) {
		top: 0px;
		left: 1100px;
	}

	.square:nth-child(2) {
		top: 0px;
		left: 1200px;
	}

	.square:nth-child(1) {
		top: 100px;
		left: 1200px;
	}

	.square:nth-child(14) {
		top: 300px;
		left: 300px;
	}

	.square:nth-child(15) {
		top: 400px;
		left: 300px;
	}

	.square:nth-child(16) {
		top: 400px;
		left: 400px;
	}

	.square:nth-child(17) {
		top: 400px;
		left: 500px;
	}

	.square:nth-child(18) {
		top: 400px;
		left: 600px;
	}

	.square:nth-child(19) {
		top: 400px;
		left: 700px;
	}

	.square:nth-child(20) {
		top: 400px;
		left: 800px;
	}

	.square:nth-child(21) {
		top: 400px;
		left: 900px;
	}

	.square:nth-child(22) {
		top: 400px;
		left: 1000px;
	}

	.square:nth-child(23) {
		top: 400px;
		left: 1100px;
	}

	.square:nth-child(24) {
		top: 400px;
		left: 1200px;
	}

	.square:nth-child(25) {
		top: 300px;
		left: 1200px;
	}

	/* ...and so on for each square */
</style>

<script>
	import axios from 'axios';

	export default {
		name: 'App',
		methods: {
			sendRequest(value) {
				console.log('send request with value:', value)
			},
			recharge() {
				if (!this.amount) {
					alert('请输入充值金额');
					return;
				}
				const amount = this.amount;
				this.amount = '';
				// 将输入的金额赋给显示框
				this.balance = this.balance += amount;
			},
			bet(value) {
				this.balance += this.totalEarnings;
				this.totalEarnings = 0;
				this.income = 0;
				if (this.balance <= 0) {
					alert('余额不足，请充值！');
					return;
				}
				// 如果用户已经开始输入数字，则清空数组
				console.log(this.isInputting)
				if (this.isInputting) {
					this.initInput()
					// 将变量重新设置为 false，表示用户已经下注完成
					this.isInputting = false;
				}
				// 玩家选择选项
				this.inputEvent.push(value);
				this.balance -= 1.0; // 消耗一个金额
				const propertyName = 'value' + value;
				this[propertyName]++;
				this.hasStarted = false;

			},
			game() {
				const inputEvent = this.inputEvent
				const totalEarnings = this.totalEarnings
				const balance = this.balance
				this.balance += this.totalEarnings;
				this.totalEarnings = 0;
				let randomOption = Math.floor(Math.random() * 25); // 生成0-24之间的随机结果
				if (this.isInputting) {
					if (balance < inputEvent.length) {
						return;
					}
					this.balance -= inputEvent.length;
				}
				this.isInputting = true;
				//将此次下注存入到上次下注的数组
				this.lastEvent = this.inputEvent;
				this.income = 0;

				var divEle = document.getElementById(randomOption);
				if (divEle.classList.contains("small")) {
					// 获取当前和目标单元格
					this.actionMovine(randomOption.toString())
					if (inputEvent.includes(randomOption)) {
						//小的1-6的收益倍数是8倍
						const earnings = 8.0 * inputEvent.filter((n) => n === randomOption).length;
						this.totalEarnings = earnings;
						console.log(`恭喜你中奖了，收益为： ${earnings}`);
					}
				} else if (divEle.classList.contains("big")) {
					this.actionMovine(randomOption.toString())
					randomOption -= 13;
					if (inputEvent.includes(randomOption)) {
						// 大的1-6的收益倍数是20倍
						const earnings = 20.0 * inputEvent.filter((n) => n === randomOption).length;
						this.totalEarnings = earnings;
						console.log(`恭喜你中奖了， 收益为: ${earnings}`);
					}
				} else {
					this.actionMovine(randomOption.toString())
				}

			},
			initInput() {
				this.value1 = 0;
				this.value2 = 0;
				this.value3 = 0;
				this.value4 = 0;
				this.value5 = 0;
				this.value6 = 0;
				this.value7 = 0;
				this.value8 = 0;
				this.value9 = 0;
				this.value10 = 0;
				this.value11 = 0;
				this.value12 = 0;
				this.inputEvent = [];
			},
			actionMovine(index) {
				var endDiv = document.getElementById(index);
				var nowDiv = document.getElementById(this.nowIndexId);
				this.nowIndexId = endDiv.id;
				// 将方块设置为初始状态
				nowDiv.classList.remove('active');
				//计算什么时候停下来
				let nowId = parseInt(nowDiv.id);
				let endId = parseInt(endDiv.id);
				let j = this.getNumberOfSteps(nowId, endId);
				// 定义需要转的圈数，默认转3圈
				for (var i = 0; i < j; i++) {
					var nextId = this.getNextNumber(parseInt(nowDiv.id));
					var nextDiv = document.getElementById(nextId);
					setTimeout((function(div) {
						return function() {
							div.classList.add('active');
						};
					})(nextDiv), i * 80);
					if (i < j - 1) {
						setTimeout((function(div) {
							return function() {
								div.classList.remove('active');
							};
						})(nextDiv), i * 80 + 500);
					}
					nowDiv = nextDiv;
				}
				setTimeout(() => {
					this.income = this.totalEarnings;
				}, j * 80 + 500);
			},
			getNextNumber(number) {
				return (number + 1) % 26; // 取余数，避免返回的是26
			},
			getNumberOfSteps(nowId, endId) {
				if (nowId > endId) {
					return 26 - Math.abs(nowId - endId);
				}
				return 26 + Math.abs(nowId - endId);
			}
		},
		data() {
			return {
				amount: '',
				balance: 0,
				inputEvent: [],
				isInputting: false,
				totalEarnings: 0,
				value1: 0,
				value2: 0,
				value3: 0,
				value4: 0,
				value5: 0,
				value6: 0,
				value7: 0,
				value8: 0,
				value9: 0,
				value10: 0,
				value11: 0,
				value12: 0,
				nowIndexId: 0,
				income: 0

			}
		}
	}
</script>
