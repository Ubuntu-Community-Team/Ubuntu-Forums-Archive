---
title: "mythbuntu-7.10-amd64.iso install hanging"
date: 2007-12-04
forum: Mythbuntu
---

### Post by hoboghost on 2007-12-04
This is my first time trying to install any distribution of linux, so I am pretty lost with even basic commands.

The regular install and the "Start from safe graphics mode" both hang up right here:
[IMG]http://img.photobucket.com/albums/v499/hobostreet/DSCF1619.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v499/hobostreet/DSCF1617.jpg[/IMG]

Before this screen shows up and hangs, it is interspersed with three flashes of full black screen.

I tried pressing return and ctr-c as some suggested in other posts, but nothing happens.  The cursor lets me type, but I don't know any commands. :)

I selected the check cd for errors option and none were found.

My hardware is:
AMD Anthlon 64 X2 4000+ dual core
Abit An-M2HD mobo, which has the NVIDA 7050PV chipset
e-Geforce 6200  LE pci-e graphics card
2GB DDR2 Corsair xms2 ram
nsk2480 case
earthwatts ps
abit airpace wi-fi express card
logitech cordless mouse and keyboard
two 320 GB maxtor harddrives
and an asus dvd burner drive

I am trying to install this to be frontend and backend and functional desktop pc.

I have a s-video cable exporting the image from the 6200LE output to the s-video tv input.

Bios shows up fine.

If you can help, thanks in advance!

---

### Post by superm1 on 2007-12-04
Can you please connect it to a normal monitor and see if it boots correctly to that?

If not, then we'll have to ask for some logs.  The issue here is that the X server is not initializing properly with your video card.  (Has nothing to do with messages on the screen)

---

### Post by hoboghost on 2007-12-04
> **superm1 said:**
> Can you please connect it to a normal monitor and see if it boots correctly to that?

If not, then we'll have to ask for some logs.  The issue here is that the X server is not initializing properly with your video card.  (Has nothing to do with messages on the screen)

Thank you for the quick reply.  I tried installing with a regular lcd moniter and I got the same result.

Should I remove the video card for now?  

Ctr F1 lets me type in commands right?  How do I get a log with a command line?  I'll search the boards for an answer to that question :)

---

### Post by froy02 on 2007-12-04
Before installing try to check the cd to see if there is any error with your installation disk.

About 10 out of hundred dvd's that i use to burn iso images are bad or yours may just need cleaning.

---

### Post by hoboghost on 2007-12-04
> **froy02 said:**
> Before installing try to check the cd to see if there is any error with your installation disk.

About 10 out of hundred dvd's that i use to burn iso images are bad or yours may just need cleaning.

I used the "check cd for error" option on the install disk.  It did not find any errors.  Should I be checking it for errors another way?

---

### Post by feroxide on 2007-12-05
> **hoboghost said:**
> I used the "check cd for error" option on the install disk.  It did not find any errors.  Should I be checking it for errors another way?

Hi. If you are still having this issue, try getting to a prompt(alt-f1) and
do a STARTX. I have similar hardware and had the same problem.
After the installation is complete, it boots/hangs again. Repeat
the above step and setup the correct video driver and resolution. 
Reboot again and you should be rocking. :)
I think there is a problem with vesa driver and my onboard video.
Good luck!

---

### Post by uopjohnson on 2007-12-05
If you are going to be doing a full desktop install anyway you may want to consider installing from the standard ubuntu amd64 desktop install disk.  That would eliminate it being a mythbuntu specific problem.

---

### Post by feroxide on 2007-12-06
> **uopjohnson said:**
> If you are going to be doing a full desktop install anyway you may want to consider installing from the standard ubuntu amd64 desktop install disk.  That would eliminate it being a mythbuntu specific problem.

Hi,
Gave it a try, just to see if it would work. Same problem. Also, I don't see how it would be a 'mythbuntu' problem, because at the point where the problem occurs, it is a (x)ubuntu install procedure. Anyway, I am betting on the multiple video output options (vga, dvi, hdmi) causing this problem.  OP is got 2 video outs on the board, plus a pci-e graphics card. I have an ASUS M2A-VM HDMI, which has 3 different outputs, and does work with ubuntu/mythbuntu, but the installation issue is a p.i.a.
If anyone has a boot option that lets you coast through the install, please let us know.

---

### Post by uopjohnson on 2007-12-06
I didn't think it was a mythbuntu problem, that just proves it.  With all of those outputs I wonder if your x session is getting displayed somewhere else where you just can't see it.  You may want to try posting in the general install forum as the experts on this sort of issues are to be found there.  If you are familiar with xorg you may want to try editing your /etc/X11/xorg.conf file manually to get the right display working.  If you want to post this file I'm happy to take a look and see if I see the problem.

---

