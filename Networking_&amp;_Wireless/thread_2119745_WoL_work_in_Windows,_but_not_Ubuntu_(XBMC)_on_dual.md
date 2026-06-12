---
title: "WoL work in Windows, but not Ubuntu (XBMC) on dual-boot machine."
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by drmichael on 2013-02-24
I can't wrap my head around why wake on lan works when I boot into and shut down from Windows, but not XBMC Ubuntu.  Any ideas?  I've tried nearly everything that I can think of/search for.  I have a Realtek NIC if that helps (RTL8101/8102).

---

### Post by UltimateCat on 2013-02-24
I'm far from the expert on this but you may need the driver for you card.
Try installing the driver and re-start your computer.

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#)

How to install
[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)

XBMC Help 
iki.xbmc.org/index.php?title=Settings/Services
[http://forum.xbmc.org/showthread.php?tid=129417](http://forum.xbmc.org/showthread.php?tid=129417)


Hope this helps

---

### Post by drmichael on 2013-02-24
Unfortunately, that driver didn't help.  Using lshw | grep r8 shows that it's using the correct, new driver, but WoL still doesn't work, even after restarting.

---

### Post by ahallubuntu on 2013-02-24
~

---

### Post by drmichael on 2013-02-24
> **ahallubuntu said:**
> Can you clarify how you are waking the computer up?  How are you sending magic packets?

I've tried a couple of different methods: sending packets from my other Windows machine using various WoL applications and using my XBMC remote on my Android phone.  All of them work for Windows.  None of them for XBMCbuntu.

> 
Try reading this:

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

and see whether WOL is enabled in Ubuntu.

Unfortunately, I've done all of that.  As for the "Troubleshooting" section, my LAN light is on and definitely blinks when I send packets to it.  There's just something in XBMCbuntu that isn't triggering.

---

### Post by miegiel on 2013-02-25
Maybe I shouldn't butt in, but in your 1st post you said you shutdown the PC.

AFAIK WoL only wakes from [sleep]("http://en.wikipedia.org/wiki/Sleep_mode") (also called [S3 or suspend to RAM]("http://en.wikipedia.org/wiki/Suspend_to_RAM#Power_states")).

---

### Post by drmichael on 2013-02-25
> **miegiel said:**
> Maybe I shouldn't butt in, but in your 1st post you said you shutdown the PC.

AFAIK WoL only wakes from [sleep]("http://en.wikipedia.org/wiki/Sleep_mode") (also called [S3 or suspend to RAM]("http://en.wikipedia.org/wiki/Suspend_to_RAM#Power_states")).

It works from shutdown if I shut down from Windows.  Doesn't seem to work with XBMCbuntu, though.

---

