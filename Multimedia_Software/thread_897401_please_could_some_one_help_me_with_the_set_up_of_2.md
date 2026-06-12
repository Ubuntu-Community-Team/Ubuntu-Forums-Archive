---
title: "please could some one help me with the set up of 2 monitors."
date: 2008-08-22
forum: Multimedia Software
---

### Post by JP1990 on 2008-08-22
hi im pritty new to ubuntu and this is my 1st pc with it on i decided i wanted to have a dual monitor set up so i got 2 19" widescreens exactly the same.

my system info is,

Motherboard = Asus P5B-MX (SKT 775)
CPU = Intel Celeron 430
Ram = Kingston DDR2 667Mhz 
Hard Drive = Seagate 320GB Sata
Optical Drive = Asus Sata DVD RW
Graphics Card = Xpertvision 7900Gs 512Mb

right here is the problem, i installed ubuntu and ran all the self checks video cards audio mic ect. told me i had to download this nvidia driver so i did. then i did all the ubuntu updates.
and i couldnt get the second monitor to give a display so i installed Envy and used it to install my nvidia driver then i got a display. but i have 2 19" widescreens with a resolution on 1440x900 but i can only get that resolution on the primary monitor on the secondary monitor i can only get 640x480 resolution.

im a complete noob when it comes to ubuntu and any help would be appreciated so much thank you in advance.

---

### Post by overdrank on 2008-08-22
Moved :)

Hi and welcome, Have you tried using the nvidia-settings to setup your second monitor? Use the alt,F2 keys and enter the command ```
gksu nvidia-settings
``` You may also need to edit your xorg.

---

### Post by Enoex on 2008-08-22
try to enable twinview by opening up the settings like overdrank suggested.  Then make sure your ubuntu screen resolution is set properly (should be the one with the largest width).  
Setting up dual monitors has always been one of the biggest issues I run into when I set up ubuntu for people, so I made a video how-to describing how to do it without editing any system files - people are usually a bit scared to do that, myself included :).  Following the steps I outline has worked for me every time, you can check it out at [Set up Dual Monitors with Ubuntu 8.04]("http://www.youtube.com/watch?v=zFX5UssUgcs")  (sorry for the unnecessary 30 second into, it was originally done as a demo for class).  The full instructions can be found in my [Dual monitors with Ubuntu 8.04]("http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/") post. 
Sorry for the excessively long post, but I hope it helps and good luck!

---

### Post by JP1990 on 2008-08-23
hi thank you for all your support i tried yesterday still with no luck im gonna follow that video exactly and see how it goes i will also re install ubuntu just incase anything wrong.

the only difference i see in my comp and your video are the fact that im using Envy and your using Envy NG. (i dont no if there are any differences.)

---

### Post by JP1990 on 2008-08-23
right i did everything in the video and i get 2 visuals now but it will not allow me to change the resolution from 640x480 on the secondary display.

the primary gets the 1440x900 resolution wich is perfect for what i need but i can not get it on the secondary display, any ideas ?

i have installed envyNG instead of just envy that seemed to run smoother and all the updates for Ubuntu are installed.

i have been told to edit the "xorg.conf" file but im a noob and have no idea on how to do this or actually find it.

thanx for all the help guys.

---

### Post by overdrank on 2008-08-23
> **JP1990 said:**
> right i did everything in the video and i get 2 visuals now but it will not allow me to change the resolution from 640x480 on the secondary display.

the primary gets the 1440x900 resolution wich is perfect for what i need but i can not get it on the secondary display, any ideas ?

i have installed envyNG instead of just envy that seemed to run smoother and all the updates for Ubuntu are installed.

i have been told to edit the "xorg.conf" file but im a noob and have no idea on how to do this or actually find it.

thanx for all the help guys.

Hi and could you post the output of this command ```
cat /etc/X11/xorg.conf
``` and use the code tags on the reply to save space. I have attached a screen shot to show in the reply messeage.

---

### Post by JP1990 on 2008-08-23
hi again when i type in the command (/etc/X11/xorg.conf) i get an error message saying 
"could not open location file:///etc/X11/xorg.conf"

---

### Post by overdrank on 2008-08-23
> **JP1990 said:**
> hi again when i type in the command (/etc/X11/xorg.conf) i get an error message saying 
"could not open location file:///etc/X11/xorg.conf"

Hi and no need to type, you can just copy and paste.The command was ```
cat /etc/X11/xorg.conf
```
And you can copy and pate the output back here. :)

---

### Post by JP1990 on 2008-08-23
i copy the data across but still nothing is there any way of some 1 logging in to the comp (in windows its called remote desktop). to see where i am going wrong ?.

