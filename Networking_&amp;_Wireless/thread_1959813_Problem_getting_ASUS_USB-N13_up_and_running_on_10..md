---
title: "Problem getting ASUS USB-N13 up and running on 10.04"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by malaTG on 2012-04-16
Hi everyone,

I have now tried for a while (Reading a lot of threads on the forum to get my new usb wireless adapter up and running. I have tried so many different things I am afraid that it is a mix of different solutions. ANY suggestions on how to proceed (Other than upgrading Ubuntu) would be much appreciated. 

I have done the following

- Downloaded the latest driver from Asus 

filename:       /lib/modules/2.6.32-40-generic-pae/kernel/drivers/net/wireless/rt3070sta.ko
version:        2.3.0.2
license:        GPL
description:    RT2870 Wireless Lan Linux Driver

- Compiled and installed it

- Added the following line in
  /etc/modprobe.d/network_drivers.conf

```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 17ab" > /sys/bus/usb/drivers/rt2870/new_id
```

- Added the following line in
  /etc/udev/rules.d/network_drivers.rules

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="17ab", RUN+="/sbin/modprobe -qba rt3070sta"
```

- Added the following line in the end of the file
  /etc/modprobe.d/blacklist.conf

  ```
blacklist rt2870sta
```

However when I reboot I still see that the module rt2870sta is loaded (using lsmod). If I unload rt2870sta and load rt3070sta it still doesn't work.

Here is what I see in dmesg

```

[   90.748431] usbcore: deregistering interface driver rt2870
[   90.748477] <--- rtusb exit
[   98.731352] rtusb init --->
[   98.731412] usbcore: registered new interface driver rt2870
```

Here is what lsusb gives me

```
Bus 002 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 

```

Thank you in advance!

/Marcus

---

### Post by chili555 on 2012-04-16
What do you think about this? [http://cateee.net/lkddb/web-lkddb/RTLWIFI.html](http://cateee.net/lkddb/web-lkddb/RTLWIFI.html)> lkddb usb 0b05 17ab .. .. .. .. .. .. 0000 ffff : CONFIG_RTL8192CU CONFIG_RTLWIFI CONFIG_WLAN : drivers/net/wireless/rtlwifi/[COLOR="Red"]rtl8192cu[/COLOR]/sw.cIn other words, neither rt2870sta nor rt3070sta are correct for your device.

I suggest you remove all the files you referenced above. Also see if there is an entry in /etc/modules referencing either rt2870sta or rt3070sta and remove it. Then I'd look for *rtl8192cu.ko* on your system. We can udev it to recognize your device, if it's there.

---

### Post by malaTG on 2012-04-16
Hi,

Thank you for answering!

I have cleared out the system from all my configuration as suggested. 

I also searched for the "rtl8192cu.ko" file throughout the system. Unfortunately I couldn't find it. 

What would be your suggested approach from here? Do I need to upgrade to get on an higher kernel version?

/Marcus

---

### Post by chili555 on 2012-04-16
Rats! I was afraid you'd ask that. I almost had a clean getaway.

You might review this: [http://ubuntuforums.org/showthread.php?t=1949810&highlight=rtl8192cu](http://ubuntuforums.org/showthread.php?t=1949810&highlight=rtl8192cu)

Note that they are talking about the *built-in* and furthermore:> Well, the point of this thread is not to tell people, "Hey, the built in driver is broken, get one from realtek". I know you can do that, in fact, I've been using the device with Lucid for months. My first preference would be to check Realtek's site for a version that covers your kernel version: 2.6.32-40-generic-pae. Download it and we'll check for your device in dev_id.c or similar and add it if it's not there. Compile it and I'm fairly certain it will work well.

---

### Post by malaTG on 2012-04-16
Hi,

I followed your advice and downloaded the correct driver from 

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

With it it actually came a install script :-) which compiled it for me.

Now it is working :-) Thank you for pointing me in the right direction. I could have spent many hours before realizing my mistake! :-)

/Marcus

---

### Post by chili555 on 2012-04-16
OR...you could try this: [http://ubuntuforums.org/showthread.php?p=11716409](http://ubuntuforums.org/showthread.php?p=11716409)

---

### Post by chili555 on 2012-04-16
> Now it is working Thank you for pointing me in the right direction. I could have spent many hours before realizing my mistake! Awesome! Glad it's working.

There are two versions of USB-N13; the Ralink 2870 and the Realtek 8192. All you searchers need to go by the usb.id; for example 0b05:17ab, rather than the model or brand. The usb.id is everything. Google is your and my best friend.

---

