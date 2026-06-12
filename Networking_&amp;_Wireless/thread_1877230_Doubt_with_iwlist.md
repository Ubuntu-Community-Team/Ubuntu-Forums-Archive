---
title: "Doubt with iwlist"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by ProDG_Yodha on 2011-11-07
Hi,

I uninstalled NM and use modprobe to switch on the WiFi. lsmod shows that WiFi module is loaded but iwlist shows nothing. So I did a sudo iwlist and it works. I wanted to know what is happening behind, when I do a sudo iwlist or in short, is there something that I can do to bypass the sudo?

Thanks

---

### Post by chili555 on 2011-11-07
I assume you mean iwlist scan. From *man iwlist*:> Triggering scanning is a privileged operation (root only) and normal users can only read left-over scan results. By default, the way scanning is done (the scope of the scan) is dependant on the card and card settings.Why do you need to bypass sudo?

---

### Post by ProDG_Yodha on 2011-11-07
I am trying to reduce the time taken to scan. If I do a iwlist after I do sudo iwlist, I can see every node. But, the sudo iwlist takes ~2 secs while the normal iwlist takes only 20ms. 

I don't know how I missed that sentence in the manual. 
Anyways, thanks a lot. I guess the only way to do it would be to hack the driver for the WiFi card.

---

### Post by chili555 on 2011-11-07
> I guess the only way to do it would be to hack the driver for the WiFi card.In order to do what? Connect automatically to any available network, insecure or not? What are you attempting to do? What is the wireless driver in question?

---

### Post by ProDG_Yodha on 2011-11-08
I am trying to switch the WiFi on and off and connect to the network automatically for work and home scenarios. At work I have different AP's, and I move around, so a little war-"walking" and connecting. 
Edit:
Wireless module is r8712u.

---

### Post by chili555 on 2011-11-08
> At work I have different AP's, and I move around,And the APs have the same SSID, too, I'd guess. A nightmare scenario...

There are several parameters available to be loaded in the r8712u module and none of them look helpful to me:> parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)I would have been happier to see a parameter like this from *ipw2200*:> parm:           associate:auto associate when scanning (default off) (int)I assume you are doing this manually, that is, without Network Manager. Looking at *man interfaces*, it looks like you could alias the most used APs, perhaps wlan0-home, wlan0-work1, wlan0-work2 and then manually configure the lesser-used networks. I have never done so myself, so I can't help much:```
The file consists of zero or more "iface", "mapping", "auto", "allow-" and "source"  stan&#8208;
       zas. Here is an example.
       auto lo eth0
       allow-hotplug eth1

       iface lo inet loopback

       source interfaces.d/machine-dependent

       mapping eth0
            script /usr/local/sbin/map-scheme
            map HOME eth0-home
            map WORK eth0-work

       iface eth0-home inet static
            address 192.168.1.1
            netmask 255.255.255.0
            up flush-mail

       iface eth0-work inet dhcp

       iface eth1 inet dhcp

etc., etc.	
```Finally, this looks promising: [http://ubuntuforums.org/showthread.php?t=1238387&highlight=map-scheme](http://ubuntuforums.org/showthread.php?t=1238387&highlight=map-scheme)

---

