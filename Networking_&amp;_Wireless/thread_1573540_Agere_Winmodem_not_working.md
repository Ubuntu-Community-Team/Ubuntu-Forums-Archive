---
title: "Agere Winmodem not working"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by Microsoft Hater on 2010-09-12
Anyone been able to fix an Agere Winmodem problem? 

I've followed the ubuntu modem faq (which, honestly SHOULD be more user-friendly than it is) and tried the martian installation too (which *also *should be more user-friendly). 
 
So I still have dial-up because I'm not in an area that will let me have anytihgn else, and all forum posts that I've found, and installation suggestions I've found haven't worked.
 
Please help with this - It really shouldn't be this much of an issue.

---

### Post by peyre on 2010-11-05
> **Microsoft Hater said:**
> Anyone been able to fix an Agere Winmodem problem? 

I've followed the ubuntu modem faq (which, honestly SHOULD be more user-friendly than it is) and tried the martian installation too (which *also *should be more user-friendly). 
 
So I still have dial-up because I'm not in an area that will let me have anytihgn else, and all forum posts that I've found, and installation suggestions I've found haven't worked.
 
Please help with this - It really shouldn't be this much of an issue.
I'm having the same issue!  I'm breathing life back into an old Tecra 8100, and come to find out its modem is an Agere Winmodem.  Damn!  When I'm on the road I sometimes need dial-up: a lot of my relatives don't have high-speed Internet, and with dial-up I can at least check my email when I'm out of town.

---

### Post by peyre on 2010-11-05
Oh wow!  Hey, I got mine to work.  I don't know exactly how I did it, but it now recognizes the modem.  (I'll test actually dialing up over the weekend.)

I did a whole bunch of stuff to get it to work, and I'm not sure exactly what I did and exactly what was necessary and what wasn't.  But here's what I know of what I did.

This was in Lubuntu 10.04.

I installed KPPP, martian-modem, and martian-modem-source.  martian is a LinModem project designed to support Agere Winmodems.

I also installed gnome-ppp, but it was useless on my system: it kept hanging when I tried to detect the modem.  I eventually removed it altogether.

**Here's the confusing part in the middle, where I'm not sure exactly what I did, but here's my best recollection:**
1. I ran sudo martian_modem, which I think started martian running.
2. At one point I ran sudo m-a a-i martian-modem and sudo m-a -f get martian-modem, which I think told me what device the modem was assigned to: /dev/ttySM0.
3. At another point I ran sudo apt-get update and sudo apt-get -s install linux-kernel-devel.
4. At yet another point I ran sudo apt-get install module-assistant.

At the end, I installed hwinfo, which I think installs the Hardware Drivers utility (installed on Ubuntu and Xubuntu by default) that controls third-party and proprietary drivers.  When I ran that utility, I saw my modem in there and active, as the Agere 164x dsp driver.

KPPP doesn't have an option for /dev/ttySM0, so I then linked it to /dev/modem:
  sudo ln -s /dev/ttySM0 /dev/modem

I was now able to select /dev/modem and get KPPP to recognize it.  Woohoo!

NOTE:  That command, sudo ln -s /dev/ttySM0 /dev/modem, doesn't stick when you close down your computer.  Next time you boot up and want to use the modem, you have to run it again.  I wrote that up in a text file on my Desktop so I wouldn't have to search for it next time.

---

