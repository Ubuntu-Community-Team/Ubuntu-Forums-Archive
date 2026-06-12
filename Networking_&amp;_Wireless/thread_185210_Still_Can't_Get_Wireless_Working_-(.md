---
title: "Still Can't Get Wireless Working :-("
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by boneman1 on 2006-05-31
I've installed Dapper on my laptop and everything works great when I'm connected via cable, but no luck with wireless.  I'm using an IBM High Rate pcmcia card by Lucent.  It's based on orinoco.  According to the Networking GUI  the card is there and active, but doesn't get an IP address no matter what I do.  I tried setting a static address and still no luck.  This card worked great in Hoary and Breezy.  If anybody has a solution I'd really appreciate it.

---

### Post by Dr. Nick on 2006-05-31
[quote=boneman1]I've installed Dapper on my laptop and everything works great when I'm connected via cable, but no luck with wireless.  I'm using an IBM High Rate pcmcia card by Lucent.  It's based on orinoco.  According to the Networking GUI  the card is there and active, but doesn't get an IP address no matter what I do.  I tried setting a static address and still no luck.  This card worked great in Hoary and Breezy.  If anybody has a solution I'd really appreciate it.[/quote]

Are the orinoco drivers part of the wlan-ng package? You may have to issue a command to get it going 

If so try
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="myssid" authtype=opensystem
sudo dhclient wlan0

I had to do that to get my prism2 card to show up. Have you tried the ndiswrapper bit yet? I used to have to use that route but with dapper it actually apperars the native drivers work just fine,

---

### Post by boneman1 on 2006-05-31
I don't know that it matters, but my wireless card shows up as eth1, not wlan0.  It's always been there and I've never had a problem with previous versions of Ubuntu.

---

### Post by Dr. Nick on 2006-05-31
[quote=boneman1]I don't know that it matters, but my wireless card shows up as eth1, not wlan0.  It's always been there and I've never had a problem with previous versions of Ubuntu.[/quote]

Probably doesnt matter, If you want to change it edit /etc/network/interfaces. Did it work correct before dapper? You said it worked in breezy if I recall. If you updated breezy to dapper then boot into your old kernel and see how it goes, If you did a fresh reinstall then that is not possible

---

### Post by boneman1 on 2006-05-31
I tried it both ways, upgrade and fresh install.  Wireless didn't work after upgrade from Breezy either.  Currently running a fresh install.  I hope I can get wireless working because I really like Ubuntu.

---

### Post by celem on 2006-05-31
Orinoco drivers are in the kernel. My Avaya Gold "just works". My other two cards also "just work". They are a Linksys WPC11-VN ver 4, and a  cheap ($10) Taiwan-made Wistron NeWeb WLAN CB-200B based on the Realtek Rtl8139 chipset. I amd VERY happy with Dapper's WiFi card support. I use WEP because these cards are all 802.11B and don't support WPA so I don't know if WPA works, but WEP works well on all three cards.

---

### Post by meat on 2006-06-01
I had Dapper installed on my laptop with the same card that you did and I could not get wireless to work either.   The card showed up and was active like yours.  I could see the wireless signal, but could not get an ip address when I typed dhclient.  Every once in a blue moon (maybe twice in 2 weeks) wireless would work after I did an update using update manager, but after a reboot, no go.

I let a friend borrow my laptop to see if he could get it to work.  He tried everything from a different WAP, no encryption, static IP and he could not get an IP address either.  I finally installed Win XP on my laptop and am using Ubuntu on a desktop machine.  I never had Breezy on the laptop, so I can't say if wireless worked with it.

Sorry if I am not any help, but I do feel your frustration.

---

### Post by woolbeo on 2006-06-03
I've had the same problem with my orinoco pcmcia card. During the beta some kernels would work, and some wouldn't. The last one that works with my card is 2.6.15-19

---

