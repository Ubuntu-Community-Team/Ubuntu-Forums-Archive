---
title: "Atheros AR5211 on Thinkpad R40"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by gus.ke on 2011-02-13
Hey all,
I just installed 10.10 Desktop (32-bit, kernel 2.6.35-22) on my old IBM Thinkpad R40.  I am having a problem connecting to wireless access points.  The network applet can detect networks, but cannot connect.  I have tried substituting my WPA2 PSK for WEP and even ditching secure connections entirely, but it cannot connect.  "lspci" returns:
"02:02.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)"
"dmesg" returned repeated timeouts for wlan.  "iwlist scan" returns "no scan results" for wlan, despite the fact that I can see several networks in the applet.

If anyone has had similar issues or just feels like helping out, I would really appreciate it. :D
Thanks,
Gus

EDIT: I forgot to mention that my check for third-party drivers also returned no results.

---

### Post by Tarkan640 on 2011-02-13
If you haven't gotten any internet, you probably need ndiswrapper. It is kind of pain to set up but there are tutorials how to get it to work. youv already found your wireless card with lspci, then you have to look up the drivers that go for it. Install a program for linux called ndiswrapper, then use it to "wrap" the windows driver for your card. It is slightly more detailed then that but google search installing and using ndiswrapper. If your problem is different and you already know about ndiswrapper, then my bad.

---

### Post by gus.ke on 2011-02-22
Thanks, I'll give that a try.

---

### Post by WNG on 2011-05-23
Hi I was wondering I have the same nasty wireless card. I used ndisgtk to 'install' net5211.inf but its giving me a invalid driver on the GUI list.

I was wondering if you had any luck and managed to get the AR5211 card working?

Thanks,
Will

---

### Post by gus.ke on 2011-05-25
Never got the bugger working, sorry.  I tried using another card, but  IBM's BIOS locks all others out.  After I finally got around the restriction, I found out that the other card (an old Broadcom I pulled out of a Dell) was not supported either.  I also tried other distros with both cards.  No success.  Eventually, I gave in and used an external adapter.

---

