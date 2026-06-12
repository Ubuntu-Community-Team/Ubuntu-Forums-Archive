---
title: "800x600 cannot be the maximum resolution!"
date: 2008-07-07
forum: Multimedia Software
---

### Post by csavio on 2008-07-07
[FONT="Arial"]Hi.  I just installed Ubuntu 8.04 on a new machine.  However, I am having trouble with the video display.  The maximum resolution that it is letting me display is 800x600 with a refresh rate of 85 Hz.  I have a VT8375 [ProSavage8 KM266/KL266] that is onboard. 

Another message board suggested I try "sudo dpkg-reconfigure -phigh xserver-xorg" which I did and it didn't solve the problem.  

Last, I did a "sudo lspci -v" and I get the following information:
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266] (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7389
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
	Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at e0080000 [disabled] [size=64K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [80] AGP version 2.0

How can I change the resolution? Thanks for your help.
 [/FONT]

---

### Post by xc3RnbFO8P on 2008-07-07
Have you tried to change your screen to **generic**
in screen and graphics?

---

### Post by csavio on 2008-07-07
[FONT="Arial"]I can't find "screen and graphics".  Where is that?  If it's in "system" --> "preferences" --> "screen resolution", it won't let me change the monitor nor drivers.[/FONT]

---

### Post by xc3RnbFO8P on 2008-07-07
It is in "system" --> "preferences" --> main menu> other, check screen and graphics

---

### Post by csavio on 2008-07-07
[FONT="Arial"]It won't let me change the settings.  It keeps defaulting and to "Plug and Play 800 x 600" :(  I tried several monitors and my widescreen TV. It stays on 800 x 600 and I think the problem lies within the driver, not the display.[/FONT]

---

### Post by xc3RnbFO8P on 2008-07-07
I found this:
> The i810 driver does not go over 1024x768. I assume you have the video integrated on your MB. Please post the chipset that is used on your motherboard and the make of model of your monitor.

There is a tool called 915resolution that might help for certain Intel chipsets; you can find info here. Not 100% sure but I think it's in the Ubuntu repositories (you might have to enable universe or multiverse in synaptic).

> 
thanks for the reply
but i found the solution
i ran a command "sudo dpkg-reconfigure -phigh xserver-xorg"

By selecting i810 from the list, then checking all the checkbox from minimum resolution to 1280x1024, and then restarting the computer gave me the max. resolution i wanted.

Thanks again
varun
[http://www.linuxquestions.org/questions/linux-software-2/low-screen-resolution-ubuntu-feisty-557453/page2.html]("http://www.linuxquestions.org/questions/linux-software-2/low-screen-resolution-ubuntu-feisty-557453/page2.html")

---

### Post by csavio on 2008-07-07
[FONT="Arial"]Thanks for your help but it's still not working. When I tried what you suggested, I get the following message:
[FONT="Courier New"]
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080707185709
[/FONT]
However, I never touched that xorg.conf file.  When I open the file, I get the following:
[FONT="Courier New"]
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
[/FONT]
[/FONT]

---

### Post by wolfen69 on 2008-07-07
try:
```
gksu displayconfig-gtk
```

---

### Post by 16777216 on 2008-07-07
Post the contents of **/etc/X11/xorg.conf **and the manufacturer and model of the monitor you are using.
I will try and make you a xorg.conf that you can use or work with to get the results you want.

---

### Post by csavio on 2008-07-07
[FONT="Arial"]Hi everyone and thanks so much for your help. I got it to work now by some miracle.  Thanks again :)[/FONT]

---

### Post by xc3RnbFO8P on 2008-07-07
It would be great help to others if you knew what solved it :)

---

### Post by MaxSommerfeld on 2008-07-08
Hi! 

It was not a miracle that solved your problem, but the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
which you executed. The output you received didn't indicate the command didn't work correctly. It just said that your previous xorg.conf file has been backed up.
Please note that this probably affected other parts of your configuration such as keyboard settings or the usage of restricted video drivers. Maybe you should check that.

---

### Post by ramakrishna2205 on 2008-07-26
> **16777216 said:**
> Post the contents of **/etc/X11/xorg.conf **and the manufacturer and model of the monitor you are using.
I will try and make you a xorg.conf that you can use or work with to get the results you want.hi, i too am a new user to ubuntu hardy heron, i have exactly the same problem. "gksu displayconfig-gtk" is the only command that works. the contents of my xorg.conf file is exactly the same as in the post above. i use an "LG L194WS" lcd monitor. every time i try to test, i get a gray screen. getiing a bit frustrated. any help would be really appreciated sir. with thanks

---

### Post by 16777216 on 2008-07-26
What is your graphics card?

---

### Post by oobsniper2000 on 2008-07-26
> **16777216 said:**
> Post the contents of **/etc/X11/xorg.conf **and the manufacturer and model of the monitor you are using.
I will try and make you a xorg.conf that you can use or work with to get the results you want.

I have the same issue.  I'm using a Hyundai X93WD monitor with nVidia integrated GeForce 7150 (I have another thread on driver installation problems) and here's my xorg.conf

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by ramakrishna2205 on 2008-07-27
if you had gone through the post above, then u too were facing the same problem i am.
i use, amd athlon 3200+ processor, nvidia chipset 6100 and LG l194ws monitor.
Are u facing, lack of resolution options. there is a simple way to overcome this without going into the command line and editing the Xorg.conf file.

Use "envy", program and choose manual install

then donot select the latest driver from the repository, but instead use the one lower i.e 96.43.05 driver from the repository

mine just started working

100%, i got all the resolutions till 1400x900

:guitar:

of u select the latest driver, the monitor just blanks out, because of the sync rates not confirming

all the best

---

### Post by ramakrishna2205 on 2008-07-27
> **16777216 said:**
> What is your graphics card?

thanks man, i use a nvidia 6100 card.

i solved the problem, by using the program called ENVY and installing a older version of the driver required for my card from the repository, the 96.43.05 version and walah! all the resolutions are displayed.
thanks again
u guys are wonderful

---

### Post by 16777216 on 2008-07-27
Sorry I couldn't get back to anybody on this I had a lot of stuff pile up on me all of a sudden. ( and still do )
But, I am glad that you got it fixed.

---

