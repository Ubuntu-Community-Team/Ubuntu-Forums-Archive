---
title: "My new PC - a little disappointed..."
date: 2008-07-19
forum: Multimedia Software
---

### Post by Bonez56 on 2008-07-19
Hi all,

Well my tax refund came in and it's been about 4 and a half years since I spent any money on my poor old desktop PC, so I headed down to my local PC store and got all the parts I wanted to build myself a nice new machine. The specs are:

Gigabyte M750SLI-DS4 mainboard (with Nvidia chipset)
AMD 64 AM2 dual core 6000+ (3000mhz)
4gb Corsair DDR2 1066mhz (these babies have their own heatsinks and fan cooling system attached!
ASUS Nvidia 9600 GT 512mb DDR3 PCIe video card
36gb WD Raptor 10,000rpm (system boot)
2x 500gb WD 7200rpm (planned to set up in a RAID mirror)
Thermaltake Case with 430w PSU
ASUS Dual layer DVD writer
TP-Link USB Wireless G adapter (Ralink chipset)

So, I get home on Friday after a long day at work and spend a couple of hours carefully building the box.

My nightmare started after a smooth installation of Ubuntu Hardy 8.04.1, 32bit x86 edition.

Firstly, the mainboard has a Realtek ALC889A sound chip on board. The audio was extremely distorted and crackly, thus rendering it as useless as an ashtray on a motorbike. Ok, so this appears to be a known bug. Some may call it a bug, others may call it "brand new hardware, give it time for us to build in support! (see [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3765](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3765)). A mate of mine had a surplus Creative Audigy 7.1 PCI laying around which he gave me, great – audio problem solved!

Now, the biggest issue of all – and the only thing stopping me from being a happy person right now is that for the life of me I can not get my Nvidia 9600 GT to work. After a fresh Ubuntu install, it uses the VESA driver and gives me a good resolution, but I can not make use of any of the 3D features due to driver problems.

Firstly, I tried the restricted drivers package by enabling the nvidia-glx-new package from System > Administration > Hardware drivers.
After a reboot, I get a blank screen. Google confirms that Ubuntu is using an older Nvidia driver and there is no support for my card.

Next step, I tried EnvyNG. Envy does not detect the card straight off the bat and suggests that I may manually force the install at my own risk, just to see if it works or not. Well, I can assure you that it does not work :(

Final step, and I thought I was seeing some light at the end of the tunnel with this one, was to download the binary package from nvidia.com and manually install the driver, get it to compile a module etc and all would be sweet. Not so. The Nvidia package says that my card is supported, others on various forums I have googled have had some success with this method, but I still keep running in to dead ends, like a lot of other people it seems. The module compiles and installs, but same as step 1, when I reboot, I get a blank screen and Gnome does not start.

This is all making me quite frustrated at the moment, i've spent about the last 48 hours at home like a hermit with about 40 firefox tabs open at any one time, reading forums from all around the globe trying to get this damn graphics card to work.

So my question to fellow Ubuntu users – does anyone have one of these cards, and did you get it to work with the correct driver? If so, could you please give me some advice?

I have since also found out that my mainboard only has fake raid, and have not even attempted using dmraid or any of those tools to set that up, i'm just taking it one step at a time.

It appears to have bitten me in the *** by going out and buying brand new hardware. I tried to stick with good, popular brands but it appears that Ubuntu is still a little bit behind in terms of bleeding edge hardware.

Any help would be very appreciated.

---

### Post by JagDragon on 2008-07-19
Have you run the nvidia xconfig program? Are you able to post us your /etc/X11/xorg.conf so that we can diagnose the issue?

PS You may have been better off getting a Core 2 Duo. AM2's may be cheap, but for a good reason.

---

### Post by Neo0351 on 2008-07-31
ive just got the same motherboard and i cant get any of the sensors to work on it, so i guess i wont be OCing anytime soon.  and you're right about the sound, which is weird cause it works fine in gentoo.  anyways, this how to install you're 9600gt.  download the driver from nvidia, then follow this thread.
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)
hope this helps.

---

### Post by ezsurfer on 2008-12-29
conez, this may be totally useless, but, I had this experience recently, and it's so Microsoftish, I really hate to admit it worked, but after having an install lose my desktop entirely, and after many potential runs of text files to try to get Nautilus back, and various other seeming software/video driver issues, I reinstalled Ubuntu, from someone's prodding.

On the reinstall, it miraculously came up all working, all the past issues to the video went away.

Still had to repair the Bose speaker system and such, but for something that destroyed a few days of work, the only really good fix was simply to reinstall the OS.  And yes, I tried upgrades and updates, none worked.  

Just thought sometimes we get so used to correcting issues, there is the possiblility that something glitched on the install.  That's the only thing I could ever come up with...


Clif

---

### Post by cariboo on 2008-12-29
You may want to update to Intrepid v 8.10 as there is a new version of Xorg and newer much better Nvidia drivers. Hardy is an LTS release, so it doesn't use some of the bleeding edge drivers that are needed for newer hardware.

Jim

---

