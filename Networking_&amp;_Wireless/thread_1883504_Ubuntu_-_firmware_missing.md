---
title: "Ubuntu - firmware missing"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by Chris01902 on 2011-11-19
Plz take into consideration I hardly have any experience using the terminal

I looked and saw similar threads to this but I am using an iPhone for a hotspot, don't know if that makes a difference. I am also using a 4gb pendrive to host the ubuntu filesystem.


I ran  lspci - nnk. | grep -A2 net

I'm looking at the wireless 
Network controller [0280]: broadcom Corp bcm4321 802.11b/g/n [14e4:4329] (rev 01) subsystem: Linksys device [1737:0060]
kernel driver in use : b43 - pci - bridge


I typed this from my iPhone. I have been google searching every keyword term I can to learn a much as I can as fast as I can. I would wish a blessing on anyone who can help w this!

---

### Post by chili555 on 2011-11-19
Can you get an ethernet connection temporarily? If so, open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
iwconfig
```You should be all set.

---

### Post by Chris01902 on 2011-11-19
Hey thx,

All I have is an iPhone USB for tethering. Should I still do as you said?

---

### Post by chili555 on 2011-11-19
> **Chris01902 said:**
> Hey thx,

All I have is an iPhone USB for tethering. Should I still do as you said?If you able to get to the internet, please do. After the module *wl* loads without complaint or error, you may detach the tether and enjoy your wireless.

---

### Post by Chris01902 on 2011-11-19
Chili I am unable to access any Internet networks whatsoever

---

### Post by Chris01902 on 2011-11-19
Wlan0.   IEEE 802.11bg Essid:off/any
Mode:managed access point: not associated Fragment the: off RTS: off

---

### Post by antoiner_roquentin on 2011-11-19
I am having trouble with my BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).
It says the firmware is missing, so I tried using the  b43-installer app to get ahold of the firmware, and everything seemingly went fine, but the driver does not come up under System > Administration > Additional Drivers. 

I thought that these two problems were similar. Any thoughts on where to go from here???

I am getting pretty frustrated!

---

### Post by Chris01902 on 2011-11-19
This only started happening when I started using a pen drive. I partioned the USB drive and left the 320 gb hd as swap space because there are sone blocks on the hd that are corrupt.

Even when I ran ubuntu from a cd, before I partioned the drive, I could access the net. It detected automatically. This is all I can think of

---

### Post by chili555 on 2011-11-19
> **antoiner_roquentin said:**
> I am having trouble with my BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).
It says the firmware is missing, so I tried using the  b43-installer app to get ahold of the firmware, and everything seemingly went fine, but the driver does not come up under System > Administration > Additional Drivers. 

I thought that these two problems were similar. Any thoughts on where to go from here???

I am getting pretty frustrated!Do you have the exact same device?> Network controller [0280]: broadcom Corp bcm4321 802.11b/g/n [[COLOR="Red"]14e4:4329[/COLOR]] (rev 01) If so, follow the advice above; if not, start a new thread and give us:```
lspci -nn | grep 0280
```

---

### Post by chili555 on 2011-11-19
> **Chris01902 said:**
> Wlan0.   IEEE 802.11bg Essid:off/any
Mode:managed access point: not associated Fragment the: off RTS: offWhat does this tell us?```
dmesg | grep -i -e b43 -e wl -e firm
```Thanks.

---

### Post by Chris01902 on 2011-11-19
It's what ip config says without the rest of why you said to type. Trying to think outside the box

---

### Post by chili555 on 2011-11-19
What does this tell us?
```
dmesg | grep -i -e b43 -e wl -e firm
```Please post it.

---

### Post by Chris01902 on 2011-11-19
This one is large can I email you a photo from my iPhone?

From a ***** perspective I can zone in on a few things

B43/ucode11.fw not found
B43-open/ucode11.fw not found
Then it gives me a web URL 

What I don't understand is this was not happening when I ran the livecd bit now that I partioned a thumb drive and I am running them the USB , it is.

---

### Post by chili555 on 2011-11-19
Please follow this procedure: [http://ubuntuforums.org/showpost.php?p=11189434&postcount=47](http://ubuntuforums.org/showpost.php?p=11189434&postcount=47)

---

