![Raspi Zero GPIO ](https://github.com/txurtxil/ST7735R-LCD/blob/master/RaspiTftST7735r.jpg "Raspi Zero GPIO")

This is a userspace code for mapping raspberry pi default frame buffer (/dev/fb0) to a tft with st7735 driver. CPU USAGE = 3.2 to 4.5% at 20fps.
FPS can be increased by modifying the usleep(50000) value in main.c and also modifying the spi speed in st7735.c. 

Tested on pizero.

Advantage of this application:
   No need of any extra kernel module/driver.
	 No additional dependency even for gpio/spi drivers.
	 Easy to understand.
	 No need to create additional frame buffer.


![Raspi Zero GPIO ](https://3.bp.blogspot.com/-vDlWZNzxu_k/XKd1quyoLvI/AAAAAAAAxMM/MOrpUz_p-TUvslAun3eVEdbaKADigilcwCLcBGAs/s1600/tft_1.8.PNG "Raspi Zero GPIO")

PINOUT: (change st7735.h file to change the pin configuration)
	#define CS_PIN  8UL
	#define A0_PIN  24UL
	#define RST_PIN 25UL

  It is GPIO8, GPIO24, GPIO25 and not the pin based on 0,1,2,3 etc on the board.

![Raspi Zero GPIO ](https://github.com/txurtxil/ST7735R-LCD/blob/master/rpi_zero_io_pinouts.jpg "Raspi Zero GPIO")


Uso:
  Configura el fb para la pantalla: 
  1. modificar /boot/config.txt y reboot:
   framebuffer_width=160
   framebuffer_height=128
   framebuffer_depth=16
   
   2. Si queremos iniciar en el boot el lcd,copiar el binario "lcd" en /bin y
      editar /etc/rc.local e inculir antes de exit 0:
     
     do
        sleep 1
        sudo /bin/lcd
     done


  enable spi for first time using "sudo raspi-config"
   
  Then make this project
	 
   make clean

    make

    sudo ./run


	 Now tty1 should be mapped to the LCD.. You can type on pi keyboad connected to usb/usb hub to see changes on display.

	 You can try ./video1.sh to play test1 video sample.
	 Similarly other examples (video2.sh, rtsp_test.sh etc)


	 You can try typing startx to start X GUI as well.


Visit http://blog.vinu.co.in for more details.

mail: m a i l @ v i n u . c o . i n 


THANKS 

:)
