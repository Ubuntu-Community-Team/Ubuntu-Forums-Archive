---
title: "Power managment on awake from sleeping &amp; no wireless network connection"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by cpcpcp on 2012-04-13
Power management puts my machine to sleep, I press the button to wake it up and there is no network connection. I have clicked the network manager applet to no avail and restart refuses to work so it shut down with the power button and then turn it back on and all is fine.
How should it work?
Is there a simple fix?
Do I need to restart a daemon or something and if so what and how.

Lucid is my Ubuntu version

---

### Post by chili555 on 2012-04-14
It is often the case that your wireless driver unloads when you suspend. Let's find out what the driver is and write a file to see if we can fix it. Please open a terminal and do:```
sudo lshw -C network
```It takes a few moments, so please be patient. You should have a listing for wireless showing your driver. Here is an example from my system:> *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwlagn[/COLOR] driverversion=3.0.0-17-generic-pae firmware=9.221.4.1 build 25532 ip=192.168.1.108 latency=0 link=yes <snip>When you know your driver, then do:```
sudo gedit /etc/pm/config.d/config
```A new empty file will open. Put in:```
SUSPEND_MODULES="iwlagn"
```Of course, substitute your driver instead of iwlagn. Proofread carefully, save and close gedit. You should be all set.

This fix works most of the time but not always.

---

### Post by cpcpcp on 2012-04-14
my driver turned out to be 
ndiswrapper+rt2870
I have done as you suggested and I will know how it turns out tomorrow evening.

Thanks

---

### Post by chili555 on 2012-04-14
> my driver turned out to be ndiswrapper+rt2870Then I think you want:```
SUSPEND_MODULES="ndiswrapper"
```Usually, the native rt2800usb or rt2870sta can work just fine. If you'd like to try, post back and we'll see what we can do.

---

