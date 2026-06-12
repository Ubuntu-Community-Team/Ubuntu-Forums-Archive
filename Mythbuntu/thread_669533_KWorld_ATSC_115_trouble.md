---
title: "KWorld ATSC 115 trouble"
date: 2008-01-16
forum: Mythbuntu
---

### Post by jay3712 on 2008-01-16
Hello everyone,
I just got a KWorld 115 so I can watch OTA HD in Myth.
I already have a Hauppauge PVR 500 for cable tv, and it works perfectly.
So I figured I could pick up the local HD channels with this card. At first it wasn't recognized, but then I upgraded my kernel to 2.6.24 and the card is recognized as kworld atsc 110/115, but it's not picking up any signals. 
In the capture card setup, what card type is this supposed to be?
Can anyone help me? I searched but all of the posts seem to deal with installing firmware to get the card to be recognized. I have loaded the nxt2004 firmware into /lib/firmware/2.6.24-4-generic.
Thanks for your help,
Jason

---

### Post by jay3712 on 2008-01-17
Anyone? Anyone? Bueller? Bueller?

---

### Post by volkswagner on 2008-01-19
Look in here


[http://ubuntuforums.org/showthread.php?t=645730&highlight=kworld]("http://ubuntuforums.org/showthread.php?t=645730&highlight=kworld")

You may also need to follow these instructions to fool the system it is a 110 card

[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110]("http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110")

> 4.1 If you are using a KWorld ATSC 115, you need to force proper recognition by adding the following lines to /etc/modprobe.conf. (card=90 forces it to be treated just like an ATSC 110)

Hope this helps

---

### Post by newlinux on 2008-01-19
IT should be setup as a DVB card if you want QAM or ATSC OTA channels. What scan settings are you using? Also, have you tried using the other input on the card?

---

### Post by Rhiadon on 2008-01-20
Also make sure you have the firmware placed in the correct location. I don;t remember the location off the top of my head but I had this problem. Myth would recognize the card because I had loaded the correct module but dmesg showed an error that I never caught. When I'd scan for channels it woudl never find anything saying "no tables". If you are gettgin this then try the firmware. If not, then I'm sorry for wasting bits. :)

---

### Post by stefanst on 2008-01-21
I just had the same problem with the Kworld ATSC 115. So I put it into an older computer and it picked up lots of channels! The only difference was that I was running the I386 Kernel (also 2.6.24) on the older machine- a Pentium III and I am running the AMD64 Kernel on the newer machine. Something goes wrong with the tuning on the 2.6.24 AMD kernel. When I switched back to the 2.6.22 Kernel and added all the modlines, it also tuned fine on the AMD machine. I also put the card into my wifes AMD64 computer and it showed the same behavior. 
So, if you are using the AMD64 kernel you have two options: downgrade back to the 2.6.22, or install the I386 kernel. Of course don't forget to copy the firmware into the 2.6.22 directory if you go this route!

Good luck!

Stefan

---

### Post by jay3712 on 2008-01-25
Ok I'm close. I can tune a couple of channels, but the audio and video are really choppy (sometimes). Is my computer too slow?
I got firmware dvb-fe-nxt2004.fw in /lib/firmware/2.6.24-4-generic
I'm using an old P4 2.6ghz i think, radeon 9000, 1gb ram, 120gb hdd, pvr-500 and kworld 115.
The card type is "Nextwave nxt200x vxb/qam"
Signal strengths are all above 90%, s/n are all 4.6-4.8 db.

---

### Post by newlinux on 2008-01-25
That's borderline for HD, especially with an ATI card. Are you using the proprietary drivers. What is your CPU usage when you are viewing the channels? I have a P4 2.6 Hyperthreading with a nvidia card and nvidia binaries that can do 720p without XvMC, but only if I'm basically not running anything else that takes up CPU cycles.

---

### Post by jay3712 on 2008-01-26
Thanks for the replies fellas.
Well that is not good news. I'm pretty sure I'm using restricted drivers, is that the same thing as proprietary drivers? 
How do I check CPU usage while I am watching (or trying to watch) tv?
I confirmed it is a p4 2.66 HT.  From what I read in the wiki ATI drivers don't support XvMC.
This is a dedicated mythbuntu box, so there is nothing else going on while I am watching TV.
What should I do?
Thanks again,
Jason

---

### Post by newlinux on 2008-01-26
That is correct, ATI doesn't support XvMC, and restricted drivers are the same as teh proprietary drivers.

I like to use htop for process/CPU monitoring:
```

sudo apt-get install htop

```

then you can run htop from a terminal while you are running mythfrontend to watch something in hidef. Or you can ssh into your box from another machine and run htop. Are all the channels you can tune hidef? do you have problems with non-hidef digital channels?

Also, what are you TV playback settings? sometimes playing with those can reduce CPU usage...

---

### Post by thecoolcat on 2008-01-26
I'm pretty sure you are maxing out on the CPU/graphics card.

For me, if my PC is loaded, the HD viewing is choppy on video/audio. However, when I change the channel to SD resolution, it is perfect. (Few of the channels in my local area are offered in both digital SD and HD resolutions.)

---

### Post by jay3712 on 2008-01-26
Yep, it's pegged at 100% cpu usage when I'm watching HD, and about 30% when watching SD. All of the settings are the defaults and I'm not running anything besides myth.
So I'm pretty much sol, right? I guess I sould go ahead and pull the trigger on a new build from Newegg.
Thanks

---

### Post by newlinux on 2008-01-26
You can still try playing with the playback settings (deinterlace settings, mpeg 2 encoder, etc.) as I suggested. different combinations *can* make a big difference. I've pretty much got the same CPU (different video card, which probably helps). I can run it in Gnome with full desktop, but not consistently with other apps running (I can have some lower resource using apps running).

---

### Post by jay3712 on 2008-01-27
Would it be worth it to try say an nvidia 7600 could fix my problems? what vid card do you have newliux? I only use my myth box to watch and record tv, so I really don't need it to do anything else. Or should I just return the Kworld 115 and watch SD?
Thanks again this has been really helpful.

---

### Post by newlinux on 2008-01-27
In my P4 I have an old Geforce 440MX. If I were you I'd get an inexpensive nvidia 5 series card. They can use XvMC which can reduce your CPU load. But just having a nvidia card with nvidia binaries (which work better than ATI) will help. You could also get a 6 or 7 series, but they won't really give you any advantages in Linux. Don't get an 8 series. You don't need much vid card horsepower since the CPU will do most, it is just that in general nvidia cards perform better in linux with the proprietary drivers (for now).

You can watch analog SD on the Kworld. It is an NTSC tuner as well. If you just want to watch analog with it you can set it up as a V4L card. Or you can use it for both:

[http://ubuntuforums.org/showthread.php?t=643415](http://ubuntuforums.org/showthread.php?t=643415)
[http://ubuntuforums.org/showthread.php?t=678956](http://ubuntuforums.org/showthread.php?t=678956)

---

