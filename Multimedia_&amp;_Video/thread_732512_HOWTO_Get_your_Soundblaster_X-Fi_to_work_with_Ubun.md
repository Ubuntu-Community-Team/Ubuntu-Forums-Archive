---
title: "HOWTO: Get your Soundblaster X-Fi to work with Ubuntu"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by Lazy8s on 2008-03-23
This tutorial will show how X-Fi users can get sound out of their sound cards. I wrote this as a thank-you for this forum pointing me in the right direction. This is a very basic step-by-step instruction. Write this down or (preferably) print this out. In order for you to have reasonable expectations let me make this disclaimer:

What this will do: Make sound work with your X-Fi card.

What this won't do: Make anything else work including but not limited to your microphone and any card acessories. (like the front panel, etc)

**Step 1**
Go to [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) and download the "Lunix 2.6 (x86) (TAR) file. Save this to your desktop. (important later on)

**Step 2**
Press Crtl+Alt+F1 to open a full-screen terminal. Type in your login name and password.

**Step 3**
type 
> 
cd Desktop


**Step 4**
type
> 
sudo su

Enter your password if prompted.

**Step 5**
type
> 
cp oss-linux-v4.0-1014-i386/tar.bz2 /

Note: the name of the file may have changed since I wrote this tutorial, be certain to type in the name of the file you downloaded.

**Step 6**
type
> 
cd /


**Step 7**
type
> 
tar -jxvf oss-linux-v4.0-1014-i386.tar.bz2


**Step 8**
type
> 
sh /usr/lib/oss/build/install.sh


**Step 9**
press Ctrl+Alt+F7

**Step 10**
Reboot your system and voila the sound should work!!

(Optional)
**Step 11**
Hit Ctrl+Alt+F1, login and type
> 
osstest


exit by pressing ctrl+alt+F7

---

### Post by hashi856 on 2008-04-04
I followed the instructions exactly and still nothing. Everything that was supposed to happen in the terminal, happened, but when I restarted my computer, still no sound. Is there any other method?

---

### Post by Plasmodium on 2008-04-11
I've gotten my X-Fi to work with the latest OSS drivers in AMD64 Ubuntu 7.10 and now the 8.04B. Following this [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60) , I've also got full control over the volume settings. The OSS soundtest and System/Preferences/Sound test all give sound (except the Tab where you can test the specific event-sounds)

A few problems remain, and I was wondering if anybody had a solution:
1) Still no system sounds (like at log-on or log-off), your hear a click of the soundcard switching on and then a click while it switches of, but no real sound. This click is also present when using a program that does deliver sound, like Totem. I have dual boot with WinXP, and here everything works perfectly, so this click is not a hardware issue.
2) Music plays fine in Totem Mediaplayer but not in Rhythmbox. In Rhythmbox the sound is very loud and all distorted. Also no sound in Flash movies in Firefox.
3) General low quality sound compared to normal X-Fi operation.

All these things are probably issues with the OSS (Beta) drivers? Has anyone here been able to use the drivers that Creative provided? I've tried to install those in Suse, Debian and Ubuntu without any luck. Even tried to recompile my kernel with SLAB allocator as has been suggested, but no joy. Anyone have the ultimate tip for getting it to work?

greetz

---

### Post by WoosterB on 2008-04-11
I can't get systems sound either and I can only run VLC media player.

BUT I can help with the firefox issue.

First, try some of these tips to see if it works:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

If that doesn't work, I posted a link towards the back end of that thread:
[http://sendderek.wordpress.com/2007/...firefox-flash/](http://sendderek.wordpress.com/2007/...firefox-flash/)

This has a libsupport file that you can download and (since it is .deb) you can install.  
I found this worked for me and my X-Fi HOWEVER the sound is a second behind the video.  I am currently searching for a solution to this.

-W

---

### Post by neurostu on 2008-04-11
What happens if you remove the card from your computer, will the built in speakers then take over or does installing the X-fi card remove the functionality of the built in speakers?

---

### Post by Plasmodium on 2008-04-14
This story just got a funny twist: when upgrading through the upgrade manager to kernel 2.6.24-16 (had -15 previously), all sound dissapeared. In the sound configuration panel OSS isn't even an option anymore, it's all gone. Uninstalling and re-installing OSS didn't help. For uninstalling I followed the guidelines from the 4Front forum, which had helped me before. 
Frankly, I'm at a loss at what to do next. Any ideas?

greetz

---

### Post by WoosterB on 2008-04-14
Yeah, I can't get OSS in those places either, although the sound in apps works great.

After looking around I think the OSS guys had a partial solution to the issue and were able to get something out of the architecture despite only a 50-75% success.  From what I've read, Creative is keeping mum about any possible drivers for 32-bit and won't hand over any information to the ALSA guys.  

I'm not big on system sounds anyway so it was no problem to me.  Just keep a weather eye open and see what happens.

-W

---

