---
title: "Blank White Screen After Installing Newest ATI Drivers."
date: 2009-01-05
forum: Multimedia Software
---

### Post by slicemaster on 2009-01-05
Well, I am relatively new to this whole Linux thing although I have been running Ubuntu on several of my computers for about six months. Anyway, I recently decided to try to install the most recent AIT drivers on my laptop (v. 8.12) running Ubuntu 8.04 LTS 32-bit (Fully Patched and Up to Date) because the preparatory drivers that Ubuntu has in their repositories are old and are not equipped with the catalyst control panel. Anyways, I downloaded the most recent driver installer from AMD's website and tried to install them but now after I try to login all I get is a white screen with my mouse curser (I can move the curser but nothing else show up). So basically I am wondering what I am doing wrong for the system to perform this way. Here are the step I followed to install the drivers.

1st - Downloaded the most recent drivers from AMD's website and saved it to my desktop.

The file name is: ati-driver-installer-8-12-x86.x86_64.run

2nd - after the file download completed I made sure that the file was executable (using the right-click properties trick)

3rd - next I opened up a terminal window as directed in the installation directions and installed the necessary packages for the drivers to operate correctly (as found in the Ubuntu documentation) and executed this command to install the packages.

Command was: sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot

4th - after the packages were installed I then proceeded change my working directory in the terminal window to "Desktop" which is where I saved the install file.

Command was: cd Desktop

5th - next I executed this command to start the install process as directed in AMD's documentation.

Command was: sudo ./ati-driver-installer-8-12-x86.x86_64.run

6th - A graphic installer then opened up and I followed the installation directions -> I chose to use the automatic method and proceeded through the installer until it was complete.

7th - I rebooted the system as per the instructions in the AMD documentation.

8th - the system rebooted and the log-in screen came up. after which I logged into my regular account, I received the "Ubuntu jingle" sound and then the screen went white with the mouse curser in the middle of the screen, and then nothing (I can move the mouse around but that is it).

9th - I broke out of the gui environment by using the keyboard shortcut Ctrl+Alt+F1 and proceeded to relog-in using the terminal prompts after which I ran the command given to me at the end of the driver installer that said if I experienced any issue I should run this command.

The command was: sudo aticonfig --initial -f

10th - the command did its thing and I rebooted the box. However still no GUI, just the white screen with the curser after log-in

!!!PLEASE HELP!!!

Thanks,
Slice

---

### Post by ptike007 on 2009-01-23
I have the same white screen problem after installing catalyst 8.12 for ubuntu 8.04.

Does anybody know a fix?

---

### Post by markbuntu on 2009-01-23
When you get to the login screen try changing the session to gnome safe mode. See if that works. If it does, look in the Xorg.0.log file for any error messages.

What ati card are you using?

---

### Post by bigbird on 2009-01-26
I went from a Nvidia on-board system to a ATI Sapphire 3850 running on 8.04 system.
My hats off to Ubuntu saw the the change unloaded the N-Driver and loaded the ATI basic driver in restricted driver but then was locked at 600x400.
After searching forums I saw a number of posts similar to mine.
I tried the sudo dpkg --reconfigure -xserver thing,
The system rebooted and the log-in screen came up looking like the correct resoloution. after which I logged into my regular account, I received the "Ubuntu jingle" sound and then the screen went white with the mouse cursor in the middle of the screen, and then nothing (I can move the mouse around but that is it).

Sorry I am too new to the command line usage and little knowledge of what I am doing to fix this myself, Please help me.
Thank you in advance, best regards Chauvin.

---

### Post by konradpiskorz on 2009-01-26
Hey,

I have the exact same problem running an ati radeon x1400 on my laptop.  While not a solution per se, I found that out of the four kernel versions installed on my laptop only 2.6.24-21-generic installed by ubuntu works.  The newer kernels do not!

It could just be the the newer generic kernels arent compiled with the options you need.  Try loading the other kernels on boot through grub and see if it works.  I haven't had any issues downgrading kernels, although again... not a fix.

---

