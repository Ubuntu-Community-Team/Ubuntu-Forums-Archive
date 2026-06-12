---
title: "Linksys WUSB100"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by j.bell730 on 2009-10-01
I have tried for the past three days to get this wireless adapter to work. I think I had gotten ndiswrapper to load the drivers for it, but the device was not recognized by Ubuntu, so I tried a few commands to see if it would be recognized, like iwlist and iwconfig, but, alas, nothing. I tried reinstalling Ubuntu to see if the module would get loaded on installation, but, that did not work either, and now I am stuck trying to get packages for a laptop which has no connection, which, let me say is not real fun (I can't get GCC to work, because it depends on itself and I forgot how I installed it before :(). I've tried Googling many times, with many keywords, but none of the guides were the slightest bit helpful for my situation.

So, did anybody get theirs working? How? A guide's preferable.

---

### Post by j.bell730 on 2009-10-01
Nevermind, I just looked at the driver file and noticed that the name of the Windows XP driver is "rt2870". I'll try again and see if I can get the Ralink drivers to work. Hopefully, I can.

---

### Post by j.bell730 on 2009-10-02
Ok, I got the driver installed and the card is recognized, but, I still can't connect.
Output of iwconfig:
```
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```
And iwlist scan:
```
lo        Interface doesn't support scanning.

ra0       No scan results

pan0      Interface doesn't support scanning.
```
Anyone know why it says "Access Point: Not-Associated"?

---

### Post by j.bell730 on 2009-10-03
Meh, forget it. I just returned the WUSB100 and bought a Belkin F5D6050. The new card worked with a reboot.

---

### Post by pdc on 2009-10-03
well done; you must be very pleased to get your Belkin F5D6050 pci card? running: to help others, could you type 

> lspci in a terminal and tell us the results please?

---

### Post by j.bell730 on 2009-10-03
It's a USB device, so:
```
$ lsusb
Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by pdc on 2009-10-04
thanks; so it seems the Belkin F5D7050A you bought uses the

> rt2x00  driver from ralink

[http://linux-wless.passys.nl/query_chipset.php?chipset=Ralink](http://linux-wless.passys.nl/query_chipset.php?chipset=Ralink)

and the prior Linksys WUSB100 also used ralink, the rt2870 driver

___________

I guess I was intrigued if you installed a new driver for the Belkin;

(or did the rt2870 driver that was installed for the Linksys still load, and worked "out of the box" for your new Belkin ...

this is surely a big problem for folks: the "guts" of each device is not on the box; you don't know what you are buying;

_______-

so here both a Linksys and Belkin were ralink devices, and ralink provides open source drivers and firmware for linux

---

### Post by j.bell730 on 2009-10-04
No, I reinstalled Ubuntu (because I didn't wanna go through all the trouble of uninstalling the rt2870, which I built from source), put the Belkin in the USB slot, rebooted and I was prompted to choose a network to connect to on startup.

---

### Post by thecow on 2009-10-04
From what I can see on google is that only a B network adapter?  I wish someone would make a page listing all the known to be functional adapters 'and' if they work with WPA while on a G or N network.  That would make buying one very easy

---

### Post by j.bell730 on 2009-10-04
Nope, I have the box right in front of me, it's a G network adapter. Also, [here's a list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), which I used to find my current Belkin adapter. I typed out a list of potential network adapters, asked someone at Best Buy if they had any Linux compatible network adapters, and gave them the list that I made, and they seemed perfectly happy to help me. Simple as that.

---

### Post by thecow on 2009-10-04
If only it was as simple as that.  In the case of N adapters there are loads of problems.  Mine is listed on that list, however it does not work on the N band using WPA

---

