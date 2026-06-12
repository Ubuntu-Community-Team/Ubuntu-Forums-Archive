---
title: "D Link DWA-125 on Ubuntu 10.04"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by w0ss4g3 on 2012-02-03
Hi, having a nightmare getting this to work.. have read a few of the various threads but I can't get anywhere :(

I've not got ndiswrapper installed.. and don't really want it.

so far:

lsusb gives:

Bus 002 Device 003: ID 2001:3c19 D-Link Corp. [hex] 

iwconfig :
lo        no wireless extensions.

eth0      no wireless extensions.

dmesg | grep rt2
[ 1267.292687] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1267.298830] usbcore: registered new interface driver rt2870

First thing I've noticed is that the device ID is different to the other threads on the DWA-125.

Anyone with a little more experience give me some help?

thanks in advance!

---

### Post by sudodus on 2012-02-03
It does not look so good according to the following link (flaky, no support for WPA2. ndiswrapper does not work)
[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

1. Since you run an old version of [KLX]ubuntu, download the iso file of the new version 11.10 and test it live from a CD or USB drive! New kernels have better support for wifi devices.

2. Depending on how you value your time versus cash, consider getting a card or USB device which is reported to work out of the box!

---

### Post by w0ss4g3 on 2012-02-03
Unfortunately I'm in the last year of my PhD and this is my office machine... I can't really afford to reinstall the OS at the moment - have spent a long time getting a lot of things set up!

The IT department handed me the USB cos they can't afford to route a cable through to the new office I've been put in. I've got the thing to get a blinking light now - bit better than before.. I can see it with ifconfig as wlan0.

Only problem now is that I get no results with sudo iwlist wlan0 scan :(

Any ideas?

---

### Post by sudodus on 2012-02-03
> **w0ss4g3 said:**
> Unfortunately I'm in the last year of my PhD and this is my office machine... I can't really afford to reinstall the OS at the moment - have spent a long time getting a lot of things set up!

The IT department handed me the USB cos they can't afford to route a cable through to the new office I've been put in. I've got the thing to get a blinking light now - bit better than before.. I can see it with ifconfig as wlan0.

Only problem now is that I get no results with sudo iwlist wlan0 scan :(

Any ideas?
I see.

Maybe you can explain to the IT dept guy that you need a USB device which is reported to work out of the box with linux, for example ***Zyxel G-202***.

If you can't get it, good luck tweaking :-)

---

### Post by w0ss4g3 on 2012-02-03
Guess that's what I'll have to do. Currently got wireless on my android phone and using usb tethering working so it'll do for now.. signal is even stronger than on the laptop I've been using lol

---

### Post by chili555 on 2012-02-03
Are you all set or would you like to continue to try to coax this to life?

---

### Post by w0ss4g3 on 2012-02-03
Well, if we can get it working then I'd be happy - not exactly perfect using a phone as a wireless card!

Tell me what to do.. :)

---

### Post by chili555 on 2012-02-03
How did rt2870sta get loaded? Did you just try it to see what happens? ...Nothing...? Do you have a Windows driver for it? ndiswrapper is probably our best shot, however, reading the Windows .inf file might be very helpful.

---

### Post by nikaein on 2012-02-04
I have exactly this problem. i use many version of drivers for dwa-125. i user 3070,3370,2870,5570 , ... from this site:
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

but, nothing happened :(

first, from where i can download proper driver?
second, does usb ID is important? my DWA-125 usb id is: "2001:3c19" like w0ss4g3, but threads like this:
[http://ubuntuforums.org/showthread.php?t=1862223](http://ubuntuforums.org/showthread.php?t=1862223)
have this ID: 07d1:3c0d

thanks.

---

### Post by nikaein on 2012-02-04
I found second question answer:
[http://www.wikidevi.com/wiki/D-Link_DWA-125_rev_A1](http://www.wikidevi.com/wiki/D-Link_DWA-125_rev_A1)
[http://www.wikidevi.com/wiki/D-Link_DWA-125_rev_A2](http://www.wikidevi.com/wiki/D-Link_DWA-125_rev_A2)
[http://www.wikidevi.com/wiki/D-Link_DWA-125_rev_A3](http://www.wikidevi.com/wiki/D-Link_DWA-125_rev_A3)

---

### Post by nikaein on 2012-02-04
I use 5370 from: (first link)
[http://ubuntuforums.org/showthread.php?t=1862223](http://ubuntuforums.org/showthread.php?t=1862223)
when i plug dwa-125, rt5370sta automatically appear in lsmod.
iwconfig returns:
```

ra0       Ralink STA
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

but "iwlist ra0 scan" returns:
ra0       Interface doesn't support scanning.

---

### Post by chili555 on 2012-02-04
> **nikaein said:**
> I use 5370 from: (first link)
[http://ubuntuforums.org/showthread.php?t=1862223](http://ubuntuforums.org/showthread.php?t=1862223)
when i plug dwa-125, rt5370sta automatically appear in lsmod.
iwconfig returns:
```

ra0       Ralink STA
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

but "iwlist ra0 scan" returns:
ra0       Interface doesn't support scanning.Did you make the needed changes in os/linux/config.mk? What does this tell us?```
dmesg | grep -e ra0 -e rt5
modinfo rt5370sta | grep 3C19
```

---

### Post by kurt18947 on 2012-02-04
Depending on your time and inclination, a few $ might supply a solution.  My experience is that 10.04 is a bit of a problem with 3 N150 wifi adapters I favor. They will all work but all need extra software/firmware/tweaks with Ubuntu earlier than 11.04.  I do have one that is G speed but has worked OOB for me since 9.04, perhaps earlier.
[http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=trendnet+tew-424ub&x=0&y=0]("http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=trendnet+tew-424ub&x=0&y=0")

This adapter works with on a live session so it's good for establishing a network connection prior to installing to a hard drive.  It sometimes seems a little sluggish but sometimes sluggish >> working flaky or not at all.

---

### Post by nikaein on 2012-02-04
on, i forgot do that :)

it is now corrected.

for those who don't know about config.mk:

change these lines:
HAS_WPA_SUPPLICANT=n
to
HAS_WPA_SUPPLICANT=y

and

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
to
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

thanks chili

p.s.: a complete howto:
1. lsusb | grep D-Link
if you have this: " 2001:3c19 D-Link Corp." continue.
2. download first driver: (RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB     09/30/2011     2.5.0.3)
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
```

bzip2 -d 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.tar.bz2
tar xf 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
cd 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux
vim config.mk

```change these lines:
HAS_WPA_SUPPLICANT=n
to
HAS_WPA_SUPPLICANT=y
and
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
to
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
save & quit
```

cd ../..
make
make install
iwconfig
iwlist ra0 scan

```

---

