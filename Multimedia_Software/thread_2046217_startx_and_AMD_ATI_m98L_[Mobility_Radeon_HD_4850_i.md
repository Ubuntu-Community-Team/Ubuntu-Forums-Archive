---
title: "startx and AMD ATI m98L [Mobility Radeon HD 4850 imac] issues"
date: 2012-08-22
forum: Multimedia Software
---

### Post by paxsonsa on 2012-08-22
Hey there guys! So I am having a bit of trouble (alot) while installing ubuntu. Ranging from Grpahical to Network. For whatever reason Ubuntu doesn't seem to like my iMac (and vice versa) 

So here what I have done. 
-Installed a Commandline System of Ubuntu 12.04 LTS Only because when I did a normal install with the LiveCD Ubuntu system would start but! for some reason my screen came on black. 
-Installed the build essentials and Ubuntu-Desktop
-Next because i knew it was a driver issue I proceeded to install the Drivers from the Ubuntu Severs (ie sudo apt-get install fglrx fglrx-amdcccle)
-Updated the System

Note: Did not reboot yet kinda a hesistant

-next I wanted to test desktop and make sure its working so I "sudo startx" 
-the first time the desktop background load but it hung there. I let it sit for about 30 mins and the cancelled in the tty. 
-I looked at the Output from the Terminal forwhen I started startx I got a couple errors/warings:

```
(ww) fglrx: No matching Device section for instance (BusID PCI:001:0:1) found
``` 

I switched back to CTL+ALT+F8 and the display still hung with the Desktop BG and only the mouse which worked fine.

I cancelled the program and ran it again. This time it didn't even load. I got the same warning above along with 

```
No protocol specified
```

which repeated on screen til startx terminate itself

so then I did some digging and looked at the LIBGL_DEBUG=verbose glxinfo which all it said was "Error: unable to open display"

What I need:
-startx to work
-to have a working Desktop Enviroment and GUI
-Gnome 3 
-3D Accerlation (I am a VFX Artist)

System:
27 in iMac (late 2009)
Intel i7 Core
1 TB Hard Drive (50GB for Ubuntu [20 for '/' and 25 for '/home'])
4 GB Ram
AMD ATI Mobility Radeon HD 4850 512mb

Resources Thus Far:
-
[http://ubuntuforums.org/showthread.php?t=1476226](http://ubuntuforums.org/showthread.php?t=1476226)
-
[http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip)
-
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Test_your_installation](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Test_your_installation)
-
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
-


Lemme Know What you Need and I will get it to you ASAP!
I am a relatively newbie nix user so I could use the help because this much work for Ubuntu is making me wonder if Arch is easier lol!

---

### Post by paxsonsa on 2012-08-22
No takers? Arch it is

---

### Post by QIII on 2012-08-22
When you first installed fglrx, did you do

```
sudo aticonfig --initial
```

before shutting down to generate an initial xorg.conf from the driver to work from?


Be a little patient.  We are all volunteers here, we are here as we have time and yours is not the only question asked.  We have lives.  The community is world wide.  The person with the right answer may be asleep, at work, having dinner with his/her kids, on a date with the wife or out golfing when you post.

If you don't have an answer in 24 hours, bump your thread.

---

### Post by paxsonsa on 2012-08-23
Yea I did and sorry to be short I am very frustrated after 3 weeks of testing and tweaking lol. 

I am going to do a fresh install of the command line system and go from there and reinstall everything!

Thanks! I will let you know!

---

### Post by waffleguy4 on 2012-09-19
I'm having this same issue on a MacBook Pro 8,2 - I cannot boot into the graphical desktop and startx does not work. Let me know if any progress is made!

---

