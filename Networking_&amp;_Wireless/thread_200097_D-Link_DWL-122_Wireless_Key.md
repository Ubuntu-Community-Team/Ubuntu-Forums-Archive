---
title: "D-Link DWL-122 Wireless Key"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by evanseeds on 2006-06-19
I installed Ubuntu today on my 567 MHz Celeron IBM box, and my wireless key doesn't work. I'm a relative newbie to Linux, having run FC1 for a little bit, but not doing much with it. The solutions i've found via searching have not helped me at all. I tried installing linux-wlan-ng through apt-get install, and it says the package cannot be found. I tried compiling it manually (by downloading it on this computer and saving it to a floppy), but when i ./configure it, it says "Linux source tree /lib/module/2.6.15-23-386/build is incomplete or missing". I'm at a loss for what to do, so any help would be appreciated.

---

### Post by Joeb on 2006-06-19
I just checked in synaptic and linux-wlan-ng shows up (I told it to search for wlan).  Is it possible you had a typo when you tried the apt-get?  Anyway, fire up synaptic and install it from there.  It should install and the description states that the standard Ubuntu kernel already contains the necessary drivers (ie the package contains utilities and scripts to use the drivers).

---

### Post by az on 2006-06-19
[QUOTE=evanseeds]I installed Ubuntu today on my 567 MHz Celeron IBM box, and my wireless key doesn't work. I'm a relative newbie to Linux, having run FC1 for a little bit, but not doing much with it. The solutions i've found via searching have not helped me at all. I tried installing linux-wlan-ng through apt-get install, and it says the package cannot be found. I tried compiling it manually (by downloading it on this computer and saving it to a floppy), but when i ./configure it, it says "Linux source tree /lib/module/2.6.15-23-386/build is incomplete or missing". I'm at a loss for what to do, so any help would be appreciated.[/QUOTE]
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)
If you installed using the Desktop cd, you have to do an extra step to get the extra packages on there recognised....

---

### Post by evanseeds on 2006-06-19
I've installed the package successfully, but I'm not sure what to do next...

---

### Post by az on 2006-06-20
[QUOTE=evanseeds]I've installed the package successfully, but I'm not sure what to do next...[/QUOTE]

As it says on the page:
Open up the file /etc/network/interfaces in your favorite text editor. Add the following lines to it (replace your_essid and xx:xx:xx:xx:xx with your network name and WEP key):

auto wlan0 # Remove or comment out if you don't want it to start at boot

iface wlan0 inet dhcp # If you want dhcp for wireless. Otherwise replace "dhcp" by "static" and see "man interfaces"
     wireless_mode managed
     wireless_essid your_essid
# Comment out the lines below if you don't have wireless encryption. See /usr/share/doc/linux-wlan-ng/README.Debian
     wireless_enc on
     wlan_ng_key0 xx:xx:xx:xx:xx
     wlan_ng_authtype opensystem




You have to do that because the card driver uses a different configuration that all the other wireless drivers in linux.

---

