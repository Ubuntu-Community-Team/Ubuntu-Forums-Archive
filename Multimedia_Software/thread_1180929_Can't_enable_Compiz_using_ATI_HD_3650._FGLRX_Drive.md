---
title: "Can't enable Compiz using ATI HD 3650. FGLRX Driver Issue!!"
date: 2009-06-07
forum: Multimedia Software
---

### Post by scrypt on 2009-06-07
Hi All...

I am having a reacuring  issue with my ATI HD 3650 Graphics card.

It seems to work fine for a few days. I can run Compiz and AWN and other graphically intensive programs etc.

But after a while. For some  unknown reason I get this Error message when I Boot Up:-

Warning: Screen isn't composited. Please run Compiz (-Fuzion or another Composited Manager.

I then got to System-Administration-Hardware Driver. To make sure the correct proprietary ATI/AMD FGLRX Graphics Driver is installed.

But it says A different version of this Driver is in use!!

I am unsure how to fix this issue.

Can anybody shed some light on this and help me to rectify my issue??

Cheers in advance

---

### Post by scrypt on 2009-06-07
Here is the bottom part of 'sgedit /etc/X11/xorg.conf'

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection

---

### Post by scrypt on 2009-06-07
I have also looked in Synaptics package manager at anything to do with ATI and FGLRX

And I noticed this problem:-

The following packages have unmet dependencies.
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.28-13-generic but it is not installable
E: Broken packages

Am I right in thinking this could have someting to do with why I cannot correctly compozit my screen??

---

### Post by harak on 2009-06-08
You could have compiled/installed the driver from ati's website. So try uninstalling it. If I remember there must be an uninstaller somewhere in the /usr/libs/. I have a hd 3200. so I could be wrong. I don't think the restricted module stuff has anything to do with it. I have the same error, even after a clean install of jaunty. and compiz works fine for me.

---

### Post by zika on 2009-06-08
> **harak said:**
> You could have compiled/installed the driver from ati's website. So try uninstalling it. If I remember there must be an uninstaller somewhere in the /usr/libs/. I have a hd 3200. so I could be wrong. I don't think the restricted module stuff has anything to do with it. I have the same error, even after a clean install of jaunty. and compiz works fine for me.
/etc/ati ...

---

### Post by scrypt on 2009-06-18
Hi All.  Thanks for the replies.

I actually re-instaled Ubuntu because I could not fix this issue..

Then low and behold I am having the exact same problem right now on my newly instaled ubuntu 9.04 system...

Every thing was running sweetly up until I clicked an acctdentaly wrong button in appearance-visual effects. and now I can't seem to fix it!!

I caused it by clicking the the button in System-preferences-appearance and then clicking the extra button/option in visual effects.

Now when I restart Ubuntu I am greeted with a message that states:-

Warning. screen in not compozited, please run compiz (-Fuzion or similar compozited application).

I can get compiz running if I run compiz in the terminal.

I just can't get compiz to automatically start when I boot-up 

Has any one had experience with fixing this? Or can any body otherwise help me to fix this??

How can I get compiz to auto start at Boot-up??

---

### Post by markbuntu on 2009-06-18
In the ServerLayout section of xorg.conf try adding this line

Option  "AIGLX" "on"

And in the section

"Extensions"

Option  "Composite" "Enable"

I don't know what driver you are using so this may or may not work but you can try it.

---

### Post by scrypt on 2009-06-18
Hi markbuntu

I added compiz into system-Preferences-Startup applications.

and this start my screen as compozited a bootup, But I now get tis message:

There is already another notification area running on this screen!

can you shed any light on this??

---

### Post by scrypt on 2009-06-18
I am still having some strange issues regarding my screen being compozited.

Every so often Compiz will just cease. and I have to write 'compiz' in the terminal to start it again.

Can anyone try to help me with this, because it seems to be an on going problem I am having.

I also get this error message flash up quickly each time I shut dowm:-

'Warning: Screen isn't composited. Please run Compiz (-Fuzion or another Composited Manager.'

I am not sure what else I can add to this post to try and give a bit more detail to my problem.
So if anybody replies can you tell me what I should add to help you help me fix my issue

cheers

---

### Post by scrypt on 2009-10-17
I am still having trouble with this isue.

when i start ubuntu.

I get this ERROR mesage :

mark@tiple2009-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


I cannot Activate and install my ATI/AMD Propriety FGLRX Graphics Driver. from System-Asdministrator-Hardware Drivers.
It looks as thogh it installs by showing a bar loading but nothing happens.

Also I have NO Mousepad Movement on my Dell Studio 1737 (I have to use A USB Mouse).

Im still new to Ubuntu's workings.
But Im not sure if my xorg.conf file might be in A mess.

Can somebody please help me rectify this.

Cheers

Scrypt.

---

