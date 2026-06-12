---
title: "Changing motherboard with onboard X1250-based graphics on Ubuntu"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by MentholLite on 2007-09-24
Hi guys,

my motherboard just died on me last week, and I got a new motherboard and CPU with onboard graphic and network interface.

Now when I startup ubuntu, I am unable to access GUI as it prompted me that x11.conf is incorrect on video card settings.
May I know what is the correct way I should go about rectifying this problem?

Thanks in advance.

---

### Post by w4ett on 2007-09-24
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa" or "ati"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from AMD/ATI [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to purge the old fglrx drivers and then  install the correct ATI  proprietary driver.

Good Luck

---

### Post by MentholLite on 2007-09-24
W4ett,

thanks for the detail instruction.
Will get back home and try this after work. :)

---

### Post by maluka on 2007-09-28
is there a way of installing these drivers once ubuntu is installed but i am unable to boot into a gui?

---

### Post by w4ett on 2007-09-28
> **maluka said:**
> is there a way of installing these drivers once ubuntu is installed but i am unable to boot into a gui?

You can reconfigure your xorg.conf to use the vesa  driver and then select the Restricted Drivers Manager to  install the proprietary drivers.

---

### Post by maluka on 2007-09-28
i get this message:

Fatal server error :
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remaning.

this machine has ATI raedeon xpress 1250 graphics

---

### Post by w4ett on 2007-09-28
Maluka, try the tutorial from this sticky in the beginners forum:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by maluka on 2007-09-28
i've tried that. it also doesn't work

---

### Post by maluka on 2007-09-28
i found this post also related to these cards but still no solution!!!: [http://ubuntuforums.org/showthread.php?t=503695](http://ubuntuforums.org/showthread.php?t=503695)

i've been trying for almost a week now! is my only option to return this machine to the store?

---

### Post by maluka on 2007-09-29
FINALLY!!!
:popcorn:

there were a few things i needed to do that were spread out over a few threads.

from this thread: [http://ubuntuforums.org/showthread.php?t=503695](http://ubuntuforums.org/showthread.php?t=503695)

> 
Code:

sudo update-pciids



then on to:[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

 
>    
   1. Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
   2. Start text mode installer and install Ubuntu/Kubuntu.
   3. Finish Install and reboot.
   4. Update package list and upgrade any packages needed.
      Code:

      sudo apt-get update
      sudo apt-get dist-upgrade

   5. Install fglrx closed source driver for ATI video cards.
      Code:

      sudo apt-get install xorg-driver-fglrx

   6. Update loaded modules.
      Code:

      sudo depmod -a

   7. Configure /etc/X11/xorg.conf
      Code:

      sudo aticonfig --initial
      sudo aticonfig --overlay-type=Xv

   8. Reboot


a BIG thank you to everyone who offered advice. you all ROCK!!! :guitar:

---

### Post by Chops 666 on 2007-10-30
> **maluka said:**
> FINALLY!!!
:popcorn:

there were a few things i needed to do that were spread out over a few threads.

from this thread: [http://ubuntuforums.org/showthread.php?t=503695](http://ubuntuforums.org/showthread.php?t=503695)



then on to:[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

 


a BIG thank you to everyone who offered advice. you all ROCK!!! :guitar:

Does anyone know if this fix will work for AMD chipsets aswell?  I am a total linux noob and am beginning with Ubuntu 7.10.  I see the person above used the Intel version.  Of course I bought all the hardware first and decided on a whim to try linux,  No matter how many times it screws me, I never learn to read before I try something.

---

### Post by chiques on 2007-10-30
Ubuntu (7.04 and 7.10) work fine for me when I ONLY use a VGA monitor. I'm in the process of setting up Linux Media Center (only Ubuntu 7.04) and LMC has a setting to configure my HDMI monitor. I'm going to download the Linux based ATI drivers ([http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)) and CROSS MY FINGERS THEY INSTALL :guitar::guitar::guitar::guitar::guitar:.

THEN AFTER INSTALLING MY ATI DRIVERS FOR THE X1250, I WILL SHUT DOWN. I'LL THEN PLUG IT IN AND REBOOT.....to be continued...:popcorn::popcorn::popcorn:

---

### Post by jaxån on 2008-04-21
(and he got losted)

---

### Post by Puejo on 2008-06-02
Hi to everybody,
i saw your post and folowed your instruction ...
and .. my X starts ... unbelievable but there is just a white screen with my mouse 
and i can start programms with klicks but i cant see any menus or icons or some other things on my desktop
does anyone know what is going on there?
what can i do ?
i hope anyone understands my post because my english is really bad 
Greeting and thx to all for reading and maybe helping
puejo

---

### Post by Offoffoff on 2008-07-15
Just turn on "Composite" in xorg.conf...

---

