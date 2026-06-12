---
title: "Can't compile rt61 on karmic"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by PHaLaNX on 2009-11-09
Hi,

I'm trying to compile the serialmonkey rt61 driver, it compiled fine on jaunty, but now it just doesn't work anymore. 

```

$ make                                                 
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'                                        
  Building modules, stage 2.                                                                                  
  MODPOST 0 modules                                                                                           
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'                                         
rt61.ko failed to build!                                                                                      
make: *** [module] Error 1
```

I have linux-source, kernel headers and build essential. Don't know why this happens. 

Can anyone help?

Thanks...

---

### Post by HBK008 on 2009-11-09
Same problem here. Just installed Ubuntu, although I do have some previous experience. Maybe a problem with the makefile??

---

### Post by PHaLaNX on 2009-11-10
Can it be that it isn't suitable for this new kernel?

Anyone?

---

### Post by chili555 on 2009-11-10
> Can it be that it isn't suitable for this new kernel?Probably. 

I noticed this on serialmonkey's download page:> Rt2x00 drivers are part of the mainline kernel tree.
This is true since January 2008 with the 2.6.24 kernel, and several distributions are already shipping the driver.
While the mainline kernel has the driver tree, it is not the latest version.
The development tree, for several reasons, can only be pulled along with the full kernel sources using the git content tracker.Is the built-in *rt61pci* not working correctly for you?

---

### Post by PHaLaNX on 2009-11-10
It does but the serialmonkey one had monitor mode support while built-in module didn't, which can be useful sometimes. I didn't check rt61pci on karmic though, but monitor mode doesn't work on it if I'm not wrong.

(I deleted the rt61pci.ko accidentally before trying it. I didn't think compiling rt61 would fail.)

---

### Post by dj_deef on 2009-11-23
look that rt61pci (that built with kernel) **has** monitor mode and injection support, rt61 (by Ralink) **has not!**

---

### Post by hugo1967 on 2009-12-17
I've had the same experience - in the past, the only driver that seemed to work for me was the rt61 latest build from Serialmonkey.  In Karmic, I think the drivers reside in different directories, so even if the serialmonkey driver *could*compile correctly, it *won't*because the makefile points to a nonexistent directory.

However, I've found that the rt61pci driver supplied with karmic seems to work just fine out of the box.  Connection almost never drops,  transmission strength and speed are just as good as ever.  I've also gotten WPA2 to work.  I edited  /etc/networking/interfaces and added the following lines

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid "mynetwork"
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 01234567890123456789

Some of these will depend on your router settings.  After making these edits, and making sure that rt61pci module was active (try 'depmod rt61pci') I entered 

sudo /etc/init.d/networking restart

And voila!  Here I am submitting a forum post!

---

