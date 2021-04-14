# ESPGIF
ESPGIF is a project which uses an ESP8266, and an SSD1351 OLED display to display a GIF! This project has the Arduino Code and a tool to convert the GIF into a byte array.
# How do I use it?!
This a quick tutorial on how to use the library.
## Step 1: Setup
You will need:
### Hardware
  - [An ESP8266](https://www.amazon.com/HiLetgo-Internet-Development-Wireless-Micropython/dp/B010O1G1ES)
  - [A SSD1351 OLED display](https://www.amazon.com/1-5inch-Interface-Raspberry-Examples-Provided/dp/B07D9NVJPZ)
  - [perfboard](https://www.amazon.com/dp/B0896YPD8F/ref=sspa_dk_detail_1?psc=1&pd_rd_i=B0896YPD8F&pd_rd_w=YeZDT&pf_rd_p=085568d9-3b13-4ac1-8ae4-24a26c00cb0c&pd_rd_wg=WL5Tr&pf_rd_r=GHDMVCPPV0WKQYS7Q2P3&pd_rd_r=2fb5e5ac-5647-4ac5-b9f6-d883cd38286a&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUExSUFXQjhBRzQ2TTRSJmVuY3J5cHRlZElkPUEwNDAwMDAyM0EwOU1GS0RQQVVETCZlbmNyeXB0ZWRBZElkPUEwNTA0NzA0MkUzUExKVFMzUllFMyZ3aWRnZXROYW1lPXNwX2RldGFpbCZhY3Rpb249Y2xpY2tSZWRpcmVjdCZkb05vdExvZ0NsaWNrPXRydWU=)
### Software
  - Python 3.7
    - Pip
    - The [PILLOW Library](https://pillow.readthedocs.io/)
    - [TKinter](https://docs.python.org/3/library/tkinter.html) (comes preinstalled with newer versions of python)
  - Arduino IDE
    - I have a repository with the modded Adafruit GFX (Allows for fast SPI transfers)
    - The Adafruit_SSD1351 library
    - Note: Both of the libraries are bundled in the "libraries" folder.
## Step 2: Setting the stuff up
Make sure you have all of the stuff listed above. If not, download and/or buy the required materials.

Go ahead and download the repo and unzip it.
- Drag the files in the `libraries` folder into the Arduino's `libraries` folder, or just use the library importer.

Drag the `GIFDisplay` folder into your Arduino projects folder, and open the `GIFDisplay.ino` script.
There are two files:
- `GIFDisplay.ino`
  - Contains code to display the data.
- `GIF.h`
  - Contains the actual image data

Drag the "GIFConvert" folder wherever you want (I recommend your "Documents" folder)

## Step 3: Wiring
Now that you've set up the project, let's actually display a GIF!

Here's the wiring diagram:

 OLED | ESP8266 
 ---- | ------- 
 SCLK | GPIO14  
 MOSI | GPIO13  
 DC   | GPIO5   
 CS   | GPIO15  
 RST  | GPIO4   

Note: The SCLK and MOSI pin mappings are immutable because the library _requires_ hardware SPI for a viewable framerate.

Once you have the pins connected go ahead and upload the sketch. If you did it right, you should see a spinning globe!
## Step 4: Displaying your own GIFs!
So, you wanna display your own GIF? 

Don't worry, this is going to be easy!

Remember the GIFConvert folder? Go ahead and open it and find the python script called, `GIFConvert.py`. Run it. It'll open a file selector. Choose your desired GIF, and press "Open". It will convert the image into an Arduino-readable format and open a .txt file containing the byte array. 

Use Ctrl+A/⌘+A to select all of the text in the open file, and use Ctrl+C/⌘+C to copy it to your clipboard.
Open the `GIF.h` file in the `GIFDisplay` folder, and use Ctrl+A/⌘+A to select all of the text, and then Ctrl+V/⌘+V to copy over the text.
Upload the code, and you should see the updated GIF!

If there is an error compiling, the GIF is probably too big. Choose a shorter/ lower framerate GIF and repeat this process.
