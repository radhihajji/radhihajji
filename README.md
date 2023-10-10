import pygame
# Define the screen size and title
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
SCREEN_TITLE = "Tennis"
# Initialize the Pygame library
pygame.init()
# Create the screen
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
# Set the window title
pygame.display.set_caption(SCREEN_TITLE)
# Create the game clock
clock = pygame.time.Clock()
# Create the player paddles
player1_paddle = pygame.Rect(50, 200, 10, 100)
player2_paddle = pygame.Rect(750, 200, 10, 100)
# Create the ball
ball = pygame.Rect(400, 300, 10, 10)
# Set the ball's velocity
ball_velocity_x = 100
ball_velocity_y = 100
# Create a function to handle the game logic
def update_game():
    # Update the player paddles' positions
    player1_paddle.y = pygame.mouse.get_pos()[1]
    player2_paddle.y = pygame.mouse.get_pos()[1]
    # Update the ball's position
    ball.x += ball_velocity_x
    ball.y += ball_velocity_y
    # Check if the ball has hit the top or bottom of the screen
    if ball.top < 0 or ball.bottom > SCREEN_HEIGHT:
        ball_velocity_y *= -1
    # Check if the ball has hit the left or right paddle
    if ball.colliderect(player1_paddle) or ball.colliderect(player2_paddle):
        ball_velocity_x *= -1
    # Check if the ball has gone off the screen
    if ball.left < 0 or ball.right > SCREEN_WIDTH:
        # Reset the ball's position and velocity
        ball.x = 400
        ball.y = 300
        ball_velocity_x = 100
        ball_velocity_y = 100
# Create a function to draw the game画面
def
