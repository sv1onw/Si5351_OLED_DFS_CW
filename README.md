# Si5351_OLED_DFS_CW
Modified version of Si5351_OLED_DFS for simple CW use or DC receiver.

This is a very minimalistic 20meter Digital Frequency Synthesizer with 0.96 or 1.3 inch 128x64 OLED Display for Ham-radio use.

This is a sketch to control a Silicon Labs Si5351a board produced by Floating Ground - SV1AFN Lab with an Arduino Nano, Uno, ProMini board. It uses a cheap no-name OLED with the above specs having a SSD1306 controller.The DFS has very minimalistic functions such as Frequency Change, Frequency Step Control, and predefined Frequency Limits to suit CW needs. Upper limit can be changed to 14.350 MHz if the DFS is to be used with a DC receiver.

The project has been built as a Digital Frequency Synthesiser to give 20 meter Band coverage from 14.000- 14100 MHz to any CW QRP transmitter or DC receiver.

The sketch that inspired me, is the work of Antony Watts, M0IFA and I have amended it to cover my needs as a 20 meters ONLY DFS.

Schematics for using an Arduino Nano are attached together with pics of my project and the schematic of a broadband RF amplifier sold in kit form, from FLOATING GROUND by SV1AFN (https://www.sv1afn.com/2n5109.html). This amplifier producing +23dBm, without the -6dB attenuator (R6 and R8 omitted, R7 replaced with a jumper), is used as QRP/p TX amplifier. I have also included a one transistor Keying circuit to be used when sending CW.

To compile the sketch without producing errors, you will need to have Oliver Kraus U8g2 very fine display library installed in your IDE, as well as Jason Mildrum's, NT7S, latest version of fabulous Si5351 library (Etherkit/Si5351Arduino) and copy Rotary.cpp, Rotary.h and Oled.h files from this repository here, inside the folder where "CW_20-DFS_v1.1.ino" file will reside. Please do that before verifying or uploading the sketch.

Reading the comments within the sketch will help you to become familiar with the program's parameters such as frequency limits, start frequency,as well as how to offset the Si5351a board's Crystal nominal frequency of 27.000000 MHz to the actual frequency value of your board (usually +/- 100 Hz to 500 Hz). You can check the accuracy of your produced Frequency square waveform (I have chosen 8.000000 MHz) by connecting one of the three outputs (CLK2) to a Frequency Counter and measure the deviation, or use a Shotwave Receiver in AM mode to zero beat the produced signal (you need to uncoment line 55 in the code for that). The sketch has currently my board's Crystal CALIBRATION value. If you use the same type of Si5351a board, there should not be big variations.

The sketch is set to start DFS at 14.060 MHz (QRP CW calling frequency) with a Frequency Step of 100Hz. Frequency Steps of 10 Hz, 100 Hz, 1KHz and 10 KHz are provided for covering a single Ham band with a 100 or 350 KHz of bandwidth. The rotary encoder is a plain vanila stock type with a built-in push button for the step change. 

I have built my DFS on a piece of double-sided perforated board 6 x 4 cm, using an Arduino Pro mini operating at 5 vold that I happened to have available. As it does not have a USB port, I load the sketch through the ICSP port. You can use a FTDI USB port, but frankly I would recommend the use of an OEM Arduino Nano that has a built USB port for the not so experienced with Arduino world constructor. Remember there is a plethora of knowledge on how to do things with Arduino on the internet.
