---
title: "Gnome doesn't load after upgrade"
date: 2010-08-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by michaelreno on 2010-08-25
Hello Everyone, Iv'e never posted a thread here before because I've always found the answer in a existing thread, but no this, I ran the upgrade from 10.04 to 10.10 and after reboot My "Gnome" no longer loads. Instead it takes me to a tty login screen, I type my user name and password and it tells me:

0 packages can be updated
0 updates are security updates.

-bash: no job control in this shell
michael@reno-laptop"~$

Can anyone point me to an answer?
Thanks

---

### Post by cariboo on 2010-08-25
It can be several things, if you can start in recovery mode, press the shift key to see the grub menu, then select ecovery mode. Once at the prompt type:

```
apt-get -f install
```

If that installs more packages, or even if it doesn't, type:

```
exit
```

at the prompt, then select resume from the menu. Once you have logged in, type:

```
startx
```

to see if X starts.

It might also help if you were to let us know what type of hardware you are running.

---

### Post by michaelreno on 2010-08-26
Thanks for your attention on this, I tried your suggestions on the first step I had to add sudo to the begining of the command line and it ran then on the "startx" I get error messages:
(EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.
 
Fatal server error:
no screens found
 
This is a HP TC1100 Tablet PC
Thanks again, I'm hoping to solve this without having to start from scratch.
I have extensive experiance with Windows and Dos but less than a year with Linux but Im sold on it, the preformance of it is superior but it is a learning experiance!

---

### Post by paul_in_london on 2010-08-26
Try this.

Reboot your latest kernel into recovery mode with networking (netroot option).

Reinstall nvidia-current and then reboot normally.

---

### Post by Shutter4U on 2010-08-26
I was having the same problem, but my graphics card is an Intel 915gm. So the startx error reported "Intel" as the driver that failed to load or whatever the message was.

I found the solution to be editing the file /etc/default/grub and adding i915.modeset=1 to the line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

so it looks like:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

```

of course, your driver is obviously different so you will need to google a bit to find the correct code to put in the grub file.

then type: "update-grub" at the command line and reboot.

---

### Post by fooman on 2010-08-26
michaelreno,  i have maverick installed on a spare hard drive in this rig (w/nvidia 8800gt + latest nvidia drivers installed).  i had not booted to it for a few weeks and thought it was working fine,  but earlier this week when i went to boot into it....i was stuck similar to you and "startx" would not get me to my desktop either.

what i had to do was add:

```
Section "ServerFlags"
Option    "IgnoreABI"    "True"
EndSection
```to the bottom of my xorg.conf file.  

here is how i solved it:  first reboot and choose recovery mode from the grub menu.  once there choose "failsafeX run in failsafe graphic mode" ...that should get you to the desktop.

if it does,  then run the following command in a terminal:

```
gksudo gedit /etc/X11/xorg.conf
```when it opens,  add (copy/paste) the following to the bottom of the file:

```
Section "ServerFlags"
    Option    "IgnoreABI"    "True"
EndSection
```save the file,  reboot and hopefully it will boot right up as normal.

hope that helps.

---

### Post by michaelreno on 2010-08-26
Thanks Everybody for the Great Help ! With everyones help I got that particular problem fixed I had to removed the video driver and then boot to safe graphics mode. I did not know how to remove the driver using a command prompt but thanks to "actionparsnip" from launchpad.net I used the following command line to remove the driver.

sudo apt-get --purge remove nvidia*; sudo apt-get --purge autoremove

Now That I can get in to my Ubuntu 10.10 I can see I've got several more bugs to tackle.
Thanks Again to everyone for all your help !!

---

### Post by Netrum on 2010-08-30
thanks guys.
I had the exact same problems.
But finnaly got it fixed after reading in here :)

---

### Post by michaelreno on 2010-08-30
After a few days of trying 10.10 I decided there are too many bugs and so I wiped my drive and went back to 10.04 LTS. I look forward to the official release of 10.10 I like the cosmetic changes that are in it.
Thanks Everybody !!

---

### Post by 23dornot23d on 2010-08-31
I too had to do this problem so have done as said and added
> 
     Code:
     Section "ServerFlags" Option    "IgnoreABI"    "True" EndSection 
added to the bottom of my xorg.conf file.  
What does  this code actually do ...... IgnoreABI ...... ?


Seems to be a lot of use of it - [IgnoreABI Search]("http://www.google.com/search?client=ubuntu&channel=fs&q=IgnoreABI&ie=utf-8&oe=utf-8")

It now works fine and the composite still works ..... so thanks for the fix .....
anybody know why its failing to start ..... 
I did not even get to the option of going in in safe graphics mode .... in gdm on a normal boot.

I am running it using kdm at the moment but will switch and see if it works ok in GDM.

I will add to this if I get back in in GDM

Ok I removed KDM and am now running GDM ..... and got some weird graphical glitches .... kicked me
out to the login screen as I was editing this the last time .... 

I am running the latest nvidia 256.44 driver ..... 3D programs seem ok .... for now ..... will see what happens over time ..... does not fill me with confidence kicking me out to the login screen and on the purple login background two big orange parts to it ...... not seen before........


Even after reading this - it still does not answer it - other than its a [GDM problem]("http://www.linuxquestions.org/questions/linux-desktop-74/how-pass-ignoreabi-to-xorg-from-gdm-809880/")



What the xorg log tells me ...........

```

[   135.527] (II) Module dri2: vendor="X.Org Foundation"
[   135.527]     compiled for 1.9.0, module version = 1.2.0
[   135.527]     ABI class: X.Org Server Extension, version 4.0
[   135.527] (II) Loading extension DRI2
[   135.527] (II) LoadModule: "nvidia"
[   135.527] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   135.527] (II) Module nvidia: vendor="NVIDIA Corporation"
[   135.527]     compiled for 4.0.2, module version = 1.0.0
[   135.527]     Module class: X.Org Video Driver
[   135.527] ================ WARNING WARNING WARNING WARNING ================
[   135.527] This server has a video driver ABI version of 8.0 that this
driver does not officially support.  Please check
http://www.nvidia.com/ for driver updates or downgrade to an X
server with a supported driver ABI.
[   135.527] =================================================================
[   135.527] (WW) NVIDIA: The driver will continue to load, but may behave strangely.
[   135.527] (WW) NVIDIA: This driver was compiled against the X.Org server SDK from git commit 2307ab5bc9365ebbe04568edb7c7620a23689b70 and may not be compatible with the final version of this SDK.
[   135.527] (WW) NVIDIA: This server has an unsupported input driver ABI version (have 11.0, need < 10.0).  The driver will continue to load, but may behave strangely.
[   135.527] (II) NVIDIA dlloader X Driver  256.44  Thu Jul 29 01:32:42 PDT 2010
[   135.527] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   135.528] (--) using VT number 8

```

Ok a little extra now its running ..... but it crashed out when I entered a terminal ..... seems ok after 
first crash out ..... goes in from login screen and appears to work ok then.

---