### Post by perixx on 2009-02-02
Allright, I had the same problem (Xubuntu x64 Hardy) - here's my solution:
(hopefully also applies to Gutsy and Intrepid)

This is done by building release specific packages and installing some missing dependencies. 



**Preparing the installation:**


1) download the latest 9/1 drivers from Ati (of course :)) into e.g ~/ati
2) open a terminal and type ```
sudo -i
```(will save us writing it often)

3) change the download folder, we'll create our deb's here: 'cd ~/ati
4) uninstall old Ati drivers: via Synaptic, Envy or the command 
```
sh /usr/share/ati/fglrx-uninstall.sh
```, depending on how you installed the old ones

5) *** a probably very important step *** 
open the Synaptic package manager, do a 'search' for **libxv-dev** and **libxvmc-dev** and install them, or try ```
apt-get install XYPACKAGE
``` in the terminal

6) to make sure all kernel modules are unloaded, we do```
reboot now
```

7) repeat steps 2) and 3)
8] X now running with 'vesa' driver, I prefer to shut down the X-server: 
```
/etc/X11/init.d/gdm stop
```Note: you can switch between a virtual termninal and the graphical X server with CTRL+ALT+1 / CTRL+ALT+7

9) let's make a backup of the current 'xorg.conf', if things get nasty: ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak_old
```

10) [b]now the main part[b], we build the release-specific package:
```
sh ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/hardy
```Note: replace 'hardy' with the appropriate string for your release; run the installer with '--listpkg' to find out which one you need

11) we now have our deb's created in our folder and install this order: ```
gdebi fglrx-kernel-source_8.573-0ubuntu1_amd64.deb
gdebi fglrx-modaliases_8.573-0ubuntu1_amd64.deb
gdebi xorg-driver-fglrx_8.573-0ubuntu1_amd64.deb
gdebi libamdxvba1_8.573-0ubuntu1_amd64.deb
gdebi fglrx-amdcccle_8.573-0ubuntu1_amd64.deb
gdebi xorg-driver-fglrx-dev_8.573-0ubuntu1_amd64.deb
```
- Ignore a message about 'Unfortunately an unsupported dependency' 
- If asked to install the **dkms** package, make it so.
- Other combinations may work, but this one did for me.

12) we make sure that the 'fglrx' driver is used:
```
nano /etc/X11/xorg.conf
``` > look for the following section and replace 'vesa' with 'fglrx': 
```
Section "Device"
	Identifier	"Configured Video "
	Driver		"fglrx"
EndSection
```Now exit with CTRL+X and acknowledge to save the file (Y+Enter)

13) lastly, let's restart into accellerated eye-candy (hopefully):
```
/etc/init.d/gdm restart
```

Good luck!


perixx

---

### Post by ice031 on 2009-02-05
PROBLEM SOLVED:

Hi, first of all I would like to say that I have successfully installed the ATI driver version 8.12 on Ubuntu 8.10.

There is a very good installation guide from wiki ~ just click on the link below:
> [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

The installation should work fine with ati drivers 9.1, but you should note that ubuntu 8.10 comes installed with [COLOR="Purple"]libstdc++.so.6 [/COLOR]instead of [COLOR="purple"]libstdc++.so.5[/COLOR](the wiki guide says to install libstdc++5.) Don't worry you can have both of them installed at the same time.

I haven't veried which version yet...waiting for a reply from ATI regarding this matter.

---

### Post by ice031 on 2009-02-05
Confirmed.
I couldn't wait to hear back from ATI, so I checked myself and version 9.1 still depends on libstdc5 (libstdc++.so.5)

cheers~ :)

---

### Post by ice031 on 2009-02-05
Officially Solved:
So to relieve everyone of their worries, I've installed Ubuntu 8.10 on another machine with the same specs with the new drivers (version 9.1)
using the Installation Guide provided by cchtml.com on their wiki page:
Link Below:

> [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

I followed the directions down to the bone, and everything installed perfectly. 
(Note: I didn't force the ati driver to adopt changes made to xorg.conf...
as mentioned in the wiki guide)

So give it a try, and if you have issues, just send me a message. 

Cheers~ :)

---

