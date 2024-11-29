# Interfacing a 4x4 matrix keypad

## Aim: 
To simulate the interface of a 4x4 matrix keypad to ARM controller and display the output on 16X2 LCD for arithmetic operation only.

## Components required: 
STM32 CUBE IDE, Proteus 8 simulator .

## Keypad layout
![image](https://github.com/user-attachments/assets/5479b0c7-3c87-4f17-88f3-2aff6268e632)

## CIRCUIT DIAGRAM 
![image](https://github.com/user-attachments/assets/e4aaeb52-ce4e-4ced-8362-560cd211aff0)
 
## Program
### Name : SWETHA S

### Reg no : 212222230155

```c
#include "main.h"
#include "lcd.h"
#include "stdbool.h"
bool col1,col2,col3,col4;
Lcd_PortType ports[] = {GPIOA,GPIOA,GPIOA,GPIOA};
Lcd_PinType pins[] = {GPIO_PIN_3,GPIO_PIN_2,GPIO_PIN_1,GPIO_PIN_0};
Lcd_HandleTypeDef lcd;

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

void key()
{
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_RESET);
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);

		  col1 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_4);
		  col2 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_5);
		  col3 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_6);
		  col4 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7);
		  Lcd_cursor(&lcd, 0,1);
		  if(!col1)
		  {
			  Lcd_string(&lcd, "Key 7\n");
			  HAL_Delay(3000);
		  }
		  else if(!col2)
		  {
		  Lcd_string(&lcd, "Key 8\n");
		  HAL_Delay(3000);
		  }
		  else if(!col3)
		  {
		  Lcd_string(&lcd, "Key 9\n");
		  HAL_Delay(3000);
		  }
		  else if(!col4)
		  {
		  Lcd_string(&lcd, "Key %\n");
		  HAL_Delay(3000);
		  }
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_RESET);
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);
		  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);

		  		  col1 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_4);
		  		  col2 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_5);
		  		  col3 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_6);
		  		  col4 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7);
		  		  Lcd_cursor(&lcd, 0,1);
		  		  if(!col1)
		  		  {
		  			  Lcd_string(&lcd, "Key 4\n");
		  			  HAL_Delay(3000);
		  		  }
		  		  else if(!col2)
		  		  {
		  		  Lcd_string(&lcd, "Key 5\n");
		  		  HAL_Delay(3000);
		  		  }
		  		  else if(!col3)
		  		  {
		  		  Lcd_string(&lcd, "Key 6\n");
		  		  HAL_Delay(3000);
		  		  }
		  		  else if(!col4)
		  		  {
		  		  Lcd_string(&lcd, "Key *\n");
		  		  HAL_Delay(3000);
		  		  }

				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);
				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_RESET);
				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_SET);

				  col1 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_4);
				  col2 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_5);
				  col3 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_6);
				  col4 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7);
				  Lcd_cursor(&lcd, 0,1);
				  if(!col1)
				  {
					  Lcd_string(&lcd, "Key 1\n");
					  HAL_Delay(3000);
				  }
				  else if(!col2)
				  {
				  Lcd_string(&lcd, "Key 2\n");
				  HAL_Delay(3000);
				  }
				  else if(!col3)
				  {
				  Lcd_string(&lcd, "Key 3\n");
				  HAL_Delay(3000);
				  }
				  else if(!col4)
				  {
				  Lcd_string(&lcd, "Key -\n");
				  HAL_Delay(3000);
				  }

				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0, GPIO_PIN_SET);
				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_1, GPIO_PIN_SET);
				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_2, GPIO_PIN_SET);
				  HAL_GPIO_WritePin(GPIOC, GPIO_PIN_3, GPIO_PIN_RESET);

				  col1 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_4);
				  col2 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_5);
				  col3 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_6);
				  col4 = HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_7);
				  Lcd_cursor(&lcd, 0,1);
				  if(!col1)
				  {
					  Lcd_string(&lcd, "Key On/c \n");
					  HAL_Delay(3000);
				  }
				  else if(!col2)
				  {
				  Lcd_string(&lcd, "Key 0\n");
				  HAL_Delay(3000);
				  }
				  else if(!col3)
				  {
				  Lcd_string(&lcd, "Key =\n");
				  HAL_Delay(3000);
				  }
				  else if(!col4)
				  {
				  Lcd_string(&lcd, "Key +\n");
				  HAL_Delay(3000);
				  }
Lcd_clear(&lcd);



}

int main(void)
{

  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  lcd = Lcd_create(ports,pins,GPIOB,GPIO_PIN_0,GPIOB,GPIO_PIN_1,LCD_4_BIT_MODE);
  while (1)
  {
      key();
  }
}

  void SystemClock_Config(void)
  {
    RCC_OscInitTypeDef RCC_OscInitStruct = {0};
    RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};
    __HAL_RCC_PWR_CLK_ENABLE();
    __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2);

    RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_HSI;
    RCC_OscInitStruct.HSIState = RCC_HSI_ON;
    RCC_OscInitStruct.HSICalibrationValue = RCC_HSICALIBRATION_DEFAULT;
    RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
    if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
    {
      Error_Handler();
    }

    RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK|RCC_CLOCKTYPE_SYSCLK
                                |RCC_CLOCKTYPE_PCLK1|RCC_CLOCKTYPE_PCLK2;
    RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_HSI;
    RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
    RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
    RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;

    if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
    {
      Error_Handler();
    }
  }


  static void MX_GPIO_Init(void)
  {
    GPIO_InitTypeDef GPIO_InitStruct = {0};


    __HAL_RCC_GPIOC_CLK_ENABLE();
    __HAL_RCC_GPIOA_CLK_ENABLE();
    __HAL_RCC_GPIOB_CLK_ENABLE();

    HAL_GPIO_WritePin(GPIOC, GPIO_PIN_0|GPIO_PIN_1|GPIO_PIN_2|GPIO_PIN_3, GPIO_PIN_RESET);
    HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0|GPIO_PIN_1|GPIO_PIN_2|GPIO_PIN_3, GPIO_PIN_RESET);
    HAL_GPIO_WritePin(GPIOB, GPIO_PIN_0|GPIO_PIN_1, GPIO_PIN_RESET);

    /*Configure GPIO pins : PC0 PC1 PC2 PC3 */
    GPIO_InitStruct.Pin = GPIO_PIN_0|GPIO_PIN_1|GPIO_PIN_2|GPIO_PIN_3;
    GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
    GPIO_InitStruct.Pull = GPIO_NOPULL;
    GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
    HAL_GPIO_Init(GPIOC, &GPIO_InitStruct);

    /*Configure GPIO pins : PA0 PA1 PA2 PA3 */
    GPIO_InitStruct.Pin = GPIO_PIN_0|GPIO_PIN_1|GPIO_PIN_2|GPIO_PIN_3;
    GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
    GPIO_InitStruct.Pull = GPIO_NOPULL;
    GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
    HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

    /*Configure GPIO pins : PC4 PC5 PC6 PC7 */
    GPIO_InitStruct.Pin = GPIO_PIN_4|GPIO_PIN_5|GPIO_PIN_6|GPIO_PIN_7;
    GPIO_InitStruct.Mode = GPIO_MODE_INPUT;
    GPIO_InitStruct.Pull = GPIO_PULLUP;
    HAL_GPIO_Init(GPIOC, &GPIO_InitStruct);

    /*Configure GPIO pins : PB0 PB1 */
    GPIO_InitStruct.Pin = GPIO_PIN_0|GPIO_PIN_1;
    GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
    GPIO_InitStruct.Pull = GPIO_NOPULL;
    GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
    HAL_GPIO_Init(GPIOB, &GPIO_InitStruct);

  }

  void Error_Handler(void)
  {
    __disable_irq();
    while (1)
    {
    }

  }

  #ifdef  USE_FULL_ASSERT

  void assert_failed(uint8_t *file, uint32_t line)
  {

  }
  #endif /* USE_FULL_ASSERT */

```

## Output screen shots of proteus
![Screenshot 2024-11-11 211323](https://github.com/user-attachments/assets/6ee003bd-d834-4a9b-a6d1-809c4d071587)

![Screenshot 2024-11-11 211201](https://github.com/user-attachments/assets/45363509-51da-41b2-9e74-3d74cc96fde3)

## Result :
Interfaced a 4x4 matrix keypad with ARM microcontroller and displayed the output on 16X2 LCD for arithmetic operation in simulation.
