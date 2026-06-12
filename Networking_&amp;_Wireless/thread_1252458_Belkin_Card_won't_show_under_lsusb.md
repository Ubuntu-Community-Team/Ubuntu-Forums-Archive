---
title: "Belkin Card won't show under lsusb"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by Bacon! on 2009-08-28
Hey all,

For a few nights now I've been trying to get my F5d7050 (v 3000) working under Jaunty (Xubuntu). I did ndiswrapper with the driver that came on the install CD (BLKWGU.inf), but my device still won't appear at all when I do lsusb. I tested the card on a different PC running XP, and it worked fine so I know it's not the card.

Any help?

---

### Post by kerry_s on 2009-08-28
if its a pcmcia card use "lspci".
have you checked "iwconfig"?

---

### Post by Bacon! on 2009-08-28
Ah sorry I should have mentioned that it's a USB.

I've tried iwconfig, but even after doing the ndiswrapper all it gives is lo and pan0.

---

### Post by kerry_s on 2009-08-28
what did you do with ndiswrapper?

should go something like this:

sudo su
ndiswrapper -i BLKWGU.inf
ndiswrapper -l
echo ndiswrapper >> /etc/modules
reboot

---

### Post by Bacon! on 2009-08-28
Yeah that's pretty much step-for-step what I did (except I also did depmod-a and modprobe), and no luck.

---

### Post by abn91c on 2009-08-28
that particular model should be plug and play with all (*)buntu, without ndiswrapper. Plug card directly to PC or use a different cable.

---

### Post by kerry_s on 2009-08-28
bummer, are you using the right *.inf, you need the xp one, you also need the *.sys file, they have to be in the same place when you do the ndiswrapper -i

i have the pcmcia card version.

---

### Post by Bacon! on 2009-08-28
> **kerry_s said:**
> bummer, are you using the right *.inf, you need the xp one, you also need the *.sys file, they have to be in the same place when you do the ndiswrapper -i

i have the pcmcia card version.

I should have all the right .inf, .sys, and .cat. One thing I noticed was that the .sys file was called BLKWGUXP.sys, but when I copied it to BLKWGU.sys it didn't make a difference.

> that particular model should be plug and play with all (*)buntu, without ndiswrapper. Plug card directly to PC or use a different cable.

Yeah, that's why I originally got the card, but it doesn't recognize it at all. Maybe tomorrow I'll bring it back for a pci card.

---

### Post by Cuba71 on 2009-08-29
I've tested the Belkin F5D7050 (050d:705d) with the native **rt37usb** Ubuntu driver and it works fine in 9.04 Jaunty and 9.10 Karmic Alpha-4.

---

### Post by Bacon! on 2009-08-29
So now I've loaded Ubuntu up rather than Xubuntu, and still no dice.

One thing I did notice is that if I do lsmod the rt73 doesn't show up, but once I modprobe it and "lsmod | grep rt" I get:

```

rt73usb 33412  0
crc_itu_t 10112  1 rt73usb
rt2x00usb 18688  1 rt73usb
rtx00lib 37888  2 rt73usb,rt2x00lib
led_class 12036  1 rt2x00lib
mac80211 217208  2 rt2x00usb,rt2x00lib
cfg80211 38032  2 rt2x00usb,mac80211

```As well as a few others which seem unrelated -- but even then I get nothing under both iwconfig and lsusb.

The computer I'm running it on **is** a bit of a clunker, but I don't see how that would make much of a difference; it is usb2.0 and the card doesn't have any other sys reqs other than that.

---

### Post by Wiebelhaus on 2009-08-29
Sorry but I must be honest , Anything made by Belkin is pure trash regardless of Operating System or Keyboard or KVM or Router or whatever , pure rubbish.

---

### Post by Cuba71 on 2009-08-30
> **Wiebelhaus said:**
> Sorry but I must be honest , Anything made by Belkin is pure trash regardless of Operating System or Keyboard or KVM or Router or whatever , pure rubbish.

I have 5 computers fitted with the same Belkin F5D7050 adapter, running XP, Vista, Ubuntu without any problems, for me they're great

---

### Post by Bacon! on 2009-09-03
Thanks for your help everybody.

I ended up returning the Belkin card and getting the CNet CWD-854, which worked out of box and gives me decent signal strength even though I'm 3 floors away from the router -- and it was $10 cheaper.

---

