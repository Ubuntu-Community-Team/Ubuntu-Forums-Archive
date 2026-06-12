---
title: "Eagerly installed  sn9c102 in the way of  uvcvideo for Sonix webcam?"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by nodcero on 2007-06-25
On my search to get my webcam working, I followed one promising clue and installed  the sn9cxxx  Modules..

Disappointingly that didn't do the trick, so further search and research let me come up with the UVP-thingies, the panacea for my Vendor and Device Number, as it seemed. And probably still is...

My hope is, that sn9c102 'just' stands in the way of uvcvideo, but modprobe -r and rmmod return a 'can't do' message, as the module is used, by whatever, and blacklisting it in /etc/modprobe.d/blacklist did so far not bring any change to that behaviour or joy either. Neither did an additional blacklist in /etc/hotplug/blacklist.

Am I generally on the right track or am I making an utter fool out of myself here? And if I am correct, how can I get rid of my first installation? Before I am making everything even worse with further bungled attempts?

If that is any help:


Thats the lsusb situation:

> Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

/proc/bus/usb/devices reads:

> T:  Bus=05 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=62c0 Rev= 1.00
S:  Manufacturer=Sonix Technology Co., Ltd.
S:  Product=USB 2.0 Camera
S:  SerialNumber=SN0001
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(unk. ) Sub=01 Prot=00 Driver=uvcvideo
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=4ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 1 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 128 Ivl=125us
I:  If#= 1 Alt= 2 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 256 Ivl=125us
I:  If#= 1 Alt= 3 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 800 Ivl=125us
I:  If#= 1 Alt= 4 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1600 Ivl=125us
I:  If#= 1 Alt= 5 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2400 Ivl=125us
I:  If#= 1 Alt= 6 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=3000 Ivl=125us
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 3 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 3 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=84(I) Atr=05(Isoc) MxPS= 400 Ivl=1ms


The probably relevant dmesg parts:

> 0.248854] Boot video device is 0000:00:02.0
[   19.264000] Linux video capture interface: v2.00
[ 1015.204000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 1015.216000] usbcore: registered new interface driver uvcvideo


lsmod shows:

> uvcvideo               42500  0 
video                  16388  0 
videodev               28160  2 uvcvideo,sn9c102
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  3 uvcvideo,sn9c102,videodev
compat_ioctl32          2304  1 sn9c102
usbcore               134280  8 uvcvideo,snd_usb_audio,snd_usb_lib,sn9c102,usbhid,ehci_hcd,uhci_hcd

---

