---
title: "Broadcom and bcmwl-kernel-source"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by ublintu on 2010-05-05
Hi,

I had some problems, when I wanted to get my broadcom wireless to work and if someone else has the same problem, maybe this helps:
In 9.10 I installed bcmwl-kernel-source to get my wireless to work, without internet, from the CD.
This time (in 10.04) I got error messages. I tried to install it with internet as well, but error again.
Then I installed 10.04 again, like this:
In the live CD I went to the hardware drivers. There was my broadcom driver listed, so I clicked to activate it and I could connect to the internet. I checked sinaptic package manager and bcmwl-kernel-source was installed. After this, from the live CD, I installed ubuntu on my laptop. When the process finished, I restarted it and bcmwl-kernel-source was installed and I had internet.
Dell Vostro 1000
lspci -vvnn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
but bcmwl-kernel-source working with
BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware.
Anyway, I have wireless now.

---

### Post by Lilonius on 2010-05-09
I tried it in 10.04 and does not work. Checked half of the forum with related topics and tried 10000 things and still does not work.

Should we expect some fix anytime soon?

---

### Post by Lilonius on 2010-05-12
One thing that it is working for me, at least for the moment, is that anytime i turn on the notebook, i first need to switch off the button for the wireles card, and when the system is up and running i turn it on and it finds the networks. but even if ti connects to a network the icon displays the red exclamation mark. but i can live with that.

---

### Post by zdenal on 2010-10-11
I have written an simple how-to to fix the Broadcom non working wireless on Lucid

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

Check it out, maybe it helps..

---

