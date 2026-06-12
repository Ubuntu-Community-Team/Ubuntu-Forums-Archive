---
title: "Belkin F5D8053 Help"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by ypeytonh on 2012-04-12
I'm trying to get my Belkin F5D8053 v3 adapter to work with Ubuntu 11.04.
Being a Mac (ex Windows) user, I find 11.04 easy to use and I feel right at home. I don't see what the fuss with Unity is but that's another topic. 
I already have a wireless card and it works. But I want to use the Belkin to get N connection speeds. I'm somewhat new to Ubuntu and would appreciate the wisdom of the experienced. :)
I've already tried several guides but none of them have worked.

I'm comfortable (not well experienced) with using the Terminal.

I've only got one USB port and no ethernet port.

I have a working wireless card but I'd rather blacklist the driver for it and just use the Belkin USB.

I've heard of ndiswrapper and none of the guides I've found have worked.

I have the driver disc.

I'm willing to work at this I just need some help. :)

Thanks!

---

### Post by chili555 on 2012-04-13
I believe the device is an rt2800usb device. I'm not too sure N speeds are or are not achievable in Ubuntu. I'd suggest we try first. Let's identify the device first. With the Belkin inserted, please run and post:```
lsusb
lsmod | grep rt2
arch
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.


----------
note to chili: Please see: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6121](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6121)

?? write a conf file ?? options mac80211 ieee80211_default_rc_algo=minstrel_ht

Test: cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo

---

### Post by ypeytonh on 2012-04-13
Thanks for your fast reply!

output of lsusb:
```
user@cr-48-ubuntu:~$ lsusb
Bus 005 Device 003: ID 0cf3:3005 Atheros Communications, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 001 Device 004: ID 04f2:b205 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1410:a014 Novatel Wireless 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@cr-48-ubuntu:~$ 
```

output of lsmod | grep rt2
```
user@cr-48-ubuntu:~$ lsmod | grep rt2
user@cr-48-ubuntu:~$
``` 

output of arch:
```
user@cr-48-ubuntu:~$ arch
i686
user@cr-48-ubuntu:~$
```

---

### Post by chili555 on 2012-04-13
While I finish up another project, let's see:```
modinfo rt2800usb | grep 815C
```If your device is supported, it should report back:```
modinfo rt2800usb | grep 815C
alias:          usb:v050Dp[COLOR="Red"]815C[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```If so, let's load rt2800usb and see what happens:```
sudo modprobe rt2800usb
iwconfig
```Be back in a few...

---

### Post by ypeytonh on 2012-04-13
```
user@cr-48-ubuntu:~$ modinfo rt2800usb | grep 815C
ERROR: modinfo: could not find module rt2800usb
user@cr-48-ubuntu:~$ 

```

I thought it was RT2870?

The module error is similar to the one I got trying to use ndiswrapper.

---

### Post by chili555 on 2012-04-13
> modinfo: could not find module rt2800usbWhaaa-a-a?? Please let me see:```
uname -r
sudo updatedb
locate rt2800usb.ko
modinfo rt2870sta | grep 815C
```updatedb will take a few moments; please be patient. This just gets curiouser!

---

### Post by ypeytonh on 2012-04-13
```
user@cr-48-ubuntu:~$ uname -r
3.0.13
user@cr-48-ubuntu:~$ 
```

```
user@cr-48-ubuntu:~$ sudo updatedb
[sudo] password for user: 
user@cr-48-ubuntu:~$ 
```

```
user@cr-48-ubuntu:~$ locate rt2800usb.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
user@cr-48-ubuntu:~$ 
```

```
user@cr-48-ubuntu:~$ modinfo rt2870sta | grep 815C
ERROR: modinfo: could not find module rt2870sta
user@cr-48-ubuntu:~$ 
```

---

### Post by chili555 on 2012-04-13
> user@cr-48-ubuntu:~$ uname -r
3.0.13
user@cr-48-ubuntu:~$Your intro asks about 11.04 and yet 3.0.13 is not an 11.04 linux-image. Did you install a custom or vanilla kernel? No wonder the drivers you need are absent. If you want to boot into 2.6.38-8 at the GRUB menu, I'm pretty sure your device will work straight away.

Why did you need a non-standard kernel? Surely not for wireless.

---

### Post by ypeytonh on 2012-04-13
This is why:
[http://chromeos-cr48.blogspot.com/2011/04/ubuntu-1104-for-cr-48-is-ready.html]("http://chromeos-cr48.blogspot.com/2011/04/ubuntu-1104-for-cr-48-is-ready.html")

I'm using a Cr-48.

---

### Post by chili555 on 2012-04-13
I can only assume that the kernel installed has been stripped of all the drivers, et al that don't support the hardware on the Acer and Samsung Chromebooks. I'm not sure we could even compile rt2800usb or rt2870sta from source, since we don't, as far as I can see, have matching linux-headers. We can re-try ndiswrapper or try to troubleshoot the built-in wireless card.

What is your preference? What happened with ndiswrapper?```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by ypeytonh on 2012-04-13
ndiswrapper gave me a fatal module error. And I'm not using a Samsung or Acer Chromebook. It's one of the original beta laptops. The current wireless card works. But I want to use the USB adapter.

---

### Post by ypeytonh on 2012-04-13
When I tried ndiswrapper before I got a module error but I'd be willing to try it again. The internal wireless card works. I'd just much rather connect to my network via the USB.

---

### Post by ypeytonh on 2012-04-13
When I tried ndiswrapper before I got a fatal module error but I'd be willing to try it again. The internal wireless card works. I'd just much rather connect to my network via the USB.

And I'm not using a Samsung or Acer Chromebook. It's one of the original beta laptops.

---

### Post by ypeytonh on 2012-04-14
I think if maybe I could flash a custom bios I could install a fresh version of Ubuntu.

---

### Post by chili555 on 2012-04-14
> **ypeytonh said:**
> I think if maybe I could flash a custom bios I could install a fresh version of Ubuntu.Possibly. I have no knowledge of your device and its BIOS.

What is the exact message?```
ndiswrapper -v
sudo modprobe ndiswrapper
```

---

### Post by ypeytonh on 2012-04-14
I opened up the computer, taped up the bios write block, and flashed some new bios(backing up the old ones of course I am now doing a fresh install of 11.10 downloaded straight from Ubuntu's site.
Maybe now we'll get somewhere! :)

---

### Post by chili555 on 2012-04-14
> I am now doing a fresh install of 11.10 downloaded straight from Ubuntu's site. Maybe now we'll get somewhere! I'm pretty certain we will! I'm anxiously awaiting your report.

---

### Post by ypeytonh on 2012-04-16
Sorry for the late response, I've been a little busy.

After a fresh install of 11.10 it worked out of the box! Thanks! It works so good I can even get a WPA handshake! :D

---

### Post by chili555 on 2012-04-16
Awesome! Glad it and 11.10 are working. Have fun!

---

