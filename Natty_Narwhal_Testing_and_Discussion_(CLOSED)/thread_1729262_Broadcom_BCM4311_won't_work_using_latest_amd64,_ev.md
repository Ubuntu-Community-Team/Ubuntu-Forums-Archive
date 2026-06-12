---
title: "Broadcom BCM4311 won't work using latest amd64, even after drivers installed"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by youbuntu on 2011-04-14
I am using Natty Daily 13-04-2011 (2nd rev) on an HP DV6231eu, which has a Broadcom BCM4311 WiFi card. I installed Natty amd64, set the DVD to be the only repo, temporarily, installed the drivers, restarted and it says "installed" and the little icon is green, but not Wifi interface is found/available/up.

iwconfig shows wlan0 is absent.

Not a good start really - any ideas? (I'm aware it's a Beta, before anyone reminds me).

:) Thanks

---

### Post by theanswriz42 on 2011-04-14
Wifi is all sorts of b0rked in natty :(

---

### Post by youbuntu on 2011-04-14
> **theanswriz42 said:**
> Wifi is all sorts of b0rked in natty :(

I'm sure (I hope) they'll sort it :)

---

### Post by drs305 on 2011-04-14
I only have wireless in a 32-bit system, so I don't know if this will work for you or not.

I got mine working via a solution posted in the following bug report (see Post 5). You uninstall the STA driver and then "sudo apt-get install firmware-b43-installer b43-fwcutter".
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038")
I imagine it will be fixed, as Mark Shuttleworth indicated it's affecting him as well in a duplicate bug thread.

---

### Post by theanswriz42 on 2011-04-14
> **drs305 said:**
> I only have wireless in a 32-bit system, so I don't know if this will work for you or not.

I got mine working via a solution posted in the following bug report (see Post 5). You uninstall the STA driver and then "sudo apt-get install firmware-b43-installer b43-fwcutter".
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038")
I imagine it will be fixed, as Mark Shuttleworth indicated it's affecting him as well in a duplicate bug thread.

It's never good to break the boss man's system :D

---

### Post by TBABill on 2011-04-14
> **youbuntu said:**
> I am using Natty Daily 13-04-2011 (2nd rev) on an HP DV6231eu, which has a Broadcom BCM4311 WiFi card. I installed Natty amd64, set the DVD to be the only repo, temporarily, installed the drivers, restarted and it says "installed" and the little icon is green, but not Wifi interface is found/available/up.

iwconfig shows wlan0 is absent.

Not a good start really - any ideas? (I'm aware it's a Beta, before anyone reminds me).

:) Thanks

Instead of actually restarting, do the install of the driver but make the last step...```
sudo modprobe wl
``` and then connect to your wireless router. If you are using the b43 driver instead of the STA driver, use "b43" without quotes instead of "wl".

I just did this an hour ago for my fresh Natty install with a BCM4312 and the STA driver.

---

### Post by nm_geo on 2011-04-14
> **TBABill said:**
> Instead of actually restarting, do the install of the driver but make the last step...```
sudo modprobe wl
``` and then connect to your wireless router. If you are using the b43 driver instead of the STA driver, use "b43" without quotes instead of "wl".

I just did this an hour ago for my fresh Natty install with a BCM4312 and the STA driver.

TBABill what kernel are you running? I have been running the B43 but thought above trying the STA driver again at least on one of my Natty Installs.

---

### Post by TBABill on 2011-04-15
I am not on my machine now, but it's whatever kernel is in Natty Beta 2. My BCM4312 is not supported by the b43 so I always use the wl instead.

---

### Post by rarsa on 2011-04-17
Having the same problem with the BCM4311 using the 64 bit version of Natty Narwal on a HP dv6105us

The STA driver is installed and "green"

lsmod shows the wl driver running

```
# lsmod | grep wl
wl                   2568244  0 
lib80211               14991  1 wl

```

After unloading the driver and reloading it, this is what dmesg shows:

```
[  513.765832] wl 0000:03:00.0: setting latency timer to 64
[  513.769128] malloc in abgphy done
[  513.769319] eth%d: 5.100.82.38 driver failed with code 21

```

I finally removed the STA driver and used the B43 as described in this link and it is now working:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677/comments/10](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677/comments/10)

---

### Post by landon418 on 2011-04-17
> **drs305 said:**
> I only have wireless in a 32-bit system, so I don't know if this will work for you or not.

I got mine working via a solution posted in the following bug report (see Post 5). You uninstall the STA driver and then "sudo apt-get install firmware-b43-installer b43-fwcutter".
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038")
I imagine it will be fixed, as Mark Shuttleworth indicated it's affecting him as well in a duplicate bug thread.

Thanks you so much!:popcorn:

---

