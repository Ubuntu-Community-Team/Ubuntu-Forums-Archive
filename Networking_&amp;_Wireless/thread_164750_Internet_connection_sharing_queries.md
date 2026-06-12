---
title: "Internet connection sharing queries"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by xen on 2006-04-23
Hey folks, first up I may aswell introduce myself a little. This is my second Ubuntu experience (the first time was a largely unsuccessful experience with Hoary Hedgehog on my desktop PC), but this time I have breezy running nicely on my Vaio laptop (no problems so far!). 

This sure is a great community!

Anyway, I use this Ubuntu powered laptop for all my school work etc, I try and keep games etc of here so that I can work well, and all my music and other files are kept on my desktop PC.

The desktop PC is connected wirelessly to a wireless router/modem combo, a couple of rooms away. What I want to be able to do is to plug my Ubuntu laptop into my desktop PC (using a ethernet crossover cable) when I return home from work/school and share the the internet connection and access files from the PC.

Networking has never been my strong point, so really i'm not sure where to start. (Note that I do not want to use a wireless adapter with my laptop).

---

### Post by mips on 2006-04-23
Uhm, is the desktop running Ubuntu or Windows ? (You said it was unsucessfull so I'm not sure.

Either way you need to enable Internet Connection Sharing. I do not know how to do this in windows but in Ubuntu simply install Firestarter on the gateway PC and configure it.

There are many guides for ICS here, both on Ubuntu & win.

---

### Post by xen on 2006-04-23
[QUOTE=mips]Uhm, is the desktop running Ubuntu or Windows ? (You said it was unsucessfull so I'm not sure.

Either way you need to enable Internet Connection Sharing. I do not know how to do this in windows but in Ubuntu simply install Firestarter on the gateway PC and configure it.

There are many guides for ICS here, both on Ubuntu & win.[/QUOTE]

Oh sorry, the desktop machine is running Windows XP.

---

### Post by mips on 2006-04-23
[http://support.microsoft.com/default.aspx?scid=kb;en-us;306126](http://support.microsoft.com/default.aspx?scid=kb;en-us;306126)
[http://support.microsoft.com/kb/308006](http://support.microsoft.com/kb/308006)

Configure the Ubuntu machine as the client. Obtain IP info via DHCP or configure the IP info statically.

---

### Post by xen on 2006-04-23
Thanks for the help, I will try these when I find the time tomorrow!

---

