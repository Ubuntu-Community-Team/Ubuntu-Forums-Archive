---
title: "[AU] Bigpond 7.2 MF636 Mobile Broadband :: HowTo"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by w0lv3n on 2009-04-17
[I]Not sure if this should be in another area if there is a dedicated 'articles' board.

Writing this after pissfarting around trying to get my own mobile broadband to work.[/I]

This is a quick and simple 'How-To' for using a **Bigpond MF636 Mobile Broadband Card** with **Ubuntu 8.10 Intrepid Ibex**

**[SIZE="4"]Step 1[/SIZE]**
*We need to disable the autorun feature of the USB Modem. Basically it has three functions: Modem, Mini-SD Reader and Mountable ISO. When you plug it into Linux, the ISO is the only thing it sees. This is a problem because we dont want the ISO we want the Modem.*

**Load** up Windows - If you havent already installed your mobile card, then do so.
**Run** "Bigpond Wireless Broadband 2.0" - This is the mobile connection manager.
**Connect** to the internet.

[IMG]http://i6.photobucket.com/albums/y249/w0lv3n/MF636_Main.jpg[/IMG]

*At this point, you are connected to the internet, the modem is working. Now we need to send a command to the modem in order to disable the ISO function*

**Shift+Click** 'Options' - This will load a slightly extended version of the normal options window.
**Click** the 'Diagnosis' tab.

[IMG]http://i6.photobucket.com/albums/y249/w0lv3n/MF636_Options.jpg[/IMG]

**Click** 'Modem Terminal' - This will open a direct terminal to the modem. Usually to do this you must have Hyperterminal or something similar - which is not standard in Vista.
**Type** 'AT' press 'Send' - This should return 'OK'
**Type** 'AT+ZCDRUN=8' press send - This should return a message saying whether it failed or succeeded.

[IMG]http://i6.photobucket.com/albums/y249/w0lv3n/MF636_Terminal.jpg[/IMG]

*You can now disconnect, quit the manager , unplug the modem and load Ubuntu*

**[SIZE="4"]Step 2[/SIZE]**
*Now that you have loaded Ubuntu, plug in the usb.*

**Open** terminal.
**Enter** the command 'lsusb'.

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 19d2:0031  
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
[I]Something similar to this should result. The important part here is the 'ID 19d2:0031' . If this isnt in your results, but 'ID 19d2:2000' is, then we havent disabled the ISO so try step one again.

Now that we have the correct function being recognised, we need to tell Linux what it is.[/I]

**Enter** the following code into terminal:
[INDENT]```
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x19d2 product=0x0031
```[/INDENT]
*This has told Linux that the device at ID 19d2:0031 is a USBserial device (I think! =P)*

**Unplug** the modem.
**Enter** the following into terminal:
[INDENT]```
sudo /etc/init.d/hal restart
```[/INDENT]
*This should restart the hardware detection. Hopefully after this point, Network Manager will notice the device and prompt for a new connection.*

**[SIZE="4"]Step 3[/SIZE]**
*Now that we have the device recognised, we need to setup the connection. Provided Network Manager plays nice, this is very easy*

**Click** the 'Mobile Broadband' tab.
**Click** 'Add'
**Select** 'Telstra' - Accept the settings.
**Click** 'Edit'
**Enter** your username and password
**Change** the APN to 'telstra.bigpond.
**Accept** the settings

*Now that the connection is set up, attempt to connect to the internet. Hopefully you should now have internet access! All thats left to do now is make the modem recognition automatic*

**[SIZE="4"]Step 4[/SIZE]**
*By editing a few lines, we will enable the device automatically upon startup.*

**Open** terminal.
**Enter** the following code:
[INDENT]```
sudo gedit /etc/init.d/rc.local
```[/INDENT]
**Add** the following lines to the bottom of the file:
[INDENT]```
modprobe -r usbserial
modprobe usbserial vendor=0x19d2 product=0x0031
```[/INDENT]

*Restart Linux and you should be able to connect straight after plugging in the USB*
 - - - - - - - - - - 

I think thats about it. Im in vista atm and had to use other links and what not to remember it all. Will edit this later with any changes.

**Please** post any issues, feedback or variations. I dont know if the terminal is available in other versions of the connection manager software or for different model ZTE MF6xx modems.

**Hope this helps people!**

[I]Original posts and information:
[http://ubuntuforums.org/showthread.php?t=1005910](http://ubuntuforums.org/showthread.php?t=1005910)[/I]

---

### Post by ghostio on 2009-04-18
> **w0lv3n said:**
> 

**[SIZE="4"]Step 1[/SIZE]**
*We need to disable the autorun feature of the USB Modem. Basically it has three functions: Modem, Mini-SD Reader and Mountable ISO. When you plug it into Linux, the ISO is the only thing it sees. This is a problem because we dont want the ISO we want the Modem.*



I was able to do the step 1 in Linux. I'm using Fedora Core 9, but I guess it's the same with Ubuntu.

First you need to install usb_modeswitch application.

Then...
1. Plug in the modem and run:
```

modprobe usbserial
usb_modeswitch --DefaultVendor 0x19d2 --DefaultProduct 0x2000 --MessageEndpoint 0x01 --MessageContent 55534243123456782000000080000c85010101180101010101000000000000

```
I got this from here: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg636352.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg636352.html)

After that you should have /dev/ttyUSB[0,1,2] visible. 

2. Open some terminal application (e.g. minicom, kermit. I used gtkterm) and use it to connect to /dev/ttyUSB2

3. Type in: 
```
AT
AT+ZCDRUN=8
```

Unplug the modem and plug it in again. Now the ISO feature should be disabled and the modem should get detected by NetworkManager.

Note: When you use usb_modeswitch app, NetworkManager probably detects the modem. And at least with my kernel I got an Kernel OOPS when I switched the usb mode.

---

### Post by w0lv3n on 2009-04-18
I did try this program but it didnt work for me. The instructions you have posted are slightly different to the ones I found though, so hopefully yours is a clear winner! 

Thanks for the input, hopefully it will make this how-to better and easier to find.

---

### Post by techno-dug on 2009-04-21
Hi, I'm trying to install on an Eee PC. I think the OS is based on Xandros. I'm having no success.

I'm now trying to get it working first of all in Mint. I follow all the instructions you have provided here, but Mint's network manager does not find the modem.

Any assistance would be much appreciated!

---

### Post by reddingo90 on 2009-08-25
Thanks [w0lv3n]("http://ubuntuforums.org/member.php?u=805795"), Finally got ubuntu 9.04 and my MF636BP USB stick to connect to the internet(Yeeee ha) following your instructions. Only hiccup was that usbserial was not recognized, but as I was doing lsusb it connected and to make sure all was ok I have rebooted several times and have been automatically connected. Thanks again. Adrian Oh! I live in Qld now but used to live in Wakiki for awhile.

---

### Post by icodemonkey on 2009-09-22
Thanks [w0lv3n]("http://ubuntuforums.org/member.php?u=805795") for the how to but after my system recognises the modem it tells me the connection has been closed. then when i re-insert the modem it asks for a password even though i have entered that in the network manager.
im using 8.10 but i just cant get the thing to make a connection

---

