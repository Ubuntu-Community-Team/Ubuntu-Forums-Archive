---
title: "Huawei E1762 unable to connect"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by littlemog on 2009-09-21
Hi,

I've been reading up a bit before I thought I'll post. I'm running Ubuntu  Jaunty Netbook R on EEEPC and I have a Huawei 3G dongle that's issued by my company (E1762). I've tried the usb modeswitch thread but it didn't work. 

Another thread suggest using a USB sniffer on windows to get the vendor id and make but unfortunately, I don't have windows. Has anyone managed to find a fix around this? I have wireless at home which works perfectly but sometimes it's good to be able too connect using 3G when I'm outside. :(

Any solutions or ideas would be great.

Kenny

---

### Post by nurazizah on 2010-01-15
Hi, I know this is an old post, but when I was looking for a solution for this, I found a lot of unanswered posts so I'm posting this anyway for those who might be looking for it.

I'm using Ubuntu Remix - Karmic Koala


To make E1762 work, first install modeswitch

```
sudo apt-get install usb-modeswitch
```

Then, edit /etc/usb_modeswitch.conf
(where I got this solution - unfortunately the page is not available anymore - the writer advised not to use gedit, but I forgot what else is available, so I used gedit anyway. You just have to be careful with the quotation marks)

```
sudo gedit /etc/usb_modeswitch
```

from:
```
########################################################
# Huawei E220 (aka "Vodafone EasyBox II", aka "T-Mobile wnw Box Micro")
# Huawei E230
# Huawei E270
# Huawei E870
# and probably most other Huawei devices (just adapt product ID)
#
# Two options: 1. removal of "usb-storage"  2. the special control
# message found by Miroslav Bobovsky
#
# Contributor: Hans Kurent, Denis Sutter, Vincent Teoh

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1003

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

```

to:
```
########################################################
# Huawei E220 (aka "Vodafone EasyBox II", aka "T-Mobile wnw Box Micro")
# Huawei E230
# Huawei E270
# Huawei E870
# and probably most other Huawei devices (just adapt product ID)
#
# Two options: 1. removal of "usb-storage"  2. the special control
# message found by Miroslav Bobovsky
#
# Contributor: Hans Kurent, Denis Sutter, Vincent Teoh

DefaultVendor=  0x12d1
;DefaultProduct= 0x1003
DefaultProduct= 0x1446

TargetVendor= 0x12d1
;TargetProduct= 0x1003
TargetProduct= 0x1446

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

MessageEndpoint=0x01
MessageContent= "55534243000000000000000000000011060000000000000000000000000000"

```

Then create this file:
```
sudo gedit /etc/udev/rules.d/15-huawei-e1762.rules

```

and insert this in it:
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"
```

Create your connection with network manager, restart you computer and it's done!

Hope this helps someone.

---

### Post by pdc on 2010-01-15
Hi nurazizah;

intrigued where you got this from;

if you go to the current usb_modeswitch.conf file, 

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf)

their section now says

> # Huawei E220 (aka "Vodafone EasyBox II", aka "T-Mobile wnw Box Micro")
# Huawei E230
# Huawei E270
# Huawei E870
# and probably most other Huawei devices (just adapt product ID)
#
# Two options: 1. removal of "usb-storage"  2. the special control
# message found by Miroslav Bobovsky
#
# Contributor: Hans Kurent, Denis Sutter, Vincent Teoh

;DefaultVendor=  0x12d1;
;DefaultProduct= 0x1003

;TargetClass=    0xff

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

when you quote

> MessageContent= "55534243000000000000000000000011060000000000000000000000000000"


none of the Huawei modems have that message content

> 55534243

starts as a prefix for several of the ZTE modems

so curious how it all pans out 

there is a debian version of usb_modeswitch, that is 1.0.5 I think .. that autoconfigures

and the latest is 1.0.7 and it is tar.gz I think

(what one gets from sudo apt-get is an older version)

(The usb_modeswitch doesn't list this modem as working, but if your fix works, great!)

and it looks like 

[http://forums.vr-zone.com/notebooks-netbooks-garage/456136-huawei-e1762-mobile-broadband-modem.html](http://forums.vr-zone.com/notebooks-netbooks-garage/456136-huawei-e1762-mobile-broadband-modem.html)

this modem is described as a "newer model than E169" I think the product ID of the E169 is 1001

---

