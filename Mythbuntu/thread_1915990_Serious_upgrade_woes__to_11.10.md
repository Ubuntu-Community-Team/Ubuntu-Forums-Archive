---
title: "Serious upgrade woes  to 11.10"
date: 2012-01-27
forum: Mythbuntu
---

### Post by Meph1st0 on 2012-01-27
This is half rant / half plea for help.  (Seriously, I'm on my hands and knees in suplication here)  I've been trying to upgrade my system to 11.10 for about a month and a half now.  I'm onto my third video card and still can't get it to upgrade properly.  I've gone through two Nvidia cards and one ATI card.  I've tried every trick or tweak that I've been able to find on the interwebs with no success.  I'm now beginning to question whether it's my video card at all.

I was on 10.10 when I started.  Chose to do a clean install of 11.10 since I couldn't upgrade directly to 11.10 from 10.10.  I know it begs the question, "why upgrade a working machine?" but it's too late for that now, the computer is hosed.  Long story short, it's been a nightmare.  Seriously, I've given up and then tried again several times now.  I've tried a few different distributions now too with no success.  The closest I got to a working system was with the ATI card but there were issues with that too.  I'm extremely close to switching to Windows.  I know...them's fightin' words.

Okay, so there's my rant.  Now here's my plea for help.  Be aware that I've kind of been out of the linux game for a while now, so I'm a little bit behind on the major changes.  (Also, I'm at work writing this so I can't gather any logs or anything yet)

I'm now using an Nvidia GT520 made by Asus.  From what I'm reading online this card should work out of the box, but it won't for me.  It'll boot up but it won't load any graphical environment.  Has Mythbuntu gone away from xfce? or is it now using lightdm/unity by default?  Using the -nomodeset switch in grub doesn't fix it.  Booting in recovery mode doesn't work either.  I can hit Ctl-Alt-F1 and get a prompt but I don't know what to do from that point forth.  Jockey-text --list shows that I'm using Nvidia-current drivers.

The Mythbuntu installation process appears to work fine.  I don't have to use any bootup switches to get to the graphical installation.  Once it's installed though it doesn't load a window manager.  It appears to just stop in the middle of it's boot process but I know it's just supposed to be showing the desktop at that point.

I need some serious help from the linux comunity here.  Let me know what logs you need to see.  I'm out of ideas.  Like I said, I've been trying for a month and a half to get a working system and tried to find the solution on my own.  I'm to the point where I need a third party to help me out.  I'm to the point now where I'm so fed up with my computer that if it doesn't work right out of the box I want to just toss the computer out the window.  I'm completely burned out on troubleshooting this problem on my own.

I've even gone through [this]("http://ubuntuforums.org/showthread.php?t=1743535") sticky with no luck.

Thank you to anyone with suggestions.

---

### Post by Meph1st0 on 2012-01-27
I know you probably want some additional details about the machine but I'll have to post them when I get home from work.  This I can tell you:

Intel Pentium E2180 Allendale 2.0GHz 1MB L2 Cache LGA 775 65W Dual-Core Processor 
ASRock 4CoreDual-SATA2 LGA 775 VIA PT880 Pro/PT880 Ultra ATX Intel Motherboard 
2 GB of RAM (Memtest86 passed)
Zalman HD135 Case
PCHDTV 5500 TV Tuner
Hauppauge 1600 TV Tuner
NVIDIA GT520 video card
1TB Western Digital Hard Drive
No name brand DVD drive

Plugged into a Sony Bravia 46" LCD via HDMI.

Let me know if you'd like to know anything more.

---

### Post by nickrout on 2012-01-27
The xorg log is /var/log/Xorg.0.log

---

### Post by Meph1st0 on 2012-01-30
Thanks Nickrout, that little push was enough for me to get on the right trail.  I was able to look in the log and find out in the end that I needed to update my grub startup command to include vmalloc=256M

It was conflicting with the Hauppauge HVR 1600 during bootup.

---

