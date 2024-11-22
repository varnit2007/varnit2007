<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rose Bouquet Animation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #f4f4f4;
        }

        .canvas-container {
            position: relative;
            width: 600px;
            height: 400px;
            border: 2px solid #000;
            background-color: white;
        }

        .rose {
            position: absolute;
            width: 50px;
            height: 50px;
            background-image: url('https://example.com/rose.png'); /* Replace with your rose image URL */
            background-size: cover;
        }

        .button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #e74c3c;
            color: white;
            font-size: 16px;
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <div class="canvas-container" id="canvas-container">
        <!-- Roses will be animated here -->
    </div>

    <button class="button" onclick="animateBouquet()">Click to Animate Bouquet</button>

    <script>
        function animateBouquet() {
            // Set up initial positions for roses
            const positions = [
                { x: 50, y: 150 },
                { x: 150, y: 150 },
                { x: 250, y: 150 },
                { x: 350, y: 150 },
                { x: 450, y: 150 }
            ];

            const canvas = document.getElementById('canvas-container');
            
            // Create roses and add them to the canvas
            const roses = positions.map((position, index) => {
                const rose = document.createElement('div');
                rose.classList.add('rose');
                rose.style.left = `${position.x}px`;
                rose.style.top = `${position.y}px`;
                canvas.appendChild(rose);
                return rose;
            });

            // Animate the roses
            let count = 0;
            function moveRoses() {
                roses.forEach((rose, index) => {
                    // Move roses horizontally and vertically
                    let newX = positions[index].x + (count * 10);
                    let newY = positions[index].y + (index % 2 === 0 ? 20 : -20);
                    rose.style.left = `${newX}px`;
                    rose.style.top = `${newY}px`;
                });

                count++;
                if (count < 30) {
                    requestAnimationFrame(moveRoses); // Repeat animation
                }
            }

            // Start animation
            moveRoses();
        }
    </script>

</body>
</html>

