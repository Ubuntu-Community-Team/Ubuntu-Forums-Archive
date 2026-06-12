---
title: "Wireless suddenly disappeared from Karmic - wtf?"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by emastro on 2009-11-08
I have a Compaq mini 700 and I've been using Ubuntu Netbook Remix for a few months now, starting shortly after 9.04 came out. I upgraded to 9.10 about a week ago (actually, in the end I had to wipe everything, install 9.04 from scratch and then upgrade to 9.10 - it's a long story) and everything worked just fine out of the box. Today I tried to install an USB DVB tuner, without success, shut down the netbook, and when I powered it up again, I suddenly had no connectivity. 

I've checked the access point and it still works fine (provides connectivity to my wife's laptop and my smartphone)

The proprietary driver for the wireless card (wl) is still correctly loaded and shows in lsmod. Lspci lists both wireless and wired cards correctly, although neither seems to work properly: the wired connection only works (and even then, only occasionally) if I boot the machine with a cable already connected - and if I disconnect the cable I get a hard crash, screen goes black and the only way out is a power-cycle. The wireless card is listed in ifconfig as "eth1_rename" instead of "wlan0". Sometimes, booting the machine with a cable already connected causes the Ethernet card to disappear and ifconfig lists the wireless card as eth0 - even in these cases, though, lspci sees and identifies correctly both cards.

As I said, I have used Karmic for about a week on that machine before this happened, last time was this afternoon. I should point out that I did not install/replace/update any drivers. I installed the dvb utilities and tried (unsuccessfully) to use the USB tuner, that's all. Turned off the computer, and when I turned it back on it had no connectivity.

Anyone seen anything like that?

Eugenio

---

### Post by emastro on 2009-11-10
*Bump*

Tried wiping and reinstalling from scratch. If I install 9.10 directly, no network cards are seen at all - wired and wireless: all that happens is a hard crash if I insert and remove a network cable. If I install 9.04 and then upgrade to 9.10, it's fine for one or two reboots and then, again, wlan0 becomes eth1_rename and there's no way to make it work again. I'm not sure, though, whether this would happen anyway or if it was my fault for installing the available updates.

Any help? Someone?

---

