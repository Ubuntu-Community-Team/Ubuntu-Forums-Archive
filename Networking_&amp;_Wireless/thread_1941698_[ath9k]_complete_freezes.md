---
title: "[ath9k] complete freezes"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by Ichika on 2012-03-16
Hi,

I tried the last Ubuntu Live CD but my computer completely freezes because of the wifi.

I have 3 computers : archlinux, debian, fedora. I want to install Ubuntu on my Archlinux (main computer).

I bought this card twice : TP-LINK WN851ND (one for the main computer, one for the debian server). When it's a wired connection, no problem at all. The ath9k and others drivers are loaded, I can see them with lsmod.

When I connect to my network (Vodafone Box in Germany), the computer freezes. I can't do anything except hard reset it.

The wifi is WPA encrypted with TKIP/PSK... that's what I can see with iwlist wlan0 scanning from fedora, debian, arch but on my PlayStation 3, it found that my WiFi network is AES encrypted.

Anyway, I tried with no encryption at all but I still have the problem.

My laptop with Fedora works fine. My computer with Arch and future Ubuntu and my debian server don't.

I have the last kernel on ArchLinux, the kernel 2.6.32-5 on Debian but I tried compat wireless on ArchLinux and I still have the problem.

Since it's a freeze, I don't get any kernel debug messages and I can't find anything in /var/log. Honestly, I don't even know what to look for.

I tried the netconsole system debug but I can't get it to work. Everything looks connected but I don't receive any messages from my crashed computer.

Does anybody have an idea ?

Thanks.

---

### Post by zinadork on 2012-03-16
If you can, turn off wireless N in your wifi router.  I found that this driver works much better using only wireless G.

---

### Post by Ichika on 2012-03-17
Hi,

unfortunately, it didn't change anything. I still have the freeze. 

I submitted a bug report on the kernel bugzilla system : [https://bugzilla.kernel.org/show_bug.cgi?id=42903](https://bugzilla.kernel.org/show_bug.cgi?id=42903)

During my research of informations, I've seen a lot of people with freezes and ath9k but it was with old kernels... and I have the last one with compat wireless so I don't know what's wrong.

---

### Post by Ichika on 2012-03-19
Hi,

I still have my problem. 

Unfortunately, I need the WiFi. I'm looking for a cheap wireless pci card that doesn't use ath9k. It is a temporary solution (waiting to find what the problem is with my cards and ath9k) so that's why the cheapest the better.

I need WPA, 100mbits minimum (can go lower of course but 100mbits would be great), support wifi b/g/n, kernel drivers (not ath9k of course), available on Amazon.de or other websites that ship in Germany.

Thanks.

---

### Post by Ichika on 2012-03-20
For those interested, please find the patch in the bug report.

---

### Post by MartinusEx on 2012-03-21
> **Ichika said:**
> For those interested, please find the patch in the bug report.

Hi,

I have the same issue (TP-Link WN851ND in a older machine running Oneiric freezes after a while) but out of the bug report I do not understand anything.
What did you do to remedy this?
Did you get rid of the problem?

I'll try myself to find my way, but if you could provide what you actually have done to get rid of the freeze. I'd be glad.

THX so far and good luck

Martin

---

### Post by pieterio on 2012-07-09
what might help (i'm a complete newbie in the linux world but am trying to improve my knowledge as well as share things i learned with other peepz);
i run ubuntu 12.04 LTS and had similar problems: laptop (Acer Aspire 7250) wouldn't even start up like is should without ethernet connected..turned off networking to get rid of freezes (like, when disconnecting ethernet *like that* it would freeze instantly...)
then i read on a french forum that if you BOOT FROM NETWORK (that is: without actually being connected through ethernet) it's all fine: i get wireless when i want to, i get ethernet when i connect it and can disconnect whenever i want with the system immediately searching for wireless..

so far no probs. everyone thought it was quite weird but it works :)

hope this helps...

---

