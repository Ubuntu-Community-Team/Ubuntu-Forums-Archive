---
title: "jan.7 updates killed my bcm43xx wifi, fixed"
date: 2011-01-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by inportb on 2011-01-08
When I found that my wifi was no longer working, I poked around a bit:

[QUOTE=dmesg]fail to load firmware brcm/bcm43xx-0.fw[/QUOTE]

Okay, so some file's apparently missing... but **/lib/firmware/brcm** has a bunch of **bcm43xx*** files. For giggles, I made a couple of symlinks:

```
cd /lib/firmware/brcm
sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fw
sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw
```

It started working again after a reboot. More precisely, it should have been sufficient to reload **brcm80211**.

---

### Post by joffe on 2011-01-08
Thanks man, saved my week-end from digging into driver compiling...

---

### Post by cariboo on 2011-01-08
My system needs the wl driver, as I can connect with the b43 driver with your fix, but it disconnects and won't reconnect, no matter what I do.

---

### Post by inportb on 2011-01-10
I also noticed my wireless breaking randomly after establishing a connection and operating normally for a time. I am able to reconnect, however, and it only happened with two driver releases.

But now, after updating **bcmwl-kernel-source** again, I see that the driver loads fine but I am unable to use the interface...

[QUOTE=iwlist scan]wlan0     Failed to read scan data : Network is down[/QUOTE][QUOTE=rfkill list]
0: ideapad_wlan: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: ideapad_killsw: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no[/QUOTE][QUOTE=lshw -C Network]  *-network DISABLED
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       logical name: wlan0
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.37-12-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn[/QUOTE]

Oops! The hardware switch is functional, but it looks like something's up on the software side.

Since you mentioned **wl**, I thought there might be a conflict. Indeed,

[QUOTE=lsmod]Module                  Size  Used by
wl                   2646666  0
brcm80211             690942  0[/QUOTE]

At the end, I was able to get **wlan0** scanning again by loading only **wl** (**brcm80211** does not work, interestingly):

```
modprobe -r wl
modprobe -r brcm80211
modprobe wl
```

What is this **wl** driver? I thought it was mainly a binary blob? Perhaps you also have a conflict of some sort.

---

### Post by cariboo on 2011-01-10
Alberto released a fix for the bcmwl-kernel-source package, I installed the fixed package and have wireless again.

> What is this wl driver? I thought it was mainly a binary blob? Perhaps you also have a conflict of some sort.

Some versions of the bcm4312 chipsets need the wl driver, mine won't make a reliable connection without it. With the b43 driver I could make a connection, but it would ranodmly drop and reconnect again. With the wl driver I get a solid  2mbps connection.

---

### Post by inportb on 2011-01-11
(grr double-post. please ignore/remove this, thanks >_>)

---

### Post by inportb on 2011-01-11
Ah, okay. I found that I was able to get wireless functionality by blacklisting either **brcm80211** or **wl**. I just blacklisted **wl**.

---

