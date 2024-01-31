<head>
	<style>
		body {
			margin: 0;
			padding: 0;
			display: flex;
			justify-content: center;
			align-items: center;
			height: 100vh;
			background: #f3f3f3;
			font-family: Arial, sans-serif;
		}

		.object {
			width: 50px;
			height: 50px;
			background-color: red;
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
			animation: move 10s infinite linear;
		}

		@keyframes move {
			0% {
				transform: translate(-50%, -50%) rotate(0deg) translate(200px) rotate(0deg);
			}

			100% {
				transform: translate(-50%, -50%) rotate(360deg) translate(200px) rotate(-360deg);
			}
		}

		.control-panel {
			position: fixed;
			bottom: 0;
			width: 100%;
			padding: 20px;
			background-color: #ddd;
			display: flex;
			justify-content: space-around;
			align-items: center;
			flex-wrap: wrap;
		}

		.control-panel input[type="range"] {
			width: 200px;
		}

		.control-panel label {
			margin-right: 10px;
		}

		.control-panel div {
			display: flex;
			align-items: center;
			margin: 10px;
		}
	</style>
</head>

<body>
	<div class="object"></div>

	<div class="control-panel">
		<div>
			<label for="speed-slider">Скорость</label>
			<input type="range" min="1" max="60" value="10" id="speed-slider">
    </div>

			<div>
				<label for="color-picker">Цвет квадрата</label>
				<input type="color" id="color-picker">
    </div>

				<div>
					<label for="size-slider">Размер квадрата</label>
					<input type="range" min="10" max="200" value="50" id="size-slider">
    </div>

					<div>
						<button id="color-change-button">Сменить цвета</button>
					</div>
				</div>

				<script>
					var speedSlider = document.getElementById('speed-slider');
    var colorPicker = document.getElementById('color-picker');
    var sizeSlider = document.getElementById('size-slider');
    var colorChangeButton = document.getElementById('color-change-button');
    var object = document.querySelector('.object');
    var colorChangeInterval;

    speedSlider.addEventListener('input', function() {
      var speed = speedSlider.value;
      object.style.animationDuration = speed + 's';
    });

    colorPicker.addEventListener('input', function() {
      var color = colorPicker.value;
      object.style.backgroundColor = color;
    });

    sizeSlider.addEventListener('input', function() {
      var size = sizeSlider.value;
      object.style.width = size + 'px';
      object.style.height = size + 'px';
    });

    colorChangeButton.addEventListener('click', function() {
      if (colorChangeInterval) {
        clearInterval(colorChangeInterval);
        colorChangeInterval = null;
      } else {
        colorChangeInterval = setInterval(function() {
          var color = '#' + Math.floor(Math.random()*16777215).toString(16);
          object.style.backgroundColor = color;
        }, 200);
      }
    });
				</script>
</body>

</html>
<head>
	<style>
		body {
			display: flex;
			align-items: center;
			justify-content: center;
			height: 100vh;
			margin: 0;
		}

		@keyframes rotate {
			0% {
				transform: rotate(0deg);
				background-color: red;
			}

			25% {
				transform: rotate(90deg);
				background-color: blue;
			}

			50% {
				transform: rotate(180deg);
				background-color: green;
			}

			75% {
				transform: rotate(270deg);
				background-color: yellow;
			}

			100% {
				transform: rotate(360deg);
				background-color: red;
			}
		}

		.square {
			width: 100px;
			height: 100px;
			background-color: red;
			animation: rotate 4s linear infinite;
		}
	</style>
</head>

<body>
	<div class="square"></div>
</body>

</html>
