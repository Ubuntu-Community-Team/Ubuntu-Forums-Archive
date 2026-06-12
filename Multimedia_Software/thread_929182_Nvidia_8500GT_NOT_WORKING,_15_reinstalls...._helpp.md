---
title: "Nvidia 8500GT NOT WORKING, 15 reinstalls.... helppp"
date: 2008-09-24
forum: Multimedia Software
---

### Post by Knuxyl on 2008-09-24
Ok, I have installed Ubuntu 8.04 15 TIMES trying to get this to work with enhanced visual effects and games run better but it's not working. I have tried EVERYTHING, I have followed so many guides on the internet..... none have got me anywhere. I have tried the envy, glx, glx-new, and the drivers from the nvidia website and tried manually on everything and automatically with everything but EVERYTIME I either get A : blank screen after ubuntu logo loading screen or B : low graphics mode. Right now I'm in 800x600 screen resolution, low graphics mode, reinstalling envyng with oldest nvidia driver that was available, 71.86.04. I've already tried 173.14.14 and 96.43.05 which are the other two available. I used to think that it was because the refresh rate was defaulting too high which I'm starting to think itsn't the problem anymore, but IF it is I need a way to make my refresh rate at 60hz, anything above will cause a blank screen. My xorg.conf file is just defaulted right now after using the recovery console on startup so no point in posting it. Before I started trying envy, I remember shutting down gdm and installing the nvidia driver from the website and it saying the kernel version and driver version were different? the kernel was lower then the driver. I have uninstalled and installed these nvidia drivers sooooo $#&!)()(*$% many times..... Here are my specs
Ubuntu 8.04 x86 32-bit
Nvidia Geforce 8500GT 512mb
AMD something.... **** i forgot, its dual core +6000 3.0ghz :p
installed on hd1,0
2gb ram
im so frustrated, vista is acting like a have a @$%!&^ virus, my x64 vista is trippin out for some reason, and ubuntu is giving me this ****, this is making me want to just stay on my smart phone, which i would if opera would get off there *** and release uiq 3 9.5...... anywaysssssssssssss someone PLZ help me im going nutss. thank you very much :)

---

### Post by realzippy on 2008-09-25
O.K.
First:
delete your xorg.conf because it is messed up by typing in terminal:

 sudo rm /etc/X11/xorg.conf

Download the NVIDIA-Linux-x86-173.14.12-pkg1.run from the nvidia website
to the Desktop.
Reboot,do not log in,choose a terminal by ALT+F3,log in there.go to the Desktop:

 cd Desktop

then:

 sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

all answered during installation with "yes"

 sudo reboot

that should work.

---

### Post by Knuxyl on 2008-09-25
didnt work
started ubuntu, got to log on screen ALT+F3 didnt work but CTRL+ALT+F3 did, logged in, had to do sudo invoke-rc.d gdm stop to stop the xserver cuz nvidia said i had to, redid the nvidia installer, it said i had to compile its own kernel or w/e cuz one wasnt available so i clicked ok, yes to reconfigure xorg.conf and restarted and got a blank screen, idk if its hanging or no screen because my speakers are on my monitor so when my monitors off the speakers dont work so i dont hear the ubuntu sounds. is there some other way to get this to work? maybe the nvidia thing isnt recognizing my cards ID, i have PNY card which ive never even heard of :p is there a way i can view its device and vendor id and put that in the driver somehow? this is really annoying the piss out of me. this same crap happened with fedora a long time ago. thank you very much for your reply :):)

---

### Post by jerome1232 on 2008-09-25
I think you might want to try manually editing xorg.conf after installing the driver.

Can you get to a tty by hitting ctrl+alt+F1 (you can use any F key up to F6 to get a console)

If so you can edit your xorg.conf like this
```
sudo nano /etc/X11/xorg.conf
```

Unfortunately I'm not familiar with the syntax you need to use to configure things in there so I can't help you with that, google may help you with finding out how to write up a xorg.conf. Backup the original so you can always revert to it.

---