---

### Post by overdrank on 2008-08-23
> **JP1990 said:**
> i copy the data across but still nothing is there any way of some 1 logging in to the comp (in windows its called remote desktop). to see where i am going wrong ?.

Hi and I do not understand what you mean copy the data across. Do you have internet connection with the Ubuntu system?

---

### Post by JP1990 on 2008-08-23
no i don't have the internet on the ubuntu syatem i am wrigting on here from my mac. I put it in word doc then on flash drive then copy and paste in the box where i press ALT + F2 and then the box dissapears and nothing happens.

---

### Post by JP1990 on 2008-08-23
i have now got the ububtu pc connected to internet through a ethernet cable from my router so now i have the internet on both pc's

---

### Post by overdrank on 2008-08-23
> **JP1990 said:**
> no i don't have the internet on the ubuntu syatem i am wrigting on here from my mac. I put it in word doc then on flash drive then copy and paste in the box where i press ALT + F2 and then the box dissapears and nothing happens.

Hi and you need to use that command in the terminal not with the alt, F2 keys. If I am understanding you are saying you enter the command with the alt, F2 keys. It will not work, only in the terminal

---

### Post by JP1990 on 2008-08-23
ok so how do i enter it in the terminal ?

---

### Post by overdrank on 2008-08-23
> **JP1990 said:**
> ok so how do i enter it in the terminal ?

Open the terminal located under applications, accessories, terminal. Then paste the command in the terminal and press the enter key. Then you can highlight the text from the output and paste in the reply message here.

---

### Post by JP1990 on 2008-08-23
right i did what you asked me too and this is what i got,

# xorg.conf (X.Org X Window System server configuration file)
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

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by overdrank on 2008-08-23
Ok when you use the nvidia-settings you are not able to adjust the second monitor settings at all?
How did you install the driver with Envy, did you do the automatic or did you choose which driver to install?
What version of the driver are you using? you can find this in the nvidia settings under X Server information.

---

### Post by JP1990 on 2008-08-23
yes that is because when i click to save the settings it says 
"unable to create new x config backup. file cat /etc/X11/xorg.conf.backup"

---

### Post by JP1990 on 2008-08-23
and i used the automatic version of the envy software

---

### Post by overdrank on 2008-08-23
> **JP1990 said:**
> and i used the automatic version of the envy software

Ok when I had a similar issue I Used Envy and tried a older version of the driver. This is why I edited my last post and asked which driver version you are using  :)

---

### Post by JP1990 on 2008-08-23
ok so would you use version 96.43.05 or 71.86.04 ? 

they are the 2 options i have 

and thanx again for all the help your giving me.

---

### Post by JP1990 on 2008-08-23
i tried all 3 sets of drivers now and still no luck i really dont know what to do next :(

i hope i dont have to go back to windows ^^

---

### Post by overdrank on 2008-08-23
> **JP1990 said:**
> i tried all 3 sets of drivers now and still no luck i really dont know what to do next :(

i hope i dont have to go back to windows ^^

HI and threats to return to windows does not attract much help.:)
I am using the driver 169.12 but there is a newer driver 173.XX that you may want to try. I did have to use the 96.XX driver on my son's system with a nvidia 7300 graphics. So I would say try the newer driver but make sure that you uninstall any nvidia driver before installing the next.

---

### Post by JP1990 on 2008-08-24
it wasnt a threat i am hoping i really want to use linux :) ill try the new driver :)

---

### Post by akudewan on 2008-08-24
> **JP1990 said:**
> yes that is because when i click to save the settings it says 
"unable to create new x config backup. file cat /etc/X11/xorg.conf.backup"

Were you running the program as root ?

gksudo nvidia-settings

---

### Post by JP1990 on 2008-08-25
when i logged in to the nvidia software it asked me for the root password yes.

---

### Post by JP1990 on 2008-08-26
Cheers for the advice, all is now working properly as expected.

Thanks you very much.

---

### Post by plnnightsky on 2008-08-26
> **JP1990 said:**
> Cheers for the advice, all is now working properly as expected.

Thanks you very much.

Would be kind enough to post your xorg.conf.  I have been trying to get mine to work as well without success.

thanks

---

### Post by kcsnare on 2008-08-28
I'm having a problem updating my settings in the nvidia x server program.  When I hit save, it gives the following error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

What am I doing wrong?

---

### Post by kcsnare on 2008-08-29
Ok, nvm.  Just had to type gksudo to get into root mode instead of starting it through the (forgive the phrase) "start menu"

---

