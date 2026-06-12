---
title: "driver for my Wifi"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by jrev on 2011-10-30
I am looking to install the USB Wifi adaptator NetGear N150 wna1100.
for a PC with Ubuntu 10.04 lucid.

Got a clue ?
Thanks

---

### Post by mikewhatever on 2011-10-30
Don't know about your wifi, but to get clues about a USB adapter, take a look at the output of **lsusb**.

---

### Post by jrev on 2011-10-31
> **mikewhatever said:**
> Don't know about your wifi, but to get clues about a USB adapter, take a look at the output of **lsusb**.
thanks and the output is 


[B]Bus 001 Device 004: ID 0846:9030 NetGear, Inc. 
[/B]
what am I going to do now ?

---

### Post by wildmanne39 on 2011-10-31
Hi, follow the directions in post 2 at this link and you should get it working, if you were running 11.10 the driver is installed be default in it.
[http://ubuntuforums.org/showthread.php?t=1663232](http://ubuntuforums.org/showthread.php?t=1663232)
Thank you

---

### Post by bogan on 2011-10-31
[B]Hi! Jrev,
You posted:
[/B]> I am looking to install the USB Wifi adaptator NetGear N150 wna1100.
for a PC with Ubuntu 10.04 lucid.I have one of those, it is a bit broken physically, but still works OK.
**Chili555** helped me to get it going with Linux 9.1 and it still works with 10.10 and 11.10.
[B]See full details in: Re: Linux Won't recognize Realtek WLan  Feb15-21 2010
in this forum.
[/B]             
( Sorry for the Bold bits I can`t get rid of them.)

The essential part is as follows:
**If **Windows Device Manager shows: Quote: "802.11 USB Wireless LAN Card" End quote.
   **And If** lsusb gives, inter alia:
> Bus 002 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3970[Then yours is the same as mine.]
Quote:
This card has a fairly well known issue. Two different and,  presumably conflicting drivers load for it. With the Ralink (getnet) inserted,  please run:    
   ```
   lsmod | grep rt2 
```You might see all of the following drivers installed: ```
  rt2870sta rt2x00usb rt2800usb 
```If so, please do:   ```
 sudo gedit /etc/modprobe.d/blacklist.conf 
```Use any other text editor, nano or kate or vim, if you don't have gedit. Add two new lines: ```
 blacklist rt2800usb blacklist rt2x00usb 
```Proofread carefully, save and close gedit. Now reboot. Does the Ralink device now work as expected?
End Quote

I hope it works as well for you, thanks to **Cjli555** not to me. **Edit:** From your last post looks as though I got it wrong, mine was a GetNet N150 wna1100.** Edit**: Was wrongly confused with' Netgear'
Chao!** bogan**.

---

