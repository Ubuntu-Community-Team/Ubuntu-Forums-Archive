---
title: "Headphone Jack Doesn't Work"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by dirtmcgirt75 on 2007-08-14
Loaded 7.04 on an HP Compaq 6110 laptop.  Only immediate problem I see is that the headphone jack doesn't work.  More specifically, sound works just fine via the onboard speakers, but plugging in my headphones doesn't do anything - the sound continues to come through the onboard speaker as if I haven't plugged in.  

I am certain the headphones and the hardware are fine since the XP build on the machine had no problem playing music before.  Tried a few suggestions on these forums but haven't seen anything specific to this problem yet.

Thanks for any suggestions you can pass along.

---

### Post by duffrecords on 2007-08-15
Please enter the following command in the terminal and post the results here.
```
sudo lshw -C multimedia
```
Or you could try this instead:
```
sudo lshw -C sound
```
This should tell us more about your sound card and which driver it's using.

---

### Post by zarksentinel on 2007-08-16
here is my result 

  *-multimedia
       description: Multimedia controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel
       resources: iomemory:cfdfc000-cfdfffff irq:169

---

### Post by duffrecords on 2007-08-16
What's your sound card's manufacturer and model number?

---

### Post by thc_oi on 2007-08-19
i have a same problem .. my sound card is  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (lspci)

---

### Post by Gremlinzzz on 2007-08-19
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)

---

### Post by aiker on 2007-08-28
I have the same problem on ASUS A6B00Vc laptop (Intel HDA sound system) and Ubuntu 6.10

---

### Post by MartijnWeterings on 2007-08-29
I was able to solve this problem by installing a newer version of the drivers.

[http://ubuntuforums.org/showthread.php?t=534070&highlight=packard+bell](http://ubuntuforums.org/showthread.php?t=534070&highlight=packard+bell)

---

