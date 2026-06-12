---
title: "ASUS N13 USB Wireless Adapter and Ubuntu 9.10?"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by ken0069 on 2010-11-21
Ok so I've been reading in several posts here about this wireless adapter and the more I read, the more confused I get.  That and I finally broke the original 9.10 load and I'm now here with a fresh re-install looking for help related ONLY TO 9.10 and this ASUS N13 USB Wireless Adapter.  Previous posts started on 9.10 then skipped forward to 10.04 and as I said, next thing I knew my system was broke!!

Maybe one of you that has one of these running on 9.10 could point me in the right direction that won't break this and help me get connected to my wireless network.

Some background:  This computer is a multiboot system that is on a LAN with three other computers.  On this computer I boot Windows XP, Windows Vista, Windows 7 and Ubuntu 9.10 and the wired part LAN works.  This ASUS USB adapter works fine in all the Windows systems so I know there's not a problem with the device itself.  

Please note that I haven't done ANYTHING to try to install this device yet and just finished 277 MB of updates on this clean install.

My network is controlled by a Cradlepoint MBR-1000 N wireless router that uses a USB Datacard for internet service.  

Thanks,

Ken

---

### Post by Hippytaff on 2010-11-21
have you tried usb-modeswitch?
[http://manpages.ubuntu.com/manpages/karmic/en/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/usb_modeswitch.1.html)

---

### Post by ken0069 on 2010-11-22
No I haven't and from what I just read on that site, it doesn't seem to apply here as there are NO onboard drivers in this device?  I had to either load drivers from the CD in Windows or connect to Micro$oft for drivers to make it work.  From what I can see, Ubuntu doesn't even know it's plugged in?

This adapter is not for direct connection to a WAN, it is a simple LAN connection for a my computer on my network here at home.

---

### Post by Hippytaff on 2010-11-22
Ok, then you might need to install the xp driver with ndiswrapper or find a linux driver (if there is one) and install it with modprobe.

---

### Post by ken0069 on 2010-11-23
OK so you've got to understand that I'm not a command line person.  In Windows even my only command line knowledge is format C: /u and that's it.  

The only reason I use Ubuntu is for the security as I've had some of my websites hacked by low life scum that managed to install a keylogger on my Windows box from a fake antivirus malware program.  I don't want to learn programming as I have many other interests that require my free time.  Linux is only a tool to me, not a hobby and I only want to know what is necessary to make it work.  As I said in my original post, the other threads on this N13 USB adapter went in several directions in the same thread and I got lost in the process and horked up the previous install, which had been on here for about a year.  

So having said all that, if you can give me some working instructions and the terminal stuff I need to make this work then fine.  If I need to upgrade to 10.10 then that's an option if it makes it easier to get the help I need.  If there's no help then I'll just scrap it move on to something else, maybe a Mac.  

?

---

### Post by Hippytaff on 2010-11-23
Sorry, I should have mentioned that there is a gui front end to ndiswrapper called ndisgtk :-)

Ubuntu caters for both those that like command line and those that prefer the gui - if you need help with anything this forum is great, but people like me tend to miss the point sometimes :-) bear with me

---

### Post by ken0069 on 2010-11-24
> **Hippytaff said:**
> Sorry, I should have mentioned that there is a gui front end to ndiswrapper called ndisgtk :-)

Ubuntu caters for both those that like command line and those that prefer the gui - if you need help with anything this forum is great, but people like me tend to miss the point sometimes :-) bear with me

No problem Bubba!  Probably be a good idea to wait until after the holiday now though but one question first.  Do I need to load 10.10 for this, ie, will it make this any easier?

---

### Post by Hippytaff on 2010-11-24
I'm not sure, but it might me a good ides to instal 10.04 as it is an LTS release (Long Term Support) and the driver might be avialble as part of the build but it's something that would need to be looked into. Happy Holidays :-)

---

### Post by ken0069 on 2010-11-26
After going round and round trying to get this adapter to work and horking up the previous software load in the process, I decided to try 10.10 this afternoon to see if it would be any easier to make it work with Meerkat.  

Good news and bad news in Mudville today!  After loading 10.10 on a spare hard drive, I did get this ASUS N13 USB wireless adapter to connect after all the Meerkat updates were done.  So seems that the "powers that be" have seen this PITA adapter is a problem for many so they fixed it with an update.  

So while I've still got two puters with 9.10 on'em, at least now I do know that 10.10 will support that N13 now.  Be real nice if someone would "fix" the 9.10 problem though as I really don't want to have to reload the other two just for that.

---

### Post by Hippytaff on 2010-11-26
How annoying :-)

if you can mark the thread as solved others will benefit from your discovery :-D

---

### Post by ken0069 on 2010-11-26
Well, IMHO it's not actually "solved" as wireless is only connecting at 54G?  I bought a Draft N device because I wanted the 300 speed for file transfers.  The wired 10/100 is faster than that??  :shock:

So is there a fix for that? ](*,)

---

### Post by ken0069 on 2010-11-28
Bump?

---

