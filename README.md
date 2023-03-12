# ATMega328P-Blink
code written in C language for an ATmega328P microcontroller. The purpose of the code is to blink an LED connected to the PB0 pin of the microcontroller with a delay of 10ms.

The code uses Timer0 of the ATmega328P to generate a delay of 5ms. The Timer0 is configured to use the system clock (CK) with a prescaler of 64. The timer is loaded with a value of 178, which is calculated based on the formula:

Timer value = 256 - (delay time / clock time)

In this case, the delay time is 5000 microseconds (5ms) and the clock time is 64 microseconds (1/16MHz * 64 = 4 microseconds). Therefore, the timer value is 256 - (5000 / 64) = 178.

Once the timer is configured, the code enters a loop where it turns on the LED, waits for 5ms using the delay5ms() function, turns off the LED, and waits for another 5ms using the same function.

The delay5ms() function uses a busy-wait loop to wait for the timer to overflow. It checks the Timer/Counter0 Overflow Flag Register (TIFR0) to see if the timer has overflowed. If the flag is not set, it continues to loop. Once the flag is set, it turns off the timer and clears the flag.
