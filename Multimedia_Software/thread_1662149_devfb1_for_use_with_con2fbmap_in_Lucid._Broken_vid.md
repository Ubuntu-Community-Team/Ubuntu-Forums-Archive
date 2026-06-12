---
title: "/dev/fb1 for use with con2fbmap in Lucid. Broken video chip workaround for dual head"
date: 2011-01-07
forum: Multimedia Software
---

### Post by rulesmaster on 2011-01-07
Hello to the Ubuntu Forums Community. 

Although I'm an experienced linux user this is my first post in any forum. This is really troubling me and it's a little beyond my current capacities. The story is long, bear with me if you can. If not, skip to the end of the post and the real questions are there.

A little history: I broke my integrated video in my laptop (I abused, and it went down) so I couldn't use it anymore with my ubuntu 9.10. The system froze after 5 minutes of use. I also had windows xp and my computer froze there after 5 minutes too. No hope there. Tried to reinstall and other os-s. Nothing, not even vesa driver helped

After some months of letting it rest, I tried to poke around. Installed Windows 7 and it worked! The instalation went through but, I couldn't install the driver for the video card (ATI MOBILITY X600). So confirmed. Video chip broken, but still hanging in low-hardware standars. Just and stretched 1024x768 to fit 1280x800 which is my laptop's  screen resolution.

Tried Ubuntu 10.04. I could install it, and to my surprise, even the effects were working for a while. But, after some time, the screen would display a big black block instead of the w's or the y's or g's. And eventually it froze. But to my pleasant surprise, not the whole system. Just X. Went to console and error:

"couldn't shedule IB:"

showed all over. Confirmed again. Chip can only work in "low hardware demands mode"

Killed GDM and started poking. This is where the fun begins. 


Vesa driver is no longer available in Ubuntu 10+ but I didn't know
(I'm running Ubuntu 10.04.1)

I tried what I knew. When on to create a xorg.conf out of failsafe. But I tried vesa as driver. After hitting wall discovered that fbdev is the right one.

Ok. Screen Shows. But displays on 1024x768 and my laptop screen is 1280x800. 

Since it  all changd since I first learned ubuntu, i did research and found out about fbset. Great because I had tried xrandr with no effect and different xorg.conf including very exxplicit monitor modelines and default depths withno effect also.

stoped GDM on all runlevels. 
restarted in console mode. 
Use ' fbset -g 1280 800 1280 800 32 ' 

---> console is in 1280x800

woohoo!

now... what if i do an old 

startx 

:S

No Protocol specified
..
No Protocol specified
..

ok.. killed it
sudo start gdm

---> woohoo! X display correctlyy in 1280x800.

ok, the hard thing.

I still want to have my double monitor setup even with fbdev.
So still more research and found out aboout:

con2fb (which now is a con2fbmap command)

however, con2fb needs that a /dev/fb1 exists.


-----HERE ARE THE QUESTIONS---- 

1- How do I set up the command

fbset -g 1280 800 1280 800 32

BEFORE gdm starts.?

2.- What is the VGA output in a laptop? Is it some kind of mapping to the same PCI entry, the 

01:00 ATI Technologies [Radeon Mobility X600]

and if so, how could I map it to a /dev/fb1 so I could dump a console to it?

3.- Is there a way to call  the good-old fashioned startx in ubuntu 10.04?
I can't get past that "No protocol specified" barrier. I would like to see what happens calling X like that. 

4.- Also, this could help the whole situation. 

Is there a way to pass some options to the radeon driver so it works "as the fbdev would"? So that it doesn try that complex operations to have better perfomance, but it would recognize the proper resolutions. 


-----------HERE IS THE SUMMARY INFO-------------

Laptop: Gateway 7550 ("old model")
CPU: AMD Athlon 4000+ 
Video: Integrated Radeon Mobility X600

Ubuntu 10.04.1 
Linux 2.6.33-24-generic i686 (don't ask why its not 64)

xorg.conf is the failsafe one. Tried including Display Subsections progresibly more explicit with no help. I can dump them if you like.

Also if you think that you need information relevant to the matter I can post it too. 

This is breaking my capacity. HELP PLEASE! 

Again, sorry for the long post (my first)

---

### Post by BicyclerBoy on 2011-01-07
IMO
The basic video modes could work because the don't use much RAM.

This sounds like walking-wounded..
I would doubt this behavior will be reliable/consistent..

Could find the GPU or RAM chip by pressure or can of freeze spray..
There are people who can attempt repairs to these parts..

Have you tried adding material to the top of GPU/GPU RAM  to press it down on mobo.
This is like shimming the mac laptop nvidia GPU flipchip failures.

I think the best option is a use plugin video card & disable the on-board in BIOS.
Does your laptop have a mini-PCIe or some expansion slots ?

---

### Post by rulesmaster on 2011-01-08
> **BicyclerBoy said:**
> 

IMO

The basic video modes could work because the don't use much RAM.

This sounds like walking-wounded.. 

:D:D:D It's funny you call it like that. After being 'resucitated' I call this my zombie laptop

> 
I would doubt this behavior will be reliable/consistent..


Indeed. It works even on heavy demand (you tube fullscreen) for just a couple of hours

> 
Could find the GPU or RAM chip by pressure or can of freeze spray..
There are people who can attempt repairs to these parts..

Have you tried adding material to the top of GPU/GPU RAM  to press it down on mobo.
This is like shimming the mac laptop nvidia GPU flipchip failures.



This sounds good. I'll try this even if I get some other workaround.


> 
I think the best option is a use plugin video card & disable the on-board in BIOS.
Does your laptop have a mini-PCIe or some expansion slots ?


I thought so too when the blessed thing crashed. Just checked specifications. It has one PCMCIA Type I or Type II cardbus.

However... I couldn't find plugin video cards information. I just searched for it real quick on ebay or something but didn't know how to call it or if such video cards existed. Could you point me out some online directions? :)

Thank you so much for your reply. And regarding the possibility of getting a /dev/fb1 for the "fbdev" driver? Do you know if possible or not?

Thank you again! Long live the zombies. (sic)

---

### Post by BicyclerBoy on 2011-01-08
PCMCIA video card exist
USB video adapters as well

I imagine they have very poor 3d performance.
But for basic housekeeping/booting & backend tasks would be fine.

Some poor sod was struggling with one & *buntu 10.04 couple months back.

I enjoyed reading your post but am sorry I not able to suggest anything useful.

---

### Post by rulesmaster on 2011-01-17
Well... After some time poking.

The best was to use the radeon driver. But I had to pass some arguments to the GPU.

I read a little of the documentation and found this that I passed to the driver on the appropiate section


Option "NoAccel"
Option "Dac6Bit"   <---- This is particurally what did the trick. It uses 
                         the DAC on 6 Bit mode emulating "VGA Mode"


Thanks for reading, and to all the obscure tricks seekers out there. Zombies are about to rule the earth.

---