### Post by feroxide on 2007-12-06
> **uopjohnson said:**
> I didn't think it was a mythbuntu problem, that just proves it.  With all of those outputs I wonder if your x session is getting displayed somewhere else where you just can't see it.  You may want to try posting in the general install forum as the experts on this sort of issues are to be found there.  If you are familiar with xorg you may want to try editing your /etc/X11/xorg.conf file manually to get the right display working.  If you want to post this file I'm happy to take a look and see if I see the problem.

Hi,
The htpc is running fine, just needs a few more tweaks. I hope OP got everything working. You are right about getting this looked at in the install forums, because there is really no 'error' displayed, it just sits there. I'll take a look at install log and will post it in another forum.
ttyl

---

### Post by japius on 2007-12-07
Had the same issue over here. Picking the "safe graphics mode" boot-option fixed my problem.

Apparently, this install issue had to do with my graphics card not being recognized. I am installing on a Gigabyte GA 73pvm-s2h and I'm having a lot of troubles recognizing the hardware.

---

### Post by feroxide on 2007-12-07
Anyone having the install hang issue with the ubuntu64.iso, try updating your bios to latest version. The M2A-VM HDMI loads and works like a charm with the latest bios, ver. 1603 date. 2007/12/04. 
Happy TV watching to all. :)

---

### Post by hoboghost on 2007-12-08
> **feroxide said:**
> Hi,
The htpc is running fine, just needs a few more tweaks. I hope OP got everything working. You are right about getting this looked at in the install forums, because there is really no 'error' displayed, it just sits there. I'll take a look at install log and will post it in another forum.
ttyl



Thanks for the thoughtful replies.  A few days after I posted this, and before I got a chance to try some of your suggestions, I downloaded and tried to install linuxmce.  Not surprisingly, I couldn't get through that installation either.  

Right now I am trying a kubuntu 7.04 install.  I'm in the middle of a two hour long  memory test (looks ok, no errors).  

Thank you for the offer uojohnson, but I don't even know how to post a xorg.conf file :)

If I figure that out I will.  Thanks!

---

### Post by be4truth on 2007-12-08
Asus M2a-VM with Ubuntu 7.10 32bit

There are issues with this board:
First issue: When installing an error like this occurs 'cannot allocate resource region .....'
Solution: go into the BIOS and disable the HPET option. Use the 'Alternate Install CD 7.10'. Before installing pass the boot option 'acpi=off'. Make sure you floppy drive is either connected or disabled in the BIOS as the installation routine hangs looking for it.
After complete installation install the restricted ATI driver via restricted driver module. Resolution up to 1280x1024 is ok. Sound ok. Didn't had much time to test video. Will do soon.

---

### Post by hoboghost on 2007-12-08
aaaaaaaaaaaaaaaaaaaaaaaaaaaaah!!!!!! I am an Idiot!  I had to disable the onboard graphics in bios and I didn't know how to, but I finally figured it out.  I had to set "iGPU Frame Buffer Control" to "Manual" and select "Disable"---I can't believe how many hours I could have saved myself! good greif! haha.  Thanks for the help all.  I have gotten kubuntu 7.04 to load.  I am super excited!:guitar:

---

### Post by feroxide on 2007-12-09
> **hoboghost said:**
> aaaaaaaaaaaaaaaaaaaaaaaaaaaaah!!!!!! I am an Idiot!  I had to disable the onboard graphics in bios and I didn't know how to, but I finally figured it out.  I had to set "iGPU Frame Buffer Control" to "Manual" and select "Disable"---I can't believe how many hours I could have saved myself! good greif! haha.  Thanks for the help all.  I have gotten kubuntu 7.04 to load.  I am super excited!:guitar:

Hi, 
Someone should have noticed that. But then again, your bios options were not listed. I am not sure if the same is true for all motherboards with on board video, but my guess would be that onboard video/dedicated video card don't mix well, especially during install. Glad to hear you go it all sorted out. :)

Should this thread be label "solved" now?

---

### Post by elderpyre on 2007-12-25
Updated the BIOS on my AN-M2HD the other day, and couldn't get any flavor of Linux to boot. The new option looked so similar to the old one I didn't even stop to think I might have to set it to manual and set the shared RAM to disabled. Thanks for the info on that #-o

---

### Post by relja on 2008-03-29
I had same problem here. Tried Ubuntu 7.10 x64 and Mint 4.0. Both ended with same message on the screen and nothing more. But I have managed to solve this by this procedure:

Booted CD and started installation (default). 
When I get to the point when installation hangs, I switch to console (**Ctrl-Alt-F1**) and type following commands:
**sudo dpkg-reconfigure xserver-xorg**
This will reconfigure Gnome display manager configuration. It is important to use VESA graphic card and for the rest use default settings. You may change resolution and refresh rate, but only if you know supported settings for it.
After finishing configuration, you have to restart Gnome display manager by running: 
**sudo /etc/init.d/gdm restart**
**sudo /etc/init.d/gdm restart**
Note that I have run second command twice because i fails on the first hand, probably because it is still running in the background. After second gdm restart, Ubuntu should start GDM and soon you will get desktop screen. 
At least it worked for me, and I hope it will for you :)

---

