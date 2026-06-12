---
title: "Humax 9300t software update with linux"
date: 2011-03-02
forum: Multimedia Software
---

### Post by jon890 on 2011-03-02
Using wine you can update a Humax PVR using your linux PC.
Go to [www.humaxdigital.com](www.humaxdigital.com)
Select site for your country.
 Select Support -> Download Centre -> select your model 9300T.
 Download 2 files, Software Download 9300T_apps_1.00.23.hdf or latest file.
First:
    * Check your system ID before you select a new software.
      
 Click on Download instruction and download WDN40AK%2b.zip
 Unzip WDN40AK%2b.zip
 Enter WDN40AK+ directory make SETUP.EXE executable and execute.

 Download 9300t_apps_1.00.23.hdf file and copy to:
  /home/user/.wine/drive_c/users/Public/Start Menu/Programs/WDN40AK+

Before starting the procedure POWER OFF your Humax 9300T using the rear ON/OFF switch or disconnecting from the mains.
NB To download software via a PC you do not need to have your product connected to a TV or the aerial. You will only need a power connection.

Connect a RS-232c (Crossover, not straight wired) Null Modem/Serial cable (9 Pin Female to 9 Pin Female) between the COM port of your PC and the RS-232 connection on your receiver. 

Enter /home/user/.wine/drive_c/users/Public/Start Menu/Programs/WDN40AK+ directory and make WDN4OAK.lnk file executable, execute with wine.

The Windows WDN40AK popup opens and shows COM1 but linux will be /dev/ttys0, keep baudrates to 115200bps. 
 Click on yellow folder in WDN popup and browse to and load 9300T_apps file.
Click on Download on Windows popup.
When the message (PC to STB popup) appears on your PC, POWER ON the Humax from the rear ON/OFF switch or from the mains.
The download process will now start and you will see the progress bar on the PC to STB window.
ON the receiver you will see D00, D10, D20, etc; when programming the software the display will change to P10, P20, P30 
Please do not switch off the receiver until you see END on the front display. Your receiver is now upgraded. 
Now power off from the rear, reconnect to your TV and aerial (if applicable) and power on the PVR.

The Humax website is confusing with the 9300T download instructions, but the above is from 9200 model which is clearer. The humax will not upgrade from standby it must be powered on precisely as above.

---

### Post by kestonman on 2011-09-06
[SIZE=2][FONT=Arial]I had a lot of problems in trying to use the Humax updating software with a Prolific PL-2303 USB to RS232 converter.  All  the recommended programs failed to set the serial port successfully although the converter was recognised by Ubuntu and would operate correctly with other serial port programs.

After trawling the net for a solution I stumbled across **Flash9200 **[/FONT][FONT=Arial]a software upgrade tool for the Humax 9200, 9150 and 9300 available from [http://www.tynecomp.co.uk/flash9200.html](http://www.tynecomp.co.uk/flash9200.html) which operates without a problem using Wine. Other Humax users should give this a try. :)
[/FONT][/SIZE]

---

