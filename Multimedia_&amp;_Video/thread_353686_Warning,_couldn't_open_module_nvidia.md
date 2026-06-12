---
title: "Warning, couldn't open module nvidia"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by o4tuna on 2007-02-05
Trying to install the legacy driver
GeForce2 TI400
Athlon 3000+ 1G
Ubuntu 6.10

First, used the instructions in the sticky for legacy, nothing changed.

Second, downloaded the envy script from Tseliot
Now all I can get is command line:( 

"Failed to start X server. it is likely not set up correctly. Would you like to view the X server output....." . i click no, then it says "The X sever is now disabled. restart GDM when it is configured correctly."

I have booted the live cd & mounted the hdd where this mess is at.
The xorg.log sez:
blah
...
blah
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
blah
...
blah
(EE) No drivers available.

Fatal server error:
no screens found

How can I restore it to plain old vga?
HELP?

---

### Post by glotz on 2007-02-05
In /etc/X11/xorg.conf, change nvidia to nv.

Before that, does your /etc/modules contain nvidia?

---

### Post by o4tuna on 2007-02-05
> In /etc/X11/xorg.conf, change nvidia to nv.
Done, I'll reboot here in a sec to see if it worked...

> 
Before that, does your /etc/modules contain nvidia?
no.
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

---

### Post by glotz on 2007-02-05
Either your boot time needs working or..? :D

So, you either go back to using nv or add the nvidia line to modules.

---

### Post by o4tuna on 2007-02-05
Well, that *kinda* worked....

Changed the nvidia stuff to nv, rebooted.
Gives me an error about ```
$HOME/.dmrc file has incorrect permissions and is being
ignored. ... file sould be " "owned by user and have 644 permissions
```
Logged as root, (all the files now belong to the user 999?!?)
:confused: :confused: 
There is no internet connectivity in root?
Is the system that hosed up, or are you guys are takin' the "protect the n00bs from themselves" thing a bit too far?

Possibly reading the solution:
[http://www.ubuntuforums.org/showthread.php?t=91455](http://www.ubuntuforums.org/showthread.php?t=91455)

Why does this have to be so hard?

I've actually authored several thousand windows support knowledge base articles, a couple of which actually made it to MS technet. I'm not an idiot, I can be a bit obstinate at times, but I'm pretty good at figuring things out - in dos/windows...

I've attempted to use various flavors of linux every 9-12 months since around 94. I've *never* gotten one to work to my satisfaction, yet.

After the latest piece of malware, I once again decided to try. I even made a list of the apps I use, found out which ones have linux counterparts or will run in WINE. Looked pretty do-able.

I'm actually kinda fond of Puppy, but the .pup/pupget offerings are a bit sparse. Ubuntu, being an offshoot of Debian seemed a good choice.

So, here's what gone wrong so far:
1. Couldn't resize the ntfs partition, even though it was 95% free (I just deleted it)
2. Randomly changing drive assignments [https://launchpad.net/ubuntu/+source/grub/+bug/8497](https://launchpad.net/ubuntu/+source/grub/+bug/8497)
3. It is a major pain in the *** to command line mount my drive(s) every time I boot from the livecd.
4. The livecd takes an ungodly amount of time to boot (puppy is way faster, why?) Troubleshooting takes a lot of reboots=a lot of my time.
5. This video driver thing, OMFG! OK, OK, Windows does suck pretty bad, but for cryin out loud, Why should I have to be a shell commando just to frickin' install a video card driver. And this is supposed to be from the video card company that loves linux, glad I didn't buy that radeon I was looking at the other day!
6. Linux documentation sucks bad! It either is for n00bs, "here type this in" with no explanation as to what is does or means, or how to adapt/manipulate it, or for advanced experts, with much prior knowledge: In order to do Z, do A & B, verify F & discombobulate R. WTF?

Ok, I'm done ranting, for now.

Any suggestions?

PS, I promise if I ever get a Linux system to function properly, & gain some knowledge of the appropriate magic incantations, I will contribute back heavily to the documentation.

PPS, While I have a great deal of respect for people who A: are uber geek enough to contribute to the OSS movement & B live in another country, but are learning English, anyway. Reading docs written by them makes my head hurt:)  Ahhh, well, maybe I should by Tylenol stock?

---

