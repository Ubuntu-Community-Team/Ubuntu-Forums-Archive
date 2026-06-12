---
title: "Rockwell Riptide Combo Card"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by Gardiner Westbound on 2006-07-13
I'm trying to get the sound working on Ubuntu Dapper on an old HP Pavilion 6460 with a Rockwell Riptide Combo sound and modem card. I found a couple of drivers that claim they might work but I am stymied how to install one or the other of them.

The first is named [COLOR="Blue"]riptide-0.6lnnxtbeta03122800.tar.gz[/COLOR] and the second [COLOR="Blue"]riptide-0.6lnxtbeta03122800-1.i386.rpm.zip[/COLOR]. There is also an installer named [COLOR="Blue"]cnxtinstall.run[/COLOR] but when I try to run it I get an error message saying it could not open the file. I am leaning toward trying the [COLOR="Blue"]riptide-0.6lnnxtbeta03122800.tar.gz[/COLOR] driver first. Any help will be appreciated.

I also have a Windows driver [COLOR="Blue"]rip417na.exe[/COLOR] for the card. Will it work in Ubuntu? I got a Windows driver to work for my Linksys WLAN adapter by using ndiswrapper. Is there a similar workaround for other Windows drivers?

Thanks

---

### Post by az on 2006-07-13
Conexant Riptide support has been dropped by Linuxant (the company who was given the priviledge of producing proprietary drivers for the hardware)  This would not have happened if they were free-libre open source, of course.

You are out of luck.

---

### Post by Gardiner Westbound on 2006-07-13
> **azz said:**
> Conexant Riptide support has been dropped by Linuxant (the company who was given the priviledge of producing proprietary drivers for the hardware)  This would not have happened if they were free-libre open source, of course.

You are out of luck.
Thanks for your reply. If a driver works is apparently dependant on the kernel and, perhaps, the phases of the moon. It can't hurt to install one and see what happens. I would like to start with [COLOR="Blue"]riptide-0.6lnnxtbeta03122800.tar.gz [/COLOR], but can't figure out how.

---

### Post by az on 2006-07-13
> **Gardiner Westbound said:**
> Thanks for your reply. If a driver works is apparently dependant on the kernel and, perhaps, the phases of the moon. It can't hurt to install one and see what happens. I would like to start with [COLOR="Blue"]riptide-0.6lnnxtbeta03122800.tar.gz [/COLOR], but can't figure out how.

I think it is only for 2.4 kernels.  Maybe it will work with Debian Woody?

---

### Post by FactTech on 2007-03-10
For anyone stumbling across this thread, FYI -- support for the Rockwell Riptide Audio PCI hardware seems to be built-in to v6.10 (Edgy Eft). It worked out-of-the-box after install for me.

There appears to be lingering support issues for the ALSA architecture (as of today this hardware is not listed as supported on their site), but the ESD and OSS subsystems have no problems with it.

---

### Post by irw on 2007-04-17
Support for the audio is built into Edgy, but not the modem; if you install the modem driver it kills the audio ...

---

