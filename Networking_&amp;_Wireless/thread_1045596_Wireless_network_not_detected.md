---
title: "Wireless network not detected"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by NeilBlack on 2009-01-20
I've just installed Ubuntu 8.10 on my laptop and it can't detect my home wireless network. It can detect a wired network, and works fine with that.

I know you'll need more information, so please help me to help you to help me. How do I find out what wireless card I have, and any other relevant information you need to help me?

I've had Ubuntu on this laptop before, I'm not sure what version it was but the wireless worked most of the time then.

---

### Post by underwhelmed on 2009-01-20
there are so many variation on this post; I'm just sitting back and waiting until there's a definite solution.
I'm using a fujitsu amilo 2735 and am was getting into difficulties until I decided to hang fire and wait a bit....
but if anyone does have a foolproof solution--- gratefully accepted;)

g

---

### Post by NeilBlack on 2009-01-20
I did a little more research and found what I think are the system specs for my computer. I typed in the exact model name and number I found on the bottom of the computer, Compaq Presario C500, but the specs I found listed a larger hard drive than my computer has.

Anyway according to that site the "Wireless Technologies" is a C556CA: 802.11b/g WLAN, from another source I have reason to believe it is made by a company called Broadcom.

The wireless router I have is a Belkin G Wireless Router. It's running a security-enabled network (WPA2)


What else do you need to know to help me?

---

### Post by barrm on 2009-01-20
I struggled with my dual boot laptop (w/Broadcom wireless card) for WEEKS. I tried ndiswrapper and fwcutter...and everything I could read about trying to get my Broadcom 4309 card to work in Ubuntu. It worked flawlessly in Win XP...but refused to 'play' with Linux. I never was too good with terminals and command lines...but I actually got to understand quite a bit of that stuff while following the endless discussions here about extracting and using propitiatory drivers in this environment. Being quite lazy, like I am, and a bit creative, like a lazy person must be...I tried something which I had not seen discussed. I did a bit of research and found out which wireless cards Ubuntu 'liked'.  I bought an "Intel Pro 2200BG Mini-PCI" card on Ebay....new...$13 and delivered in 3 days.  Removed 2 screws from the back of my Dell Inspiron, popped the @?@&&! Broadcom out, inserted the Intel, replaced the cover...and then powered the sucker up. Nothing else, and Ubuntu liked it!! ..it worked right out of the box...immediately!!!!! XP recognized the card, ran a wizard, and installed the driver...Bottom line .... $13 and 5 minutes cured my headache.

---

### Post by NeilBlack on 2009-01-21
I fixed it. Turns out all I needed to do was install a different driver.

---

### Post by Dragonbite on 2009-01-27
> **NeilBlack said:**
> I fixed it. Turns out all I needed to do was install a different driver.

What different driver did you install?

I have done the Hardware Drivers thing which downloaded the cutter and such and it still won't detect anything!

It's a Broadcomm 4309.

---

### Post by kevdog on 2009-01-28
If you guys with the 4309 chipset could post:

lspci -nnm

It would help a lot.

---

### Post by Dragonbite on 2009-01-29
> **kevdog said:**
> If you guys with the 4309 chipset could post:

lspci -nnm

It would help a lot.

Ok, I got

```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
01:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
01:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
01:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
01:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)

```

And when I tried  **lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl** I got
```
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43

```

---

