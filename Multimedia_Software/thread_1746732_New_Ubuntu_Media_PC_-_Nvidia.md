---
title: "New Ubuntu Media PC - Nvidia"
date: 2011-05-02
forum: Multimedia Software
---

### Post by jr_taylor on 2011-05-02
[SIZE=1]Hi, 

I have recently purchased the [/SIZE][SIZE=1]Zotac IONITX-G-E Intel Atom 330 Nvidia ION motherboard for use as a media pc under my TV.  At first i put Windows 7 on the machine but have now switched to Ubuntu 11.04.  

Everything is working fine, its just the large video files are unwatchable due to the system hanging and jerking.  These files were playing fine on this same machine when Windows 7 was installed.  

So i opened up the System Monitor and noticed that my CPU was maxing out at 100% load.  Is this due to the Nvidia graphics card drivers not being installed and not taking over the work from the CPU?

So i went onto the Nvidia website and downloaded the most recent drivers for my board.  This is a .run file and i am unsure what to do with it.  When i double click it, i get the error message 

"gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."



My questions are:

Is there anywhere i can see a list of hardware and the drivers installed?  Ubuntu installs and looks as if the hardware is working, but how do i know my system is running the latest, up to date drivers available from the hardware manufacturer and not the generic drivers Ubuntu has installed?

How do i installed the drivers i have downloaded from the Nvidia website?  



If you need to know anything else then please ask and i will let you know.  

Thanks for any help in advance, 
James
[/SIZE]

---

### Post by earlneath on 2011-05-02
Sounds as though hardware acceleration "vdpau" on nvidia may not be happening. Others have reported this on 11.04. You may find you are better off with 10.10 for now. It might also be because 11.04 uses the "composite" extension in X for the new interface "compiz" and has to be disabled.

See here for ion info [http://forum.xbmc.org/showthread.php?t=100511](http://forum.xbmc.org/showthread.php?t=100511)

There is likely a better route - using supported drivers - than what you have attempted
I use the proprietary nvidia drivers but you should understand what you are getting into before you go down that route - you have to update kernel module every time you update the kernel. This may not be necessary. Suggest you look for the answer on the xbmc.org forums as there are lots of ion users there. There are even ion-specfic distributions of xbmc live built on ubuntu

To answer your question your file manager has attempted to use a text editor to open the installer file. You have to make the file you downloaded executable either in the file manager properties dialogue or in the command prompt, and then launch it from the command prompt (not from a command prompt terminal window). As it is the x video driver you cant run the upgrade from within x and what you are trying to do you might find it fiddly if you are not confident with the command line. If so, don't go down this route.

---

### Post by WannabeFantasma on 2011-05-02
How to install NVIDIA drivers (.run file)

SAVE .RUN FILE TO DESKTOP FIRST!

you can install the drivers by pressing

**CTRL+ALT+F1**

Then log in with your username and password

then **sudo /etc/init.d/gdm stop**

go to directory where your .run file is
**cd Desktop** (Or where ever you put the .run file)
then type in **sudo sh N**(press tab and Nvidia..... should become visible) press enter and it should install (you have to accept some things etc...)

after that

**sudo /etc/init.d/gdm start** and you should have your drivers installed.

EDIT: Note that you need to do this **every time** you update to a new kernel... When pc starts it tells you error click on the "go to terminal" thing and start from** cd Desktop** or where ever you put the file, till the **sudo /etc/init.d/gdm start** and you're ready to go.. 

(I saved my .run file to /home/*myname*/drivers so I can find it easily after a kernel gets updated)

good luck

I use XBMC for movies and with VDPAU enabled it works flawless (1080P without a hiccup)

(btw if you have questions, I got the same motherboard :D )

---

### Post by jr_taylor on 2011-05-08
Thanks!  Its good to know you have the same motherboard and OS as me, so really we have the same PC.  

I have downloaded the drivers to my desktop like you said, but when i try and follow your instructions, i get to the "**sudo /etc/init.d/gdm stop"** part but i am told there is no such file or directory.  

I went onto the next bit but the drivers fail to install due to there being an x-server running.  Is that what is trying to be stopped in the command i can not get to work?  



Also, do you have any tips or tricks that you have come across that you have done to your media PC?  Seeing as im using mine for exactly the same purpose as you, things you have come across might be useful.  

Thanks, 
James.

---

### Post by BicyclerBoy on 2011-05-08
For all users especially new users..
The easiest way to access the nvidia proprietary drivers is by 3rd party package repository..
Package management deals with dependencies/updates/kernel headers/install scripts etc..

IMO The nvidia installer script method is not recommended for new users with little real computer experience..there is no need to do it the hard way. 

Add the ppa into synaptic package manager
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty)
Then reload, upgrade..

You can check it is working by run the GUI
nvidia-settings
You can check openGL performance/function by running
glxinfo and/or glxgears
You can check VDPAU by running
vdpauinfo

The take advantage of VDPAU video decode you need applications that use it directly (MythTV XBMC) or indirectly VA-API-VDPAU backend (DIY build of VLC).

See MythTV/XBMC ION specific wiki pages...
VDPAU can require VDPAUbuffers to be increased/set, seems to require 512MB of total system RAM for video.

You will need to configure MythTV or XBMC to use VDPAU.
Note the ION platform can only manage VDPAU slim playback (MythTV profile) & can not do any hq scaling & can not do VA deinterlacing (2x adv DI in MythTV).

---

### Post by WannabeFantasma on 2011-05-08
> **jr_taylor said:**
> Thanks!  Its good to know you have the same motherboard and OS as me, so really we have the same PC.  


Not same OS I guess :D (still have 10.04)

Tricks, not really everything works quite good :D
(Been stable for over a year now :D )
Dissabled some start up programs to let it boot a little faster(like bluetooth/ubuntu one i don't use...)


Yeah maybe what bicyclerboy said is going to be easier for starters. so you should try that :)

And yeah take 512mb ram for the graphics card.(haven't tested less but it works and since I still have 1,5 gb left for the os there is no problem :) )

---

### Post by BicyclerBoy on 2011-05-08
The hard way:
To stop gdm from console login you need to use

sudo service gdm stop

This applies to 10.04 & later..how much later I don't know...

To compile nvidia driver you need the kernel headers package for your kernel version
uname -r

Search synaptic for kernel headers that match & install.

The kernel headers/compiling is why the nvidia method causes your video driver to break all the time..

---

