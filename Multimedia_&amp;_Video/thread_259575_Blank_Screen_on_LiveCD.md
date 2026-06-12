---
title: "Blank Screen on LiveCD"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by Orbital75 on 2006-09-17
Hi I'm new to Linux and Ubuntu. I down loaded the lastest Ubuntu (6.06.1) Burned the Iso image to a CD and then Rebooted. Well the LiveCD will go through the entire process boot my machine but when it gets ready to finsh and go into the Desktop the sceen turns completely black and then I hear the Theme music in the back ground. I looked at my monitor and the Active light goes from Green to Amber like it's in standby. It seems to be the OS is booted and ready to go but can't display anything. What can I do to solve this. I just want to use it as a live CD for right now to get use to all the linux programs. Below is my config.....

OS: Windows XP Pro ( Service Pack 2 ) ( All Patched )
CPU: AMD Athlon XP 2800+
Mobo: ASUS A7V600 - X
RAM: 1024 Gigs DDR Ram
Video: Geforce FX 5200 ( 128 DDR )
Sound: Intergrated SoundMax Audio
Magnetic: ( Two ) 40 Gig ATA HD
( One ) 80 Gig SATA HD
Optical: Lite-On DVDRW, Lite-On CDRW
PSU: Antec TruePower 430 Watt Power Supply

---

### Post by DarkGaucho on 2006-09-18
I have this same problem, so I thought I'd post here rather than start a new thread.

Everything is exactly as described by Orbital75, except my monitor displays the following message....  "ATTENTION: Signal frequency is out of range, please change signal timing."

Of course, I can't change anything, because I can't see anything on the screen except the message. (although like Orbital75, I can hear the theme music starting-up in the background)

My main hardware is as follows.....

CPU:  Intel Pentium D805 (2.6gb dual-core)
Mobo:  Gigabyte 81945G
RAM:  2 x 512mb Corsair value-select
Video:  Intel 82945G Integrated Graphics Controller
Monitor:  Mitsibishi Diamond Plus 71

I would like to run ubuntu as my primary O/S on this system, so any help or advice would be greatly appreciated.

Cheers,
DG

---

### Post by hannesz112 on 2006-09-18
same problem here. 

The live cd boots and it starts the "start up" sound.
But nothing happens on the screen. Also in the save mode. 

CPU: AMD sempron 2800 +
Mobo: no idea it's an laptop acer aspire 3020
RAM: 512 MB
Video: Ati X700

---

### Post by TLE on 2006-09-18
Most probably what the problem is in all three cases is that the frequency is indeed out of range. Meaning that however the LiveCD is set up to send signals to a screen of your type doesn't fit it, and so as a safety precution the screen switches off. People have had problems with this before, mostly when using flat-screens and/or notebook screens with a non-standard proportion (meaning not 4:3 or 16:9). Try to start the LiveCD in safegraphics mode and let me know what the result is.
Regards TLE

---

### Post by hannesz112 on 2006-09-18
TLE

It also doesn't work in safe mode. I also tried to change the resolution as low as possible. 

But the funny thing is that i already had it running. But i f*ck*d up something so i tought a complete format of the HD and re-install the laptop would be the solution.

any ideas........?

thnx

---

### Post by skutterdan on 2006-09-18
Hi. I had this same problem with one of my pc's. I have Nvidia 5600 and got same blank screen. it is indeed a problem with refresh rates. You'll have to edit your xorg.conf file. 

1. boot from live cd

2. when Ubuntu has finished loading wait till you hear the theme music and press Shift+Alt+F1. you'll get to the terminal screen.

