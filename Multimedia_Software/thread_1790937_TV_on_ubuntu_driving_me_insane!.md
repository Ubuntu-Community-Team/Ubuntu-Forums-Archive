---
title: "TV on ubuntu driving me insane!"
date: 2011-06-25
forum: Multimedia Software
---

### Post by clgamer on 2011-06-25
HI all,
Newbie to ubuntu & the whole linux os, but love the look and feel of 11.04. I have struggled to get any answers to this question so I am trying for the last time before returning (regrettably) to WIndows 7.

I have around 8 Aopen MP45-DU mini pc's that all use the same DVB-t Card (MC770A HYBRID). Ubuntu works pretty well at a glance- all devices seem to work right away for this machine except the DVB-T card. 

Impressively after installing Ubuntu and clicking "additional drivers" it picks up that there is a DVB-T card installed and offers a download for it. SO I activate the firmware- but thats not the end of my troubles.

The DVB-T still does not function at all, I have tried all players from VLC to kaffeine to meTV and many many many more (including myth)

Not sure if the dmesg output below helps with identifying the issue: 

10.991929] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   11.037924] xc2028 17-0061: creating new instance
[   11.037928] xc2028 17-0061: type set to XCeive xc2028/xc3028 tuner
[   11.068012] Registered IR keymap rc-dib0700-rc5
[   11.068900] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/rc/rc0/input6
[   11.069072] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/rc/rc0
[   11.069613] dvb-usb: schedule remote query interval to 50 msecs.
[   11.069619] dvb-usb: YUAN High-Tech STK7700PH successfully initialized and connected.
[   11.069819] dib0700: rc submit urb failed
[   11.069821] 
[   11.069907] usbcore: registered new interface driver dvb_usb_dib0700
[   11.380279] ppdev: user-space parallel port driver
[   11.621219] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   11.636842] composite sync not supported
[   11.788569] composite sync not supported
[   12.532864] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   12.533063] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   12.799898] composite sync not supported
[   12.943873] composite sync not supported
[   13.095875] composite sync not supported
[   13.247890] composite sync not supported
[   13.584178] composite sync not supported
[   15.660771] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   19.132102] composite sync not supported



Anywho, does anyone use the avermedia/yuan mc770 card or has had experience solving this issue before. 

I am using the latest version of Ubuntu and quite interested in paying someone (if available) to solve this remotely for me. Anything to gain some movement (pm me if you want)

It would be a real shame to have to switch back to windows just because I couldn't get the TV cards working on these things :(

---

### Post by BicyclerBoy on 2011-06-25
A quick check on LinuxTV.org  (where the support comes from) reveals that the PD770A is not supported
The STK7700PH is supported.

Your model MC770A-Hybrid is not mentioned anywhere...
Could it be the same as PD770A (not supported)

I have read that the dvb part could work but not analogue (not great loss).

All the models seem to use the same USB ids in the best tradition of cheap asian manufacturers.

In your dmesg
I don't see the firmware being loaded.
something like  "firmware images from xc3028-v27.fw"

Have you added the linux non-free firmware package in synaptic manager (not in that gnome drivers jockey toy) ?

AFIAK Recent kernels have dropped some v4l (1) support, this has required the drivers to be updated.
You could try 10.04 or 10.10.

---

### Post by clgamer on 2011-06-26
> **BicyclerBoy said:**
> A quick check on LinuxTV.org  (where the support comes from) reveals that the PD770A is not supported
The STK7700PH is supported.

Your model MC770A-Hybrid is not mentioned anywhere...
Could it be the same as PD770A (not supported)

I have read that the dvb part could work but not analogue (not great loss).

All the models seem to use the same USB ids in the best tradition of cheap asian manufacturers.

In your dmesg
I don't see the firmware being loaded.
something like  "firmware images from xc3028-v27.fw"

Have you added the linux non-free firmware package in synaptic manager (not in that gnome drivers jockey toy) ?

AFIAK Recent kernels have dropped some v4l (1) support, this has required the drivers to be updated.
You could try 10.04 or 10.10.

Thanks so much for the reply- was giving up hope on any direction :confused:. How would I install and pay for the "none free firmware package"? 

I guess this would be my very last resort in hope that there is some sort of premium driver available for purchase that isn't available for free- that would be good too

Thanks again

---

### Post by BicyclerBoy on 2011-06-26
The package is free..
just it is called linux-firmware-non-free ..
Non-free means it can not be distributed with ubuntu by default, there are lots of other packages the same including different builds of the same libraries. Not free of copyright/patents, not foss.

A topic for you to read on ubuntu website is about package management.

You can find the firmware package in synaptic package manager.
You will already have the package linux-firmware..

If you are making HTPC type setup you should check out the ubuntu webpage about topics like DVD playback, restricted extras, medibuntu, libavcodec/format/utils, gstreamer bad & ugly, w32codecs
You will find these synaptic package manager but only after adding some more repositories. The medibuntu webpage will explain how.

---

