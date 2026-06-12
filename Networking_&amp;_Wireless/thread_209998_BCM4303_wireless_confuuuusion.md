---
title: "BCM4303 wireless confuuuusion"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by PsychicPsycho3 on 2006-07-06
Let me start off by saying I'm not a n00b to computers, but am to linux.

I just downloaded and installed Ubuntu 6.06 on my Dell Inspiron 8200. I'm trying to get the built in wireless Truemobile 1080 (whose firmware is Broadcom 4303) to work. From the get-go my card was recognized, but shows up at eth1. When I try to configure it, it seems like it's trying, but after I OK out of the configuration box, and go back into it, the card is deactivated again. 

I went through the whole ndiswrapper business, which I'm not sure I even had to, since the card was being recognized already. It shows up in iwconfig with all the information, but when I type "sudo iwlist eth1 scan" I get "eth 1     interface doesn't support scanning : No such device"

Let me end by saying it's late, I've been at this for hours and I'm frustrated... and TIA for any help.

---

### Post by ubunturules on 2006-07-06
Try this:
```
sudo gedit /etc/modprobe.d/ndiswrapper 
```
and change eth1 to wlan0, save an then reboot.

---

### Post by PsychicPsycho3 on 2006-07-06
just did a fresh install 'cause I think I effed up the loopback adapter. Anyway, wired is working no problem.

When I open the ndiswrapper fire with gedit, there's nothing there at all. Perhaps this is the problem.

---

### Post by PsychicPsycho3 on 2006-07-06
Update:

I've reinstalled ndiswrapper and did all the blacklisting business. I used the code you posted and the file was there this time. *However*, it already said wlan0 instead of eth1, so I'm still quite confused.

::grumble::

---

### Post by atrus123 on 2006-07-06
[QUOTE=PsychicPsycho3]Update:

I've reinstalled ndiswrapper and did all the blacklisting business. I used the code you posted and the file was there this time. *However*, it already said wlan0 instead of eth1, so I'm still quite confused.

::grumble::[/QUOTE]

It makes no difference if it says eth1 or wlan0 (really, it doesn't).  That's only user choice.

If you keep having problems, it might be your driver.  You may want to try finding an older or newer driver from your card vendor.

---

