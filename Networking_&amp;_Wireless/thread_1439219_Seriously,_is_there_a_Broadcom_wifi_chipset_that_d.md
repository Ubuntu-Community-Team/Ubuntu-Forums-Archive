---
title: "Seriously, is there a Broadcom wifi chipset that doesn't suck?"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by fargle on 2010-03-25
I swear this is not a troll, I'm legitimately asking.  Because if there is a Broadcom chipset that doesn't suck, on Linux much less on Windows, I have yet to see it.

So I ordered and got a new Dell Studio 14z (sweet machine BTW!), and the only wireless option available was a Dell Wireless 1397 card, which is a Broadcom 4312 chip apparently.  So I thought I'd give it a shot, since I didn't have much choice anyway.

Anyway, last night on my home WPA2-PSK network, all of a sudden it acted like it had lost its default gateway, even though my iPhone worked fine.  I could ping the gateway but not get past it.  A netstat -nr showed the default gateway still there.

Strange, but I'm running Lucid Beta 1, so I figured, who knows.

Then today, I have it on my desk at work, connected to a Cisco guest wireless network, no encryption at all, and when I come back to my desk, the wireless is disconnected and dmesg is full of this:

```
Mar 25 15:06:05 studio14z kernel: [ 5688.521253] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Mar 25 15:06:05 studio14z kernel: [ 5688.521260] b43-phy0: Controller RESET (DMA error) ...
Mar 25 15:06:05 studio14z kernel: [ 5688.736425] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Mar 25 15:06:11 studio14z kernel: [ 5694.249190] b43-phy0: Controller restarted

```

and it's dead, Jim.  No wireless networks to see.

I've had problems in the past with other Broadcom cards, even on Windows - I've had the same two laptops, one with an Intel IPW-2200 and one with a Broadcom card, sitting side-by-side with the Broadcom showing 40% less signal strength and dropping packets.

Anyway, I just ordered a Dell 5100 AGN card (Intel), but I'm the security/wireless guru at work and I seriously want to know if anyone has ever had a good, reliable Broadcom card.

---

### Post by mcooke1 on 2010-03-26
short answer, yes. Installed one into Dell Inspiron so I could use my home network on N 5 GHz only. Works perfectly in Vista, Mandriva 2010 and Xubuntu 10.04. It was easy to install in Mandrava a bit difficult in Xubuntu because Jockey was not working. The card is the BCM4321 and in Linux uses the sta broadcom driver. I have only used it to connect to N 5 GHz and its connected at the moment at 100%. I have the Intel wifi link 5100 AGN on another Laptop it works good in linux.

  [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by fargle on 2010-03-26
Okay, thanks, good to know.

Although I've also seen some things go by from people saying their Broadcom always reports 100% signal strength no matter what, so who knows on that.

I do appreciate the confirmation on the 5100, because that's what I ordered and it should be here on Tuesday.  Luckily I haven't switched to using this laptop primarily as yet (waiting for 10.04 final) so it's not the huge problem it would have been in the meantime.  I think I would have had to get a USB adapter from Micro Center in the meantime if I were depending on this wireless card.

---