### Post by Knuxyl on 2008-09-25
yeah i can get to manually configure the xorg.conf file but i have NO idea what to change on it. im so tired of looking if someone knows that would be greatly appreciated. all i know is when i put Driver "nvidia" thats what causes the blank screen. i know theres got to be someone else having this problem, so plz help us :p

---

### Post by norwoods on 2008-09-25
please run the following commands in a terminal and post the result.
you will need to enter the root password after the 'sudo insmod --versionsize --version' command

cat /proc/version
Xorg -version
sudo insmod --version
size --version
make --version
gcc --version
ls /lib/libc.so.*
uname -r
ls /usr/src |grep `uname -r`

[http://www.nvnews.net/vbulletin/showthread.php?t=119682](http://www.nvnews.net/vbulletin/showthread.php?t=119682) has links to the latest driver and README:

[ftp://download.nvidia.com/XFree86/Linux-x86/177.76/NVIDIA-Linux-x86-177.76-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/177.76/NVIDIA-Linux-x86-177.76-pkg1.run)

[ftp://download.nvidia.com/XFree86/Linux-x86/177.76/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.76/README/index.html)

download driver 177.76 and put it on your Desktop.
download README if you want to but a condensed version follows:
rename the driver file to something shorter so you will not have to type as much, like: NVIDIA177.76.run
get a console with ctl-alt-F1
login
change directory with cd to your Desktop
stop the X server by running sudo /etc/init.d/gdm stop
install the driver by running sudo sh NVIDIA177.76.run
answer the questions; when it asks, let it run nvidia-xconfig
reboot by running sudo shutdown -r now

if you have 2 monitors with DVI, try booting with only one connected.

---

### Post by Knuxyl on 2008-09-25
```
cat /proc/version


Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008


```

```
Xorg -version


This is a pre-release version of the X server from The X.Org Foundation.

It is not supported in any way.

Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.

Select the "xorg" product for bugs you find in this release.

Before reporting bugs in pre-release versions please check the

latest version in the X.Org Foundation git repository.

See http://wiki.x.org/wiki/GitPage for git access instructions.



X.Org X Server 1.4.0.90

Release Date: 5 September 2007

X Protocol Version 11, Revision 0

Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)

Current Operating System: Linux JD-Desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686

Build Date: 13 June 2008  01:08:21AM

 

	Before reporting problems, check http://wiki.x.org

	to make sure that you have the latest version.

Module Loader present


```


```
sudo insmod --version


module-init-tools version 3.3-pre11

```

```
size --version


GNU size (GNU Binutils for Ubuntu) 2.18.0.20080103

Copyright 2007 Free Software Foundation, Inc.

This program is free software; you may redistribute it under the terms of

the GNU General Public License version 3 or (at your option) any later version.

This program has absolutely no warranty.


```


```
make --version


GNU Make 3.81

Copyright (C) 2006  Free Software Foundation, Inc.

This is free software; see the source for copying conditions.

There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A

PARTICULAR PURPOSE.



This program built for i486-pc-linux-gnu


```

```
gcc --version


gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Copyright (C) 2007 Free Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is NO

warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


```

```
ls /lib/libc.so.*


/lib/libc.so.6

```

```
uname -r


2.6.24-19-generic


```


```
ls /usr/src |grep `uname -r`


linux-headers-2.6.24-19-generic


```


wanted to get those out of the way. im going to try that new nvidia driver. ill post back the results.

---

### Post by Knuxyl on 2008-09-25
same thing, blank screen. did exactly what you said. i went ahead and copied the xorg.conf file to my desktop in shell and reconfigured xserver so here is the contents of the xorg file

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Thu Sep 18 17:19:17 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


edit : oh btw my screen max is 1280x1024x60hz, 60hz on all resolutions, have old crt monitor

---

### Post by norwoods on 2008-09-25
your xorg.conf is the same as mine.  i have a 9600gt so maybe something is wrong with 8500gt support.  good luck.

---

### Post by Therion on 2008-09-25
At this point, with you having done as much as you have, it might be best to start with a fresh install and simply let the Restricted Driver Manager install the nVidia driver.  Easy peasy and it, meaning the Restricted Driver, runs all the Compiz effects just fine.  I've been using it since Hardy came out.

I'd suggest doing a reinstall and doing ALL the updates and such BEFORE allowing the Restricted Driver Manager to install your video driver.

---

### Post by Knuxyl on 2008-09-25
done that
have installed ubuntu 15 times, about 7 of those started off by updating, restarting, enabling restricted driver, restarting, blank screen....

---

### Post by infoseeker on 2008-09-28
I have the same problem.  I have a 9600GT and I cannot get the Nvidia driver to operate/configure correctly.  All I get is a screen setup of 800x600 (with the error messages).  I then have to delete the xorg.conf file and reboot back to the default driver, with its out-of-focus fonts (ant-aliasing probably causing this)

Latest driver I downloaded was 173.14.12.....no luck!

I have a 1280x1024x60 LCD display.

This is really bugging me ;)

I recently dumped my 8600GT (which worked flawlessly) as the cooling fan failed and replaced it with the 9600GT, thinking it might be directly compatible.  I had the option to use the restricted driver under 'System/Administration/Hardware Drivers' with the 8600GT but I do not get anything listed there now, so I attempted the 173.14.12 driver directly from Nvidia.

Tried reading here too:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Driver:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

EDIT: I see there are plenty threads regarding problems with the 9600GT...so it seems there is no cure ;)

---

### Post by Knuxyl on 2008-09-30
*bumpppp*

still not working...... i would love to switch to linux from windows but so far linux has disappointed me greatly, especially ubuntu.... i know the coders are workin hard on it but before adding all these addon freeware programs and getting all that to work maybe they should work on the compatability with hardware??? just a thought....

btw my amd dual core processor seems to not work with the cpu monitor, i remember an error, so theres another ubuntu hardware problem.

---

### Post by Knuxyl on 2008-10-01
*bump*

---

### Post by wolfen69 on 2008-10-01
i don't know, but there *could* be a problem with your video card. why not use ubuntu without the drivers? then you could sell your video card and get another one. to me, not having 3D is better than dealing with windows. just a thought.

i use a 7300gs nvidia card and have fantastic 3D effects. it doesn't take the latest and greatest card to get good 3D in linux.

---

### Post by mikeize on 2008-10-01
Sorry man, that sucks.  I am running fine using that same card, and I don't recall having any real trouble.  Not to patronize you, but have you checked to make sure that the card is physically seated properly?  Otherwise the above advice about selling your card and buying a new one might be the easiest solution at this point.  Seems like I've seen a lot of good deals on them lately.  Good luck.

-mike

---

### Post by Knuxyl on 2008-10-01
lmao is the card positioned right? hahaha yesss if it wasnt it wouldnt work. i play games on vista with aero enabled alllll the time, its fine. i had this same problem with fedora a long time ago. my card is PNY or something like that NVidia Geforce 8500GT 512mb, i doubt we have the same card if urs works....and i am not selling this card, not trying to be a dick, but thats kind of a no **** if it doesnt work but i asked HOW do i make it work, not alternatives.

---

### Post by gr3g972 on 2008-10-01
maybe you should reinstall ubuntu and use envy-ng for your nvidia card 
because i have ubuntu 8.04 install on my pc i have my nvidia 8600gt working fine so try it and let me know

---

### Post by Knuxyl on 2008-10-01
i have tried alllll the drivers. can u give me a step by step procedure to installing it? cuz the way i did it didnt work.

---

### Post by hansblitz on 2008-10-07
yeah i had the same problem too. i've just started using ubuntu so i pretty much stumbled arounf the place. but i got my 8500gt to work at a higher resolution (it was defaulting to 1280x768) by using the "screens and graphics" app thing in the applications menu. i just specified my screen and changed the grapics card to gforce 8 series and after a restart it just worked! with extra visual effects and all!

hope this helps

---

### Post by rakan_dr on 2008-10-08
the drivers are poor, i agree. I have GT8500 512, and the system isn't stable

---

