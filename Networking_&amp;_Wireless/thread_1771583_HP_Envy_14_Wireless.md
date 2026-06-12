---
title: "HP Envy 14 Wireless"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by mevans2802 on 2011-05-30
Hi,

I have installed Ubuntu 11.04 on my new HP Envy 14 and it recognised the BCM43224 wireless adapter and installed the Broadcom STA driver automatically. However network manager seems to be struggling setting up the device:

```
mike-hpenvy NetworkManager[2870]: <error> [1306751173.662976] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 6)
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): now managed
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): device state change: 1 -> 2 (reason 2)
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): bringing up device.
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): preparing device.
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth1): deactivating device (reason: 2).
May 30 11:26:13 mike-hpenvy NetworkManager[2870]: <info> (eth0): device state change: 2 -> 3 (reason 0)
```

I have tried re-installing these drivers and also compiling from source with no luck. I have scoured the web for answers but most people seem to have managed to get this card working fine with those drivers.

Any help would be much appreciated.

---

### Post by chili555 on 2011-05-31
I know I will live to regret the answer, but please post:```
rfkill list all
```Tell us about your wireless switch and the LED not changing and I'll get a few aspirin.

--------------
Hint to chili: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
> WHAT'S NEW IN RELEASE 5.100.82.38
---------------------------------
+ Support for bcm43227 and bcm43228
+ Fix for issue where iwconfig was sometime reporting rate incorrectly
+ Supports rfkill in kernels 2.6.31 to 2.6.36
+ Supports scan complete event (SIOCGIWSCAN)
+ Adds EAGAIN (busy signal) to query of scan results
Is rfkill supported in 2.6.***38***???

---

### Post by mevans2802 on 2011-05-31
Hi,

Pretty sure it isn't the switch:

```
mike@mike-hpenvy:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Cheers

---

### Post by chili555 on 2011-05-31
Awesome! I feel better already. Does it scan?```
sudo iwlist eth1 scan
```When you click the Network Manager icon, does it try to connect? Are you asked for your encryption password?

---

### Post by mevans2802 on 2011-05-31
It scans with iwlist, but Network Manager doesn't seem to acknowledge it - there's no wireless icon.

---

### Post by chili555 on 2011-05-31
> there's no wireless icon.Meaning what? Do you mean you can't find a Network Manager icon to click, or do you mean you can find it and click it but it shows no networks. Please see attached.

---

### Post by mevans2802 on 2011-05-31
There's no icon to click on.

---

### Post by chili555 on 2011-05-31
Cool! It's an actual known bug: [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/746495](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/746495)

It appears the bug is fixed by updating several packages, libappindicator and gtk+2.0. Can you hook up an ethernet cable, get a connection and do:```
sudo apt-get update && sudo apt-get upgrade
```Also, tell me if there is any improvement if you do:```
nm-applet &
```You may have to leave that terminal open if the icon appears.

---

### Post by mevans2802 on 2011-05-31
Still no icon after upgrading. Also, manually running nm-applet makes no difference. Starting to wonder whether it's worth downgrading to 10!

Cheers

---

### Post by mevans2802 on 2011-05-31
Still no icon after upgrading. Also, manually running nm-applet makes no difference.

Cheers

---

### Post by chili555 on 2011-05-31
Can you confirm that Network Manager is actually installed? Please open Applications > Synaptic and search for Network Manager. Does it have a little green box indicating it is installed?

---

### Post by mevans2802 on 2011-05-31
I can confirm Network Manager is indeed installed.

---

### Post by chili555 on 2011-05-31
If you run, without the ampersand:```
nm-applet
```Are there any errors, warnings, interesting messages, smoke, sparks or anything that helps us??

[http://janetalkstech.com/network-manager-applet-crashes-periodically-in-ubunty-11-04-natty-narwhal](http://janetalkstech.com/network-manager-applet-crashes-periodically-in-ubunty-11-04-natty-narwhal)

Are you running the new whiz-bang Unity desktop?

---

### Post by mevans2802 on 2011-05-31
Initially I get:
```

An instance of nm-applet is already running.

** (nm-applet:4290): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

If I kill the process and re-try I get:
```

DEBUG: old state indicates that this was not a disconnect 0

```
as in the link you posted.

I am running Unity.

---

### Post by chili555 on 2011-05-31
Use the workplace switcher and see if it has become lost on another desktop. Also try:```
sudo /etc/init.d/network-manager restart
```If neither of those do it, I suggest you log out and select Classic Ubuntu and log back in. Is the applet visible there? Can you right-click the panel and add Notification Area?

I am running low on ideas.

---

### Post by mevans2802 on 2011-05-31
No luck in classic. 

I'll keep trying and arm myself with a long ethernet cable in the mean time. Thanks a lot for your help.

---

