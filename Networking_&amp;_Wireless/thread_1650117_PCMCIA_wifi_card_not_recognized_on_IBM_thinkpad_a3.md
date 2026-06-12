---
title: "PCMCIA wifi card not recognized on IBM thinkpad a30p with  ubuntu 10.04"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Ruby on 2010-12-21
Hi, i've installed Ubuntu 10.04 on my IBM thinkpad a30p.
now everything seems to work fine, except for the wifi card (edimax ew-7708il) i have.
PCMCIA modules are loaded, but the card just doesn't appear in the network devices...
Any ideas?

---

### Post by Ruby on 2010-12-21
ok some news...
I've found the genuine modell name for the card. It's ew-7708PN, a quick search shows this card SHOULD be supported out of the box; i.e - [http://ubuntuforums.org/archive/index.php/t-783395.html](http://ubuntuforums.org/archive/index.php/t-783395.html)
But - still no luck...

---

### Post by chili555 on 2010-12-21
With the device inserted, please open Applications > Accessories > Terminal and run and post:```
lspcmcia -v
lsmod | grep rt2
dmesg | grep -i rt2
```Thanks.

---

### Post by Ruby on 2010-12-21
o.k, lspcmcia returned this;
```
ruby@ruby-laptop:/$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.0)
	Configuration:	state: on	ready: unknown
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.1)
	Configuration:	state: on	ready: unknown

```

The other two returned nothing...

---

### Post by chili555 on 2010-12-21
There doesn't seem to be any device present in the PCMCIA slot at all, does there? Let's try:```
sudo lshw -C network
```How about the other commands? Thanks.

---

### Post by Ruby on 2010-12-21
wow... turns out one of my pcmcia slots just doesn`t work -_-
i put the card in the other slot, now lspcmcia gives
```
ruby@ruby-laptop:/$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.0)
	Configuration:	state: on	ready: unknown
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.1)
	Configuration:	state: on	ready: unknown
			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V

```
lspci has now added
```
07:00.0 Network controller: RaLink RT2800 802.11n PCI

```
lsmod and dmesg now say this
```
ruby@ruby-laptop:/$ lsmod | grep rt2
rt2860sta             481561  1 
ruby@ruby-laptop:/$ dmesg | grep -i rt2
[ 1730.835183] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1730.860784] rt2860 0000:07:00.0: enabling device (0000 -> 0002)
[ 1730.860814] rt2860 0000:07:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 1730.862280] rt2860 0000:07:00.0: setting latency timer to 64
[ 1731.532119] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[ 1934.092707] rt2860 0000:07:00.0: enabling device (0000 -> 0002)
[ 1934.092730] rt2860 0000:07:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 1934.093833] rt2860 0000:07:00.0: setting latency timer to 64
[ 1934.163329] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat

```

still, obviously, no link. but we`re getting some progress :P

BTW ifconfig is showing a wlan0 but Network Connections in system menu doesn`t. why is that?

---

### Post by chili555 on 2010-12-21
> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.datSlide the device out of the slot slightly, so it's in the correct slot but not making electrical contact. In a terminal:```
sudo mkdir /etc/Wireless/RT2860STA/
```If it already exists, that's fine; please proceed:```
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```Write one word:```
Default
```Proofread, save and close gedit. ```
sudo rmmod -f rt2860sta
sudo modprobe rt2860sta
```Slide the device back in. Any improvement?

---

### Post by Ruby on 2010-12-21
still the same... same error on dmesg | grep -i rt2 as well.

---

### Post by chili555 on 2010-12-21
> [ [COLOR="Red"]1934.163329[/COLOR]] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.datIf it's the same timestamp, it's the same old information. Just because I'm OCD and skipped my meds today, please reboot and run the tests again.

---

### Post by Ruby on 2010-12-21
well chili555, your OCD saved the day :)
After reboot the wifi came to life, connected and is working great.
still the error keeps coming up on dmesg.
```
ruby@ruby-laptop:~$ dmesg | grep -i rt2
[   18.192551] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   18.230539] rt2860 0000:07:00.0: enabling device (0000 -> 0002)
[   18.230564] rt2860 0000:07:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   18.231460] rt2860 0000:07:00.0: setting latency timer to 64
[   85.036778] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat

```

Anyway, thank you very much for the help. i'm gonna settle with this. looks like this file isn`t necessary for the device`s proper work.
:)

---

### Post by chili555 on 2010-12-21
If it's working, it's all good! Have fun.

Please drop down Thread Tools and mark the thread as Solved.

---

