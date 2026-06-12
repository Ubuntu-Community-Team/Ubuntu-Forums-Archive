---
title: "Three Huawei E353 Modem (UK)"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by percebeiro on 2011-07-16
Hi!
Somebody have this dongle working in Ubuntu 11.04?.
I cant do it. I cant find the driver for it.
I have a new network cnnection in manager connections->mobilebroadband but I&#7743; affraid that system doesn suupport the model of this modem.
Somebody can help me?
Thanks!

---

### Post by ieee488 on 2011-07-16
Plug the device in, then boot up your PC.

Then try to connect.

You won't know if you don't try.

---

### Post by tvboxspy on 2011-07-21
I have got this working on 10.10 and 11.04

[http://ubuntuforums.org/showthread.php?t=1799524](http://ubuntuforums.org/showthread.php?t=1799524)

---

### Post by mikeh007 on 2011-08-20
**tvboxspy**   -  that's great news,   but I'm running 10.04,  and am a linux newbie.   Could you possibly advise how to install it for 10.04 ?     Would be much appreciated

Mike, London

---

### Post by spiky001 on 2011-08-20
Have you tried network manager and setting it up in there,

---

### Post by ubuntu_cork on 2011-10-01
Hiya I am on Lucid (10.04)LTS and can't seem to see where I get it to work either, I installed the natty backported kernel 2.6.38 from the kernel-ppa team thinking that might help, but alas no.  IT Does work fine in 11.04 but my gf and I use 10.04 on our laptops so we need it working there.

Just where to start looking is the problem :(

---

### Post by alexfish on 2011-10-02
> **ubuntu_cork said:**
> Hiya I am on Lucid (10.04)LTS and can't seem to see where I get it to work either, I installed the natty backported kernel 2.6.38 from the kernel-ppa team thinking that might help, but alas no. IT Does work fine in 11.04 but my gf and I use 10.04 on our laptops so we need it working there.
 
Just where to start looking is the problem :(
 
the device should switch if the usb_modeswitch data has the device id's please visit the usb_modeswitch site , they also have a forum
 
but will then need to check which driver module is required for the device , looks as if this could be the option module,
 
to check if the device is listed (in switched mode)
```
modinfo option
```if the device is not listed
will have to send the device ids to the option new_id (could try the latest usb_modeswitch ) see if it configures the option module for the device
 
have always found sakis3g useful for configuring new devices , use in combination with the latest modeswitch data , sakis3g will
use the etc/usb_modeswitch.d files and should load a suitable driver,, not the latest debian tar files,
 
**[[SIZE=1]Draisberghof - Software - [B]USB_ModeSwitch**[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/")[/B]


**[[SIZE=1][B]Sakis3G** - All-in-one [/SIZE]]("http://www.sakis3g.org/")[/B]
 
 
regards
 
alexfish

---

### Post by linufanss on 2011-10-13
> **percebeiro said:**
> Hi!
Somebody have this dongle working in Ubuntu 11.04?.
I cant do it. I cant find the driver for it.
I have a new network cnnection in manager connections->mobilebroadband but I&#7743; affraid that system doesn suupport the model of this modem.
Somebody can help me?
Thanks!
The E353 really supports the ubuntu OS as well.
Get a new unlocked [URL="http://ubuntuforums.org/> **percebeiro said:**
> Hi%21%20Somebody%20have%20this%20dongle%20working%20in%20Ubuntu%2011.04?.%20I%20cant%20do%20it.%20I%20cant%20find%20the%20driver%20for%20it.%20I%20have%20a%20new%20network%20cnnection%20in%20manager%20connections-%3Emobilebroadband%20but%20I%C3%A1%C2%B8%C2%BF%20affraid%20that%20system%20doesn%20suupport%20the%20model%20of%20this%20modem.%20Somebody%20can%20help%20me?%20Thanks%21%20The%20E353%20really%20supports%20the%20ubuntu%20OS%20Get%20a%20new%20unlocked%20e353%20dongle%20may%20solve%20this%20problem%20Source:%20http://www.mobile2wifi.co.uk/index.php?main_page=product_info&cPath=2&products_id=27"]e353[/URL] dongle may solve this problem

---

### Post by tom7 on 2012-01-24
E353 works on Ubuntu 10.04 if you first go to Ubuntu Software Centre and install usb-modeswitch.

---

### Post by agestrada on 2012-02-03
> **spiky001 said:**
> Have you tried network manager and setting it up in there,

This worked for me. In 11.04 go to Network Connections:Mobile Broadband and Add a new connection. Choose UK, Three, etc... It connects once you finish the setup.

---

### Post by Fr Tod Umptious on 2012-06-11
> **tom7 said:**
> E353 works on Ubuntu 10.04 if you first go to Ubuntu Software Centre and install usb-modeswitch.

Hi 
Good to hear that you have the e353 working on 10.04, I am tearing my hair out over it.

Which version of usb_modeswitch do you have it working with ?

I have installed the following to no avail

usb-modeswitch 1.1.4-1
usb_modeswitch-data 20100127-1

I have tried to use the tool sakis3g mentioned by another poster but I get the following results

a. In the 'Please Select an Action' screen if I select More Options -> Only switch Modem (if applicable) I get a 'Modem Switched' message (after selecting the correct usb modem etc.

b. In the 'Please select an Action' screen if I select 'Connect With 3G' I get a 'Failed to connect' error.

The modem is not the problem as it works fine on Windows 

At no stage do I see anything in dmesg or lsusb to indicate that the modem has switched.
And I cannot find anything in modifo option for a combination of [FONT=Arial, Helvetica, sans-serif]12d1 [/FONT][FONT=Arial, Helvetica, sans-serif]and 1f01[/FONT], which are the vendor and product codes.

I manually edited my usb_modeswitch.conf to look like the following, based on what I saw on another site

Anyone got any thoughts ?, any help would be much appreciated.
```

[FONT=Arial, Helvetica, sans-serif]# Configuration for the usb_modeswitch package, a mode switching tool for[/FONT]
[FONT=Arial, Helvetica, sans-serif]# USB devices providing multiple states or modes[/FONT]
[FONT=Arial, Helvetica, sans-serif]#[/FONT]
[FONT=Arial, Helvetica, sans-serif]# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"[/FONT]
[FONT=Arial, Helvetica, sans-serif]# in /usr/sbin[/FONT]
[FONT=Arial, Helvetica, sans-serif]# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)[/FONT]
[FONT=Arial, Helvetica, sans-serif]# Everything else counts as "disable"[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]# Disable automatic mode switching globally (e.g. to access the original[/FONT]
[FONT=Arial, Helvetica, sans-serif]# install storage)[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]DisableSwitching=0[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]# Enable logging (results in a extensive report file in /var/log, named[/FONT]
[FONT=Arial, Helvetica, sans-serif]# "usb_modeswitch_<interface-name>"[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]EnableLogging=0[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]#######################################################[/FONT]
[FONT=Arial, Helvetica, sans-serif]# Huawei E353 (3.se)[/FONT]
[FONT=Arial, Helvetica, sans-serif]#[/FONT]
[FONT=Arial, Helvetica, sans-serif]# Contributor: Ulf Eklund[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]DefaultVendor= 0x12d1[/FONT]
[FONT=Arial, Helvetica, sans-serif]DefaultProduct=0x1f01[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]TargetVendor=  0x12d1[/FONT]
[FONT=Arial, Helvetica, sans-serif]TargetProduct= 0x14db[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]MessageContent="55534243123456780000000000000a11062000000000000100000000000000"[/FONT]
[FONT=Arial, Helvetica, sans-serif]
[/FONT]
[FONT=Arial, Helvetica, sans-serif]# Driver is cdc_ether[/FONT]
[FONT=Arial, Helvetica, sans-serif]NoDriverLoading=1[/FONT]
```

---

