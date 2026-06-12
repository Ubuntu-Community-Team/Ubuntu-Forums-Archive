---
title: "Intel 2200 Error &quot;No Wireless Devices&quot;"
date: 2005-02-19
forum: Networking &amp; Wireless
---

### Post by rusi_pathan on 2005-02-19
Installed ubuntu tonight...

Dell C400 + Intel Pro 2200 Wifi

While installation the Intel pro 2200 was detected (even prompted for the WEP key) and I thought wow...

But after intstallation the system Wireless link monitor shows "No Wireless devices"

Already tried to install the driver (@ [http://ubuntuforums.org/showthread.php?t=12270](http://ubuntuforums.org/showthread.php?t=12270) )

Any clues as to what's wrong or am I missing something.

Thanks in advance.

---

### Post by rusi_pathan on 2005-02-19
Btw could the problem be the fact that I specified it as my "primary" network device (eth1) during the installation?

---

### Post by somuchfortheafter on 2005-02-20
go to administration and network settings to check and see if the device is enabled and setup for dhcp or w/e is needed.

---

### Post by rusi_pathan on 2005-02-21
lspci shows that there is a Intel 2200 pro wifi
 
But no matter what I do it just wont find the device. Whats surprising is that during installation the card is detected and drivers are installed but iwconfig and ifconfig dont show up anything.
eth1: no device found


I also tried ndiswrapper (along with the proper windows drivers) and even that doesnt seem to work,
wlan0: no device found

Any clues... I'm really frustrated with this wifi thing.

---

### Post by somuchfortheafter on 2005-02-21
try
sudo ifconfig eth0 up
sudo iwconfig eth0

well mine at least is eth0 yours may be different but i do have the same card except on a toshiba tecra and all is well

---

### Post by rusi_pathan on 2005-02-21
My wifi is setup at eth1 (that's what it said during installation)

 # sudo ifconfig eth1 up
 eth1: ERROR while getting interface flags: No such device
  
 # sudo iwconfig eth1
 eth1: No such device

The wired LAN card is set up on eth0.

---

### Post by rusi_pathan on 2005-02-21
I am an idiot !

There was a damn IRQ conflict (which was clearly visible using $dmesg). The ipw2200 was using IRQ 7 which was dedicated to the || port.

Disabled the || port from the BIOS (Ver. A12, Dell C400). Removed "exclude irq 7" from /etc/pcmcia/config.opts and everything runs like a charm.

Ubuntu detects and installs everything (even Intel 2200 b/g PRO wifi).

Works right out of the box  :-D

---

### Post by Psquared on 2005-10-07
[QUOTE=rusi_pathan]I am an idiot !

There was a damn IRQ conflict (which was clearly visible using $dmesg). The ipw2200 was using IRQ 7 which was dedicated to the || port.

Disabled the || port from the BIOS (Ver. A12, Dell C400). Removed "exclude irq 7" from /etc/pcmcia/config.opts and everything runs like a charm.

Ubuntu detects and installs everything (even Intel 2200 b/g PRO wifi).

Works right out of the box  :-D[/QUOTE]

I know this a little late, but how did you discover that? I have the same problem with Breezy (didn't have it with Hoary) in that the system can't find my wireless adapter. (eth1, Intel Pro Wireless using ipw2200)

What I mean is, what message did you see in dmesg that clued you in?

---

