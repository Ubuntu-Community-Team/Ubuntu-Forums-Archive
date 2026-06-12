---
title: "ATI and nVidia Drivers &quot;Download &amp; Install&quot;"
date: 2005-12-30
forum: Multimedia &amp; Video
---

### Post by Jaygo333 on 2005-12-30
I installed Ubuntu about a week ago from windows and want to install the motherboard and graphic drivers. I "think" I downloaded the right packages from ati and nvidia but don't know how to install them.
My PC Specs. I have an Ati All in wonder 9600 XT graphics card and an Abit NF7-S2 motherboard with nforce 2 that I use as my sound card. I want to install the Ati and nVidia drivers but don't know how to. Any help as to where to "download" the right packages (I don't know if I have the right and updated packages as I got them from a russian site somewhere) and "how" to install those packages. 
I try to play some of the 3d games  that ubuntu has but the graphics all lag. I know they are not installed because, when that happened in windows(bleH), I installed the Ati drivers and everything was fine.

Any help anybody1?1

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by DoorGunner on 2005-12-30
Hi 

first backup your xorg.conf file
$su
password
# cp /etc/X11/xorg.conf /etc/X11/backup-xorg.conf

next download the ati-drivers

$sudo apt-get install ati-driver-fglrx
$sudo apt-get install fglrx-control

reboot

I found if i didnt reboot i could  not get fglrxconfig to work. The reboot will set the ati drivers in place but will allow you to login using your origional xorg.conf file perameters. Next you will need to config your fglrx (drivers) answer the questions with respect to your computer.

$sudo fglrxconfig

Next we need to check the xorg.conf or your new fglrx file
$sudo gedit /etc/X11/xorg.conf

Somewhere near the top you will see a group of LOAD instructions.
ensure in this list the fol. are listed. If not just add them in after any of the group. 

Load "extmod"
Load "fbdevhw"

I added mine in after the GLX module

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a
 Load "extmod"
 Load "fbdevhw"

close, save and reboot
------------------------------------------------------------------------
Testing

$ fgl_glxgears. 
You should see a cube with gears turning in it and you should get speeds of around 500 - 900 fps.

$glxgears 
you should have around 3000 to 5000 fps. glxgears didnt work for me but fgl_glxgears did for me. I was satisfied with that.

also to confirm you can try fglrxinfo 

you should see the fol

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

If you get mesa instead of ATi Technologies or no fgl_glxgears it means your driver did not set properly.
---------------------------------------------------------------------

For some reason if you miss a step or something goes wrong dont panic. you will still be able to remove the ati-driver-fglrx and fglrx-control and copy the xorg backup file back. It might be a good idea to print this instruction set out prior to implimentation.

---

### Post by kaamos on 2005-12-30
[QUOTE=DoorGunner]
$su
password
[/quote]

This should be replaced by

$sudo su
password

---

### Post by Jaygo333 on 2005-12-30
[QUOTE=kaamos]This should be replaced by

$sudo su
password[/QUOTE]

What's the difference between normal $su and $sudo and $sudo su.
Aren't they all the same1?1

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by Fibre on 2005-12-30
Hi guys I've got on the band wagon. I've been trying to get it to work but have noticed that when I get to :-

$sudo apt-get install ati-driver-fglrx

I get :- 

fibre@ubuntu:~$ $su
fibre@ubuntu:~$ # cp /etc/X11/xorg.conf /etc/X11/backup-xorg.conf
fibre@ubuntu:~$ $sudo apt-get install ati-driver-fglrx
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Where have I gone wrong ?

---

### Post by DoorGunner on 2005-12-30
I suspect you need to do a few things first. Like setting up apt-get.  Go to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  This site is a good place to start. Start at "How to add extra repositories" It was made for Ubuntu hoary. The key is to know that you are using breezy not hoary so just remove the # on the apropriate lines. Dont change the wording.

Once you get apt-get set up properly find the build essentials section.
$sudo apt-get install build-essential

This is what you need to install your drivers. Then you can go back to installing your driver with our instructions here. :D  

you will find that site helpfull in future installations and need to go back and start it in order and work your way down. It will get you all the basics you need for a fully functional computer.

---

### Post by Fibre on 2005-12-30
Excellent Buddy I'll go give it a go and forgive me for intruding Jaygo333.

Thanks DoorGunner will do.

:)

Oh yeah I saw that before but the sections in it that relate to hoary turned me off it. So what your saying is anything that says anything relating to Hoary take the # out of the front of it and that's it.

Ah here it is found a better - I think - this one is for Ubuntu 5.10 breezy - 

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Just Saves me with the Hoary side of it, Thanks again DoorGunner for pointing me in the right direction I'll see how I go.

---