3. Type "sudo nano -w /etc/X11/xorg.conf" (note it's X11 not x11 or Xll!)

4. scroll down the config file using your cursor keys until you see:
 **Section "Monitor"** 

 **EndSection**
5. Enter the following lines:
   " DisplaySize     320    240
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0 " (erm.. without the quotes ;) )

6. press ctrl+o to save. Press enter and press ctrl+x to exit the nano editor.

7. press "shift+alt+backspace" if this works then you should get to see the ubuntu login screen. If you get a blank screen the press "shift+alt+F1" and return to the terminal screen.

8. enter "sudo /etc/init.d/gdm force-reload" and then follow step 7.

Hope this is of some help

---

### Post by hannesz112 on 2006-09-21
Skutterdan

Everthing goes fine until i put in "sudo /etc/init.d/gdm force-reload"

```

* Stopping GNOME Display Manager....     [ ok ]
* Starting GNOME Display Manager....     [fail]

```

As shown above it won't start GDM. 
Do you have any idea why?


thnx

---

### Post by hannesz112 on 2006-09-21
Woohoo

I made it.

Just run ```
sudo dpkg-reconfigure xserver-xorg
```

Leave everything default en then after the setup is done run :

```
sudo /etc/init.d/gdm force-reload
```

many thnx

---

### Post by skutterdan on 2006-09-22
Hey. Glad you got it sorted out. I did originally try
 
sudo dpkg-reconfigure xserver-xorg

But found that it never quite saved the file properly. Still at least we both get to use a decent OS! :D

---

### Post by yultanman on 2006-09-22
I have a cousin who is cross country that i am trying to assist. We can get to the boot menu of the live cd but once it has booted and the screen goes black we seem unable to obtain even the text mode login using CTRL-ALT-F1 or SHIFT-ALT-F1 or ESC or SHIFT_ALT_ESC or CTRL-ALT-ESC

I would suspect hte video card malfunctioning but it does allow us to see text when it is booting and the initial login screen. 

We have tried forcing the graphics to 600x480, VGA and the 'Safe Graphics Mode'


Anyone have any other suggestions for us. He does not have another computer so we are unable to download any other tools easily.

Any other suggestions?

---

### Post by GadgetsGuy on 2006-09-30
['Frequency Out of Range' fix for Ubuntu Dapper]("http://www.hotubuntunews.com/blog_03.shtml")

:cool:

---

### Post by RodM on 2006-09-30
I have this result with a probable different cause. I am very keen to get Ubuntu running on my Fujitsu Siemens Scaleo PC. Similar to other users the screen dissapears but the program continues and the theme music is heard (Ubuntu is the only Linux that has fired up my Realtek High Definition Audio). :confused: Please help. The chipset is Intel 915GL x86, Graphics Media Accelerator with acer AL1511 flat screen display. 
  
When loading using defaults I get some error messages:
..loading hardware drivers..
[17179644:652000] hw-random : RNG not detected  (number can change)
..loading manual drivers..
mount : Function not implemented..
..Starting Gnome Display Manager   (which fails, hence black screen)

If I use the expert option or "sudo-reconfigure xserver-org" then I get:
VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
Please append a correct "root=" boot option
Kernel panic -not syncing:VFS:Unable to mount root fs on unknown-block(8,1)

---

### Post by mthomason on 2006-10-21
I've got the same basic problem as others in this thread (blank screen after boot) with the following differences...

If I select Normal boot, then Ubuntu loads OK (in low res) and then switches to a high res mode with a blank/black screen...and that's it.  No music and Alt-Shift-F1 doesn't seem to do anything.

If I select Safe Mode boot, then Ubuntu loads OK (in low res) and then switches to a high res mode with a blank screen for a few seconds, then monitor sleeps.  I then hear logon music and CD then spins down...and that's it.  Alt-Shift-F1 doesn't seem to do anything.

I'm Ubuntu-less...Got help?

Athlon 64 3500+  AMI Motherboard
ATI Radeon X800 Pro
1GB RAM

---

### Post by TLE on 2006-10-22
> **mthomason said:**
> I've got the same basic problem as others in this thread (blank screen after boot) with the following differences...

If I select Normal boot, then Ubuntu loads OK (in low res) and then switches to a high res mode with a blank/black screen...and that's it.  No music and Alt-Shift-F1 doesn't seem to do anything.

If I select Safe Mode boot, then Ubuntu loads OK (in low res) and then switches to a high res mode with a blank screen for a few seconds, then monitor sleeps.  I then hear logon music and CD then spins down...and that's it.  Alt-Shift-F1 doesn't seem to do anything.

I'm Ubuntu-less...Got help?

Athlon 64 3500+  AMI Motherboard
ATI Radeon X800 Pro
1GB RAM

You should try and reconfigure your Xorg as described on the page GadgetsGuy linked to. But to do that you do off course first need to get to the terminal. When you have booted and you have a black screen, please try to push CTRL-ALT-F1   NOT...   ALT-SHIFT-F1, if that works follow the guidelines I referred to earlier. If it doesn't post back here and we'll se what we can figure out.

---

### Post by Orbital75 on 2007-02-13
TLE,
  I have tried your method but my monitor still goes into power save.
I waited as you stated for the Theme Music to start then hit
Shift+Alt+F1 but my monitor still goes black and the Amber light comes on.
I have tried hooking a CRT to it and the CRT displays Out Of Range.
All versions of Ubuntu worked fine before version 6. I can't even get to
a command prompt if I let it go through the process of running the live
CD.  I have options at the beginning that I can try such as boot options
VGA and what not.  I have tried the lowest VGA Settings and Safe Mode
but all end up with the same result.  Any idea?

I am running a Sony SDM-HS74P lcd monitor and a Geforce FX 5200 ( 128 DDR )
Video card.

I hooked up a Compaq MV520 crt to see if it was the driver but that seems not to
be the case. The Compaq crt displayed OUT OF RANGE.

Any idea how I can fix this.......

---

### Post by TLE on 2007-03-08
I told you to push ctrl-alt-f1

---

### Post by AySz88 on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/140908](https://bugs.launchpad.net/ubuntu/+bug/140908) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Since this thread was at the top of several of my searches, this might be helpful for some people in the future:

If you have an nVidia 8800 card, select the option from the menu that you want, then press "F6" and delete "quiet" and "splash".  Then you'll have to boot into recovery mode, and edit /boot/grub/menu.lst.  See [https://bugs.launchpad.net/ubuntu/+bug/140908](https://bugs.launchpad.net/ubuntu/+bug/140908) for details.

Sorry for resurrecting the thread.

---