### Post by clgamer on 2011-06-26
Thanks for your help, 
Yes installed these didn't help. Doing some reading through forums for anyone who has has this card/pc. I downloaded the Gnome device manager- shows 4 DVB-T devices as "?" and one USB device which is the Yuan.. not sure if that means much

---

### Post by BicyclerBoy on 2011-06-27
The dmesg output will indicate if firmware has loaded & device is initialised.
The driver being loaded & reporting the correct model is a requirement.

If you give one of your PCs to the developers you may have some luck..
Seriously...
The h/w support is very difficult/impossible without the h/w.
Your tuner is very similar to existing devices & so possibly needs some control/GPIO mapping stuff worked out.
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]
Kernel Labs 
[http://www.kernellabs.com]("http://www.kernellabs.com/")[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

His blog is a good read..

---

### Post by clgamer on 2011-06-27
Ok, got it to say something else in Dmesg...

Any ideas if I am getting warmer- it seems to load the firmware now?

13.044398] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/rc/rc0
[ 13.044525] dvb-usb: schedule remote query interval to 50 msecs.
[ 13.044532] dvb-usb: YUAN High-Tech STK7700PH successfully initialized and connected.
[ 13.044641] dib0700: rc submit urb failed
[ 13.044642] 
[ 13.044684] usbcore: registered new interface driver dvb_usb_dib0700
[ 13.186860] ppdev: user-space parallel port driver
[ 13.497864] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[ 13.521256] composite sync not supported
[ 13.704442] composite sync not supported
[ 13.715144] EXT4-fs warning (device sda1): release_blocks_on_commit:2672: discard not supported, disabling
[ 14.832010] composite sync not supported
[ 15.015874] composite sync not supported
[ 15.199873] composite sync not supported
[ 15.387870] composite sync not supported
[ 15.752126] composite sync not supported
[ 18.343317] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[ 21.142993] EXT4-fs warning (device sda1): release_blocks_on_commit:2672: discard not supported, disabling
[ 21.473210] composite sync not supported
[ 31.491943] wlan0: authenticate with 00:0e:9b:a2:1a:ea (try 1)
[ 31.493865] wlan0: authenticated
[ 31.493903] wlan0: associate with 00:0e:9b:a2:1a:ea (try 1)
[ 31.496485] wlan0: RX AssocResp from 00:0e:9b:a2:1a:ea (capab=0x411 status=0 aid=2)
[ 31.496490] wlan0: associated
[ 31.497166] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 42.464017] wlan0: no IPv6 routers present
[ 80.006670] xc2028 17-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[ 80.033195] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[ 85.917754] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (20, id 0000000000000000.
[ 86.021928] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.
[ 124.545079] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[ 130.430150] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (20, id 0000000000000000.
[ 130.534700] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.
[ 253.481090] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[ 259.365908] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (20, id 0000000000000000.
[ 259.470083] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.
[ 636.679829] xc2028 17-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[ 642.565762] xc2028 17-0061: Loading firmware for type=D2620 DTV8 (20, id 0000000000000000.
[ 642.669936] xc2028 17-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.

---

### Post by BicyclerBoy on 2011-06-27
Well the LinuxTV hardware list reveals that this device
YUAN High-Tech PD770A  is a hybrid:
part       status
analogue NO
FM radio  NO
DVB-T part: Clone of yuan-high-tech-stk7700ph but not working yet **?**
(the question mark is **not** my addition)
and
YUAN High-Tech STK7700PH [COLOR=green]   Yes[/COLOR], [COLOR=green]in kernel since 2.6.28[/COLOR]
(DVB-part of the Asus notebook M51Sn tv-tuner)
[http://linuxtv.org/wiki/index.php/Crypto_Diva_FM_DVB-T_Hybrid](http://linuxtv.org/wiki/index.php/Crypto_Diva_FM_DVB-T_Hybrid)

So you'll have to try with the dvb utils package (scan) etc.
[http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device).

Note that mythbackend does not share any (myth) configured tuners..

---

### Post by clgamer on 2011-06-30
> **BicyclerBoy said:**
> Well the LinuxTV hardware list reveals that this device
YUAN High-Tech PD770A  is a hybrid:
part       status
analogue NO
FM radio  NO
DVB-T part: Clone of yuan-high-tech-stk7700ph but not working yet **?**
(the question mark is **not** my addition)
and
YUAN High-Tech STK7700PH [COLOR=green]   Yes[/COLOR], [COLOR=green]in kernel since 2.6.28[/COLOR]
(DVB-part of the Asus notebook M51Sn tv-tuner)
[http://linuxtv.org/wiki/index.php/Crypto_Diva_FM_DVB-T_Hybrid](http://linuxtv.org/wiki/index.php/Crypto_Diva_FM_DVB-T_Hybrid)

So you'll have to try with the dvb utils package (scan) etc.
[http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device).

Note that mythbackend does not share any (myth) configured tuners..

Thanks for this, may give it a try. 
I reverted back to windows :( just to save hours/days perhaps more. I loved using ubuntu so no doubt I will have a shot at it again and will keep updating with any new finds. 

Appreciate your help

---

