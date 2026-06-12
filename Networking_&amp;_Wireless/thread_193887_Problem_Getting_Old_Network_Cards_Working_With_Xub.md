---
title: "Problem Getting Old Network Cards Working With Xubuntu 6.06 Dapper"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by mtn on 2006-06-10
While installing Xubuntu 6.06 Dapper on an old P166 the install won't pick up either of the 2 network cards (not wireless) I have. I have Googled about and had a look in this forum but not turned up any thing. I'm wondering how I might solve this little problem. 

Technical info
Card 1: Compaq (printed on the board) TLAN (printed on chip)
Card 2: TCL
Router: Belkin Router
Internet access provided through cable modem by Telewest

I think I have a Windows driver somewhere for the Compaq card if this helps! 

During the install I am offered an option to provide driver on a floppy, I don't know where I might get these and don't really understand how Linux drivers work i.e. with windows it was some dlls or something. I don't know what Linux wants here!

Any help would be much appriciated.

[UPDATE]
I have spent hours searching about trying to figure it out. I finally found a link to Linux driver for one of the cards (Compaq TLAN Netflex 3) but the link was dead. I have tried the Debian install disks, Gentoo basic install CD and of course Ubuntu and Xubuntu and got no whrere. When I do ipconfig it is not there when I do ipgonfig eth0 it does show up but I guess it need configured. I don't know how to do this and so am going to admit defeat this time (this does not come naturally). Maybe I'll have another look in the future.

---

### Post by blx_286 on 2006-09-15
> **mtn said:**
> While installing Xubuntu 6.06 Dapper on an old P166 the install won't pick up either of the 2 network cards (not wireless) I have. I have Googled about and had a look in this forum but not turned up any thing. I'm wondering how I might solve this little problem. 

Technical info
Card 1: Compaq (printed on the board) TLAN (printed on chip)
Card 2: TCL
Router: Belkin Router
Internet access provided through cable modem by Telewest

I think I have a Windows driver somewhere for the Compaq card if this helps! 

During the install I am offered an option to provide driver on a floppy, I don't know where I might get these and don't really understand how Linux drivers work i.e. with windows it was some dlls or something. I don't know what Linux wants here!

Any help would be much appriciated.

[UPDATE]
I have spent hours searching about trying to figure it out. I finally found a link to Linux driver for one of the cards (Compaq TLAN Netflex 3) but the link was dead. I have tried the Debian install disks, Gentoo basic install CD and of course Ubuntu and Xubuntu and got no whrere. When I do ipconfig it is not there when I do ipgonfig eth0 it does show up but I guess it need configured. I don't know how to do this and so am going to admit defeat this time (this does not come naturally). Maybe I'll have another look in the future.


I have the same problem using an old Compaq Armada M700 laptop, which is a P2. I think I also found the same link, it was for the ftp site for Caldera. Did you ever find anything else on this?

---

### Post by blx_286 on 2006-09-15
I found this [www.tux.org/pub/tux/tlan/ link]("http://www.tux.org/pub/tux/tlan/") which may help. It's kinda old though.

I just plugged in an old 3COM 3C575-TX PC card and it fired right up. So I think I will run with that one.

---

