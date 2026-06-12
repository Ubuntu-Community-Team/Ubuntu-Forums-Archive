---
title: "Intel 82845 graphics, displays using only part of the screen"
date: 2014-05-06
forum: Multimedia Software
---

### Post by Doranwen on 2014-05-06
First of all, I should say that although I haven't used the current version of Ubuntu and this is my first time playing around with Lubuntu, I have fiddled with Ubuntu years back and I run Linux Mint on a daily basis so I'm comfortable with Linux, including the terminal (though don't have a ton of commands memorized).  I built the system I'm currently running, but I have more experienced people I go to when I get stumped on a problem--unfortunately one of them's unavailable and the other is swamped and has no time to help me figure out this issue, so I'm hoping someone here might know what to do.

So a friend asked me to put Linux on their old laptop--and I mean old.  This is a Dell Inspiron 1100, with 256 mb RAM and a 2.0 GHz processor.  You can see the specs on such a beast here:  [https://www.dell.com/downloads/emea/products/inspn/inspn_1100_uk.pdf](https://www.dell.com/downloads/emea/products/inspn/inspn_1100_uk.pdf)

It was running XP, and did so without problems (as long as you don't count slow as molasses in January a problem).  But given Microsoft isn't supporting it anymore, she didn't want to connect it to the 'net, so asked me to put Linux on.  I decided on Lubuntu pretty fast, realized that the regular install disk might be problematic with the amount of RAM, and went for the alternate installer for 14.04 (obviously 32-bit).  Given this, I had no way to test it live, but she had everything backed up, so I went ahead and tried installing.

My first sign of trouble was a line as the installer began about "Unidentified video mode".  It gave me about 8 or 10 options, all of which were some version of 640x480 or 800x600.  The first time I tried it I picked one of the 640x480s and it installed fine--but the display was reserved to about 3/5 of the entire screen, aligned to the upper left corner.  The laptop would properly support 1024x768 from my guess (I didn't even boot into XP so didn't see it), but it was using the 640x480 portion of it--not stretching it to the full screen at all (what was there was at proper size--it was just like someone scrunched everything into the smaller space on the screen but left everything the normal size).  The rest of the screen had really weird error-y colors, obviously not intentional.

One of my friends suggested trying the install with "nomodeset", so I did that, and this time it centered a 640x480 display in the middle of the screen (surrounded by black).  I'm at an utter loss on what to do--the OS does not recognize any resolution higher than this, and none of the video modes listed (which I can't remember now, it only appeared upon install) supported 1024x768.

Lspci gave this output:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

I ran across a site suggesting looking at vbeinfo in grub, and did so (took a pic with a webcam on a different computer), but not sure if that's relevant or not.  Graphics is one area I'm not very good at troubleshooting, I'm afraid!

Anyway, computer seems to work otherwise, connects to the 'net just fine and I've had no trouble with the terminal, browsing folders, etc.  Just slow, but that's to be expected (if I get this fixed, might invest in double the ram so it's at least semi-responsive).  But a display that tiny isn't going to work for my friend, so I need to figure out how to get it to recognize the entire screen properly.  Any suggestions?


**EDITED to add solution to first post in case you don't want to read all the way down:**  I just had to replace "nomodeset" with "i845.modeset=0" in grub, and it fills the full screen now!

---

### Post by ibjsb4 on 2014-05-06
> [COLOR=#000000]might invest in double the ram[/COLOR]

Half of gig is better, but still slow on things like ff and chrome browsers.

256 is imo not enough to work with.

---

### Post by Doranwen on 2014-05-06
Well, yeah--but the specs indicate that it won't take higher than 512 mb, so I'm probably stuck there.  Considering this lady has been using it at 256 mb on XP, she has patience with technology that I can only dream of, and would probably think 512 mb is delightfully fast, so I don't think it'll be a problem for her.  The tiny display, however, **will**.  So I really need to find a solution for that.

---

### Post by ibjsb4 on 2014-05-07
Here's some ideas.

[http://ubuntuforums.org/showthread.php?t=2222014](http://ubuntuforums.org/showthread.php?t=2222014)

---

### Post by Don_Tai on 2014-05-07
I find it interesting that Lubuntu can revive Dell dinosaurs! I recently (April 14 2014) loaded Lubuntu 14.04 onto a Dell Inspiron 6000, circa 2005 that had 500mb RAM, and while I had some issues with the wifi, that turned out to be my fault, it was a relatively easy install. The old Dell had a very tired and broken XP that was tormented by my 4yo nephew, who shorted out 2 of the 4 USB ports. With such low memory and no DVD I had to use the alternative i486 iso, burned to a CD. While a USB drive could boot the computer the Dell would only install from the CD.

To give your Dell biddy a fighting chance I recommend you do a couple of things. Firstly, download the alternative i486 Lubuntu iso and burn a CD. Then install from CD. 256 RAM will not run Lubuntu very well, but it will install. Upgrade the ram to the max 1G, which I looked up on Crucial.com. For web browsing and word processing your Dell laptop should run very well, not just Ok, but snappy. Your old Dell is circa 2003, only 2 years older than mine, so I have some confidence this will work.

My old Dell Inspiron 6000 has been running well. I upgraded the ram to the max 2G with a purchase from Ebay.ca. After I installed the "indicator-multi-load" applet I noticed that my ram usage usually goes to a max of 800mb and I have never exceeded 1G ram. I conclude that 1G of ram is sufficient and I overbought, wasting $7.50CAD. I am currently using Firefox with 10 tabs open, and the system is not only stable but quite fast. You can take a look at my [build notes]("http://dontai.com/wp/2014/04/25/lubuntu-14-04-lts-install-on-old-dell-laptop/"), where I document what lubuntu changes and addons I used. I document this because if I need to change my system in the future I can go back to my notes.

I have added a second monitor, so now I have a 2646x800 display. I have very stable wireless connectivity. I plugged in a couple of older web cams and they all work, right away. Apps I have installed and that work include: Skype, Opera, Midori, Filezilla, Sound and the mic work. Youtube videos work. I am using my laptop more for web browsing and the occassional light wordprocessing. The kids have tried some web-based games and they are very happy with the speed.

Add some memory from Ebay and with the help of Lubuntu 14.04 your laptop will transform itself back into a useful piece of modern computer hardware.

---

### Post by Doranwen on 2014-05-08
Lol, Don_Tai, I don't think you quite read what I said.  I already had installed Lubuntu from the alternate install--and have had display problems.  That's what I'm here to sort out.

ibjsb4:  Lol, I didn't have the right search parameters, apparently, had tried to look for help and got nothing useful.  Problem is, I've tried the xorg.conf they suggest--and I can't even get to a gui, have to switch to a terminal to delete the file and reboot in order to get a gui back.  Now, when I add the line about the vga mode in grub, it just boots into a black screen--with the white mouse cursor.  Before it booted the splash **did** fill the screen, though, which is new.  Any suggestions from there?

---

### Post by Paul_Slaughter on 2014-05-09
You can upgrade the memory on a Dell Inspiron 1100 to 1Gb with two 512Mb SODIMs. I have already done it. First you have to upgrade the Bios to A22. This file in available from Dell support. It is a DOS boot file so you will have to create a boot CD. Then you upgrade to Bios to A32 also available from Dell. This is has a Windows installer. Memory is still available from Crucial. I have installed Ubuntu 14 on mine and I am having the same video problems.

---

### Post by Doranwen on 2014-05-11
Unless the display issue  is solved, there no point in spending money on RAM and all of that.  If  I can't solve the display issue, the laptop is really unusable for its owner (which is not me), no matter how  fast it is.  I'll look into upgrading the RAM **only after** the display fills the entire screen.

---

### Post by mörgæs on 2014-05-11
You could try VESA graphics. See the link in my signature for more details.

---

### Post by Doranwen on 2014-05-11
I've tried booting with various vga lines (adding them at the end of the line in the main boot window for grub that starts with "linux")--it just boots to a black screen with a white mouse pointer (I can move it all around, but there's nothing to click on).  Ctrl+Alt+F1 will get me to cli from that, but it never boots me to a gui with any of those modes added.  If there's a different way to add the mode that will work better for testing, I don't know it.

---

### Post by mörgæs on 2014-05-13
You could try booting into recovery mode and / or the xorg.conf described here:
[http://ubuntuforums.org/showthread.php?t=2223134](http://ubuntuforums.org/showthread.php?t=2223134)

---

### Post by squakie on 2014-05-13
This appears to have been an on-going issue dealing with the 845.  It never has been very good with Ubuntu.  I found an older thread dealing with Mint (Mint is actually Ubuntu with a different desktop manager).  You may want to look into what it says.

In the mean time, instead of nomodeset, I'd try i915.modeset=1 and if that doesn't work then try i915.modeset=0.

This all has to do with the 845 and getting it set up correctly.  I went through this once years ago and unfortunately don't remember what I did to get it to work.  I'll keep looking.  

In the mean time, here's the link: [http://forums.linuxmint.com/viewtopic.php?f=175&t=83767](http://forums.linuxmint.com/viewtopic.php?f=175&t=83767)

---

### Post by Doranwen on 2014-05-14
Aha!!!!!  You said i915 but the thread you linked pointed out that the person had i845 (as do I--the i915 was what the original user had who had tried the modeset to fix the card)--so after I tried both i915 versions (first one displayed in upper left as before, 2nd wouldn't display anything but garbled colors), I went on a hunch and tried the i845 versions. Trying "i845.modeset=1" got the usual upper left, BUT . . . "i845.modeset=0" filled the **full screen**!!!!!!  I am overjoyed.  Proper 1024x768 display, they might be able to use this yet . . .

Now, how do I get that to be set that way ALL the time so the user won't have to do the complicated grub command-line edit?

I may end working on updating that BIOS and upgrading the RAM after all--this laptop has some life left in it yet! :D

---

### Post by mörgæs on 2014-05-14
Congratulations. Please see the bottom of the page:
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) (you might need to replace gedit with leafpad or textpad).

---

### Post by Doranwen on 2014-05-14
Done, and thanks so much all who tried to help--especially thanks for that link, squakie, was just what I needed. :D

---

### Post by squakie on 2014-05-14
You're welcome - I'm just glad you got things working!  And guess what - if someone else has this problem in the future and doesn't see this thread you can pay it forward by answering it for them!

Great job!  ;) ;)

---

### Post by gregd2 on 2014-10-19
I want to get started with a "non windows" operating system.  I have the exact same dell inspiron 1100 with the 845gl chipset that is used in this post and I have installed Lubuntu on it.  I put in exactly what this user put in and this has sent me back to the black screen that I had before I changed to i915 mode and got the small screen.  I have a little more ram, but otherwise the same computer.  Why would it fix this users problem and the exact same thing won't fix my problem.  If I do this it actually gets worse.  Am I missing something?

I'll summarize in case that isn't clear:

Installed Lubuntu - booted to black screen
Changed settings to i915.modeset=0 - got small screen to show up in center of display with no way to change resolution
Changed to i845.modeset=0 - went back to booting to black screen

Any help is appreciated.

---

### Post by gregd2 on 2014-10-19
Update:
I changed it to xforcevesa and now I have full screen.  I don't know if there is another setting that might make it work better, or why i845.modeset=0 didn't work for me, but at least it works now.

---

### Post by alma3 on 2015-01-31
> **gregd2 said:**
> Update:
I changed it to xforcevesa and now I have full screen.  I don't know if there is another setting that might make it work better, or why i845.modeset=0 didn't work for me, but at least it works now.


I'm having the same problem. I installed Lubuntu and I have a small screen on left corner, ghost on bottom and black screen on right. I need help on how to fix this common problem as I am a new to Linux. Thank you.

---

### Post by mörgæs on 2015-01-31
Please post the output of ```
sudo lshw -C video
``` in CODE tags.

---

