---
title: "Newbie Alert--new USB WiFi adapter"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by walt.smith1960 on 2010-03-08
I guess I'm a glutton for punishment, or just ignorant:). I purchased a device labeled "EnGenius". It uses a RaLink RT3572 chip and claims to be Linux compatible.  My OS is Karmic 32 bit desktop with updates installed. I first simply rebooted and plugged it in. No signs of life. I then downloaded the Linux driver from Ralink's web site and made the changes recommended in the various files.

[LIST]
[*]changed the device I.D. to 0x1740,0x9801 per lsusb's result. the manufacturer's name comes up Senao. There was an entry in "common/rtusb_dev_id.c" labeled "egenius" so I changed the I.D. #'s but didn't change the name from "engenius" to "senao" Should I have?
[/LIST]

[LIST]
[*]I made the changes in "os/linux/config.mk as recommended re WPA supplicants.
[/LIST]
I did the compile steps and they seemed to complete successfully. 

I edited the /etc/modules file and added "rt3572STA.ko" and saved and restarted. Still no blue light. The device does work under WinXP so it's not a dead device, I think. I thought about trying NDISwrapper but the windows install is an executable file. I don't know how to get the *.inf & *.sys files required to try NDISwrapper. I'll attach the contents of lsusb, iwconf and lsmod.

I'll welcome any thoughts on this device. I've read the other Ralink files and tried to make sense of them.  This is my first effort at compiling a driver so be nice :redface:

[ATTACH]149400[/ATTACH]

[ATTACH]149401[/ATTACH]

[ATTACH]149402[/ATTACH]

---

### Post by chili555 on 2010-03-08
The module *rt2800usb* is supposed to drive your device:> $ modinfo rt2800usb | grep 9801
alias:          usb:v[COLOR="Blue"]1740[/COLOR]p[COLOR="Blue"]9801[/COLOR]d*dc*dsc*dp*ic*isc*ip*Does it spring to life if you do:```
sudo modprobe rt2800usb
```If not, may we see:```
dmesg | grep rt2
```In your iwconfig, isn't ra0 your device's interface? Are networks available if you click the Network Manager icon?

---

### Post by walt.smith1960 on 2010-03-09
Hi Chili555 and thanks for your help. I tried "sudo modprobe 2800usb" and nothing. I had all the rt* entries blacklisted in /etc/modprobe.d/blacklist.conf". I removed all the entries there, rebooted and tried again. Still no luck. There were some entries when I typed lsmod. I'll attach that as "lsmod2." I'll also attach the results of dmsg as dmesg_rt2" Fortunately I have a TrendNet UB424v3.1 which works natively so I'm not totally out of luck. I'd just like to get the EnGenius device to work.

[ATTACH]149487[/ATTACH]

[ATTACH]149488[/ATTACH]

---

### Post by chili555 on 2010-03-09
Let's try a different approach. Please blacklist rt3572sta. Remove the device and reinsert it. Then please let me see all of:```
iwconfig
```Please obscure the MAC address. Thanks.> I have a TrendNet UB424v3.1It's not a Realtek rt2xx device is it?

I think your *lsmod* errors are probably because *both* rt3572sta *and* rt2800usb are loading.

---

### Post by walt.smith1960 on 2010-03-09
No joy on that. The WiFi USB device that works shows up as a RealTek RTL8187B. I unplugged that then restarted and plugged in the problem child. Attached are the outputs. It seems with rt3572 blacklisted the new device doesn't show up at all under iwconfig. 

[ATTACH]149497[/ATTACH]

[ATTACH]149498[/ATTACH]

Do I just need to experiment with blacklist various drivers and see if there's a combination that works?  Remove the rt3572STA completely?  At least with rt3572 enabled and all the rt* modules blacklisted the device would show up under iwconfig as  ra0  Ralink STA. It didn't show up in network manager and the blue light didn't come on but it did appear in iwconfig.

Thanks for staying with me.

---

### Post by chili555 on 2010-03-09
Please leave rt3572sta blacklisted and do:```
sudo modprobe rt2800usb
dmesg | grep rt2
```Can't you copy and paste from the terminal instead of screenshots?

---

### Post by walt.smith1960 on 2010-03-09
> **chili555 said:**
> Please leave rt3572sta blacklisted and do:```
sudo modprobe rt2800usb
dmesg | grep rt2
```Can't you copy and paste from the terminal instead of screenshots?

I've tried highlighting text in the terminal but ctrl-c (copy) and ctrl-v (paste) don't seem to work. Did I mention I'm a newb?:redface:

---

### Post by chili555 on 2010-03-09
Left-click and drag your cursor over it and select 'Copy.'

---

