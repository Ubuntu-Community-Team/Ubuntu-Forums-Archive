---
title: "ACER Orbicam integrated webcam now supported by GSPCA"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by brazzmonkey on 2006-12-20
check this out
[http://paper0k.wordpress.com/2006/12/18/orbicam-finalmente-supportata/](http://paper0k.wordpress.com/2006/12/18/orbicam-finalmente-supportata/)
i'm no italian speaker (i'm french), but it's kind of easy to understand. ACER orbicams integrated webcams are now supported by the latest gspca driver. it works for me (and bugs 30 sec later... :()
here's what our italian friend explains :
```
lsusb
```
to check if webcam is detected. you should get something like this.
```
Bus 001 Device 002: ID 046d:0896 Logitech, Inc.
```

!!!
**Please make sure you really get the following ID : 046d:0896**. This topic basically deals with this hardware only. Should get any other ID, please check [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) and make sure your hardware is supported. If you cannot find your device ID in the compatibility chart, then your hardware is not officially supported by GSPCA. You can still try the following steps, but please do not complain if this doesn't work.
!!!

**UPDATE : **if you're using feisty, this webcam should now work out of the box. You can still update GSPCA driver using this tutorial.

prerequisites :
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
get the sources here :  [http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)
go to the proper folder and uncompress archive :
```
tar zxvf ggspcav1-20070508.tar.gz
```
compile and install
```
cd gspcav1-20070508/
make
sudo make install
```
tune gspca module loading
 ```
sudo gedit /etc/modprobe.d/options
```
add
 ```
options gspca force_rgb=1
```
save and close.
load module :
 ```
sudo modprobe gspca
```
check the following device node
 ```
ls /dev/video*
```
```
 dmesg|tail -30
```
install webcam software
```
 sudo apt-get install camorama
```
you're done !

when using camorama, make sure you use the correct device (default is /dev/video0, you may have to try camorama -d /dev/video1, especially if you have a tv tuner or such device). however it bugs 30 sec later (i suppose the camera can't stand looking at me...)

---

### Post by kalindriv on 2006-12-26
Great!!!!
Thank you very much! It works quite fine, but it's enough!!!

---

### Post by ephioz on 2007-01-05
Can't get this to work. 

When I type
```
ls /dev/video*
```
I get "No such file or directory".
What am I doing wrong? I really would like this to work!

---

### Post by hakan69 on 2007-01-06
My Acer 5101 reports the Orbican as 1267:0210 Logic3/spectravideo. When I follow the Howto above, everything works without protests until I type ls /dev/video*. I then get, just like epioze: "No such file or directory". Camorama reports "Coluld not connect to video device"
kalindriv and brazzmonkey, what hardware have you got?

---

### Post by Mujaheiden on 2007-01-07
My friends' Acer 5100 is supplied wirh a "Bus 003 Device 002: ID 0402:5602 ALi Corp." webcam, which also doesn't show as dev/videox. The driver seems to be still in development [1](https://sourceforge.net/projects/m560x-driver/)

---

### Post by brazzmonkey on 2007-01-10
this appears to work only with Logitech webcams, i.e. you MUST read "ID 046d:0896 Logitech, Inc." in lsusb output. other devices, such as ali or logic3/spectravideo won't work, until explicitely supported. check 
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) for a list of supported webcams.

---

### Post by stoer on 2007-01-15
Hi,
i also have a logitch webcam, tried the above....
lsusb gives the following.

```
steve@laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08f5 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000 
```

tried your link 
[http://mxhaard.free.fr/spca50x/Downl...0061216.tar.gz](http://mxhaard.free.fr/spca50x/Downl...0061216.tar.gz)
which didn't work for me, went to the download page and did find  the following file...

gspcav1-20070110.tar.gz

so tried this.

```
steve@laptop:~/gspcav1-20070110$ ls /dev/video*
/dev/video  /dev/video0
```

dmesg|tail -30

```
steve@laptop:~/gspcav1-20070110$  dmesg|tail -30
[17179620.916000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179620.916000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179620.916000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179620.916000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179620.916000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179620.924000] [fglrx] total      GART = 268435456
[17179620.924000] [fglrx] free       GART = 252440576
[17179620.924000] [fglrx] max single GART = 252440576
[17179620.924000] [fglrx] total      LFB  = 128020480
[17179620.924000] [fglrx] free       LFB  = 119828480
[17179620.924000] [fglrx] max single LFB  = 119828480
[17179620.924000] [fglrx] total      Inv  = 134217728
[17179620.924000] [fglrx] free       Inv  = 134217728
[17179620.924000] [fglrx] max single Inv  = 134217728
[17179620.924000] [fglrx] total      TIM  = 0
[17179621.780000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179621.780000] apm: overridden by ACPI.
[17179623.048000] Bluetooth: Core ver 2.8
[17179623.048000] NET: Registered protocol family 31
[17179623.048000] Bluetooth: HCI device and connection manager initialized
[17179623.048000] Bluetooth: HCI socket layer initialized
[17179623.064000] Bluetooth: L2CAP ver 2.8
[17179623.064000] Bluetooth: L2CAP socket layer initialized
[17179623.132000] Bluetooth: RFCOMM socket layer initialized
[17179623.132000] Bluetooth: RFCOMM TTY layer initialized
[17179623.132000] Bluetooth: RFCOMM ver 1.7
[17183040.360000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17183041.036000] usbcore: registered new driver snd-usb-audio
[17184327.588000] usb 3-1: USB disconnect, address 2
[17184331.104000] usb 2-2: new full speed USB device using uhci_hcd and address 2
```

camorama -d /dev/video0 I think, connects to my tv card.
camorama -d /dev/video1 Can't connect error

Any ideas, or is it again something with the driver?
Cheers.

---

### Post by brazzmonkey on 2007-01-15
read my previous message. your device id differs from the one i mention, i'm afraid your webcam is not supported at this time.
sorry mate...

---

### Post by stoer on 2007-01-16
> **brazzmonkey said:**
> read my previous message. your device id differs from the one i mention, i'm afraid your webcam is not supported at this time.
sorry mate...

Bum!
ok, many thnx and back to the drawing board.

---

### Post by leagris on 2007-01-25
Bus 005 Device 008: ID 046d:0896 Logitech, Inc. 


Somehow work but picture very dark and noisy

17315695.660000] usbcore: registered new driver gspca
[17315695.660000] /home/lea/download/gspcav1-20070110/gspca_core.c: gspca driver 01.00.12 registered
[17315748.616000] /home/lea/download/gspcav1-20070110/gspca_core.c: [spca5xx_set_light_freq:1858] Sensor currently not support light frequency banding filters.
[17315748.616000] /home/lea/download/gspcav1-20070110/gspca_core.c: [gspca_set_isoc_ep:881] ISO EndPoint found 0x82 AlternateSet 7

Adjustments are not working.

[IMG]http://www.noiraude.net/img/Webcam-1169767096.png[/IMG]

---

### Post by brazzmonkey on 2007-01-26
adjustments don't work for me either. changing resolution is also problematic. but image quality is very good as long as ambient light is sufficient.

---

### Post by Mujaheiden on 2007-01-26
turn on some lamp and shine it on your face :) The background seems allright, so its just too dark at your place.

---

### Post by leagris on 2007-01-26
An old Philips Toucam Pro PVC740K gives very clean bright pictures in same environments. And it is at least 3years old. The current driver version for the Logitech should probably gain in having AGC amplification, exposure and other built-in adjustments availables.

[IMG]http://www.pc-cameras.philips.com/manuals/aaa_images/start/740camera.gif[/IMG]

Me with the Philips Toucam :

[IMG]http://www.noiraude.net/images/vero2002042701.jpg[/IMG]

---

### Post by brazzmonkey on 2007-01-26
wow is it just me or you look younger with the philips webcam ?
i reckon the driver is still buggy/not completed, and the orbicam is maybe less sensitive than you philips. anyhow, at least your orbicam works, even if it's not perfect... mine freezes and i get the following output :
```
dmesg
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [0] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [1] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [2] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [3] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [4] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [5] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [6] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [7] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [8] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [9] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [10] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [11] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [12] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [13] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [14] len=0, status=-18
[17206017.200000]
[17206017.200000] gspca_core.c: [spca50x_move_data:1548] ISOC data error: [15] len=0, status=-18

```

and no, i won't post my photo here ;)

---

### Post by searocræft on 2007-02-20
Thanks, it worked for my Orbicam on my Acer Aspire 5635WLMi!

---

### Post by ptpipe on 2007-03-12
Hello,
I have an ACER Travelmate 6460 and I tried to fallow this described procedure. Everything worked fine but I the video device is not found.

$ls /dev/video*
No such file or directory

$lsusb
Bus 005 Device 003: ID 046d:0896 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
(...)

$dmesg|tail -30
(...)
[17180092.232000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[17181056.000000] Linux video capture interface: v1.00
[17181056.000000] usbcore: registered new driver gspca
[17181056.000000] /home/lmourao/gspca-20060930/gspcav1/gspca_core.c: gspca driver 01.00.05 registered

Does anyone has a clue about what's happening ?

Thanks ;)

---

### Post by brazzmonkey on 2007-03-12
weirdo...
what gives ```
$ lsmod | grep gspca

``` ?
which ubuntu version ?

---

### Post by ptpipe on 2007-03-14
Here are the results:

```
$ lsmod|grep gspca
gspca                 638288  0
videodev               10752  1 gspca
usbcore               134912  4 gspca,ehci_hcd,uhci_hcd
```

And when I try to run Camorama:

```
$ camorama
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: not found
```


```
# gspcagui -d /dev/video0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


       ---------------------- DirectFB v0.9.24 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------


       ---------------------- DirectFB v0.9.24 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-10-13 15:40)
(*) DirectFB/Core: Single Application Core. (2006-10-13 15:40)
(*) Direct/Memcpy: Using linux kernel memcpy()
(*) Direct/Memcpy: Using MMX optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' failed
    --> No such device
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Couldn't initialize SDL: DirectFBCreate: Initialization error!
(!) Direct/Util: opening '/dev/fb0' failed
    --> No such device
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL: DirectFBCreate: Initialization error!.
```

I'm running Kubuntu 2.6.17-11-generic.

I tried to install a Creative Webcam using a similar procedure (but different driver) on a different laptop and the same happens. I think it's something related to xhost.

---

### Post by stueyboy on 2007-03-29
Hi, just thought I could offer some help for Acer webcams. I have an Acer 5601 with an integrated Orbicam.

> Bus 001 Device 002: ID 046d:0892 Logitech, Inc.

I initially struggled getting this to work in edgy but have since upgraded to the beta Feisty which has the driver installed as standard but I still had to fiddle with it to get it to  work. It does now work OK but is a bit blue which seems to be a common theme with these cams

> gspca                 643152  0 
videodev               28160  1 gspca
usbcore               134280  5 gspca,usbhid,uhci_hcd,ehci_hcd


Anyway, just thought I would let folks know that the above will work if you try hard enough.

Stu

---

### Post by staeryatz on 2007-04-13
I can't seem to get it working on Edgy. My notebook is an acer aspire 5050-5554 with an orbicam. Others with the same cam seemd to have gotten it working.

lsusb
```

Bus 003 Device 004: ID 0c45:6260 Microdia 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

lsmod | grep gspca
```

gspca                 676560  0 
videodev               14208  1 gspca
usbcore               167840  5 gspca,usbhid,ehci_hcd,ohci_hcd

```

I sill get ls: /dev/video*: No such file or directory. Camorama will not say a word in the command line. Ekiga will not detect devices using v4l nor v4l2. Any suggestions?

---

### Post by brazzmonkey on 2007-04-13
well, according to your device ID, i'm afraid your hardware differs from ours, and it's not listed on gspca website, so it's probably not supported atm.

---

### Post by staeryatz on 2007-04-14
Oh yeah I just noticed that now it's not on the list (c313). Well, at least now I don't have to waste my time trying to get it working, until it is on that list. Thanks for making this thread, very informative.

---

### Post by Gsyman on 2007-04-15
I trying to install creative live notebook pro, which is supported by gspca. When iget as far as sudo modprobe gspca I get 
FATAL: Error inserting gspca (/lib/modules/2.6.17-11-generic/kernel/drivers/usb/media/gspca.ko): Unknown symbol in module, or unknown parameter

What do I need to do to fix this?

Thanks

---

### Post by Swoop on 2007-05-01
Hey
I followed the guide and now my acer webcam works great. Its an Acer Travelmate 4280 with the logitech orbicam attached.
However i found two issues still remaining:

The adjustments controls dont work at all :(

The colors were all screwed up.

I managed to fix the colors by adding this to modprobe.d instead of rgb:

```
options gspca force_yuv=1
```

Now colors are showing correct in e.g. camorara :D

Hope this helps some peoploe.. however im still showing the rgb value in amsn for instance

---

### Post by Swoop on 2007-05-01
Okay i got a fatal error after a reboot, and removing the above live sorted it out... reseraching more into it... if anybody knows why let me know.

---

### Post by Swoop on 2007-05-01
> **Gsyman said:**
> I trying to install creative live notebook pro, which is supported by gspca. When iget as far as sudo modprobe gspca I get 
FATAL: Error inserting gspca (/lib/modules/2.6.17-11-generic/kernel/drivers/usb/media/gspca.ko): Unknown symbol in module, or unknown parameter

What do I need to do to fix this?

Thanks

I got this error, and i removed the line about force_rgb from module.d and the message went away .. i can still see the cam no trouble, but colors are wrong. Still working on this.

---

### Post by brazzmonkey on 2007-05-01
new driver has been released on april 26th.
no improvements for me though, image still freezes after a while.

removing the force_rgb option does nothing but mess with colours. rgb seems to be the proper parameter for my webcam, in addition, this force_yuv thing seems just plain wrong because i cannot find such an entry in the documentation.

---

### Post by brazzmonkey on 2007-05-09
a new version is out. still buggy for me, though.

---

### Post by Swoop on 2007-05-10
Tried to complile new version... i just followed the original instructions just with the new filename. Do i need to do anything else to use new version ?

anyhow no matter if i use the option=rgb or not the colors are really messed up here. Lets put it this way .. people have the same color as a smurf ! ;)

Anyhow here is some info from the dmesg:

```
[ 5775.212000] /opt/gspcav1-20070426/gspca_core.c: [spca5xx_set_light_freq:1868] Sensor currently not support light frequency banding filters.
[ 5775.212000] /opt/gspcav1-20070426/gspca_core.c: [gspca_set_isoc_ep:887] ISO EndPoint found 0x82 AlternateSet 7
[ 5826.224000] /opt/gspcav1-20070426/gspca_core.c: [spca5xx_set_light_freq:1868] Sensor currently not support light frequency banding filters.
[ 5826.224000] /opt/gspcav1-20070426/gspca_core.c: [gspca_set_isoc_ep:887] ISO EndPoint found 0x82 AlternateSet 7
[ 5850.356000] /opt/gspcav1-20070426/gspca_core.c: [spca5xx_set_light_freq:1868] Sensor currently not support light frequency banding filters.
[ 5850.356000] /opt/gspcav1-20070426/gspca_core.c: [gspca_set_isoc_ep:887] ISO EndPoint found 0x82 AlternateSet 7
[ 5893.388000] /opt/gspcav1-20070426/gspca_core.c: [spca5xx_set_light_freq:1868] Sensor currently not support light frequency banding filters.
[ 5893.388000] /opt/gspcav1-20070426/gspca_core.c: [gspca_set_isoc_ep:887] ISO EndPoint found 0x82 AlternateSet 7
[ 6122.404000] /opt/gspcav1-20070426/gspca_core.c: [spca5xx_set_light_freq:1868] Sensor currently not support light frequency banding filters.
[ 6122.404000] /opt/gspcav1-20070426/gspca_core.c: [gspca_set_isoc_ep:887] ISO EndPoint found 0x82 AlternateSet 7
[ 6293.924000] /opt/gspcav1-20070426/gspca_core.c: [spca5xx_set_light_freq:1868] Sensor currently not support light frequency banding filters.
[ 6293.924000] /opt/gspcav1-20070426/gspca_core.c: [gspca_set_isoc_ep:887] ISO EndPoint found 0x82 AlternateSet 7
[ 6536.028000] /opt/gspcav1-20070426/gspca_core.c: [spca5xx_set_light_freq:1868] Sensor currently not support light frequency banding filters.
[ 6536.028000] /opt/gspcav1-20070426/gspca_core.c: [gspca_set_isoc_ep:887] ISO EndPoint found 0x82 AlternateSet 7

```

Bus 002 Device 002: ID 046d:0896 Logitech, Inc.

thats my card.. its Acer orbicam on an Acer Travelmate 4280. Anybody know how to get the colors correct ?

---

### Post by markbirss on 2007-05-11
Hi

gspcav1-20070508 works on my Acer Ferrari 1005 with Acer Orbicam
Bus 003 Device 004: ID 046d:0896 Logitech, Inc. 

camorama shows perfectly with correct color, however xawtv and other apps don't show color correctly ? anyone know howto fix ?

---

### Post by markbirss on 2007-05-14
To solve the blue picture problem (BGR to RGB translation) do the following:

modify /etc/modprobe.d/options

options gspca force_rgb=0 or 1

---

### Post by Swoop on 2007-05-14
Okay with the value 0 i can see correct colors. But only in camora. when i open ekiga softphone i get the same blue colors again. 
any other places we need to change the value ?

Oh and i should notice the colors werent correct untill after a reboot .. dont know what i needed to reboot in order to activate the changes.

---

### Post by markbirss on 2007-05-15
Hi Swoop

I found that it is camorama that changes to blue color picture. You can fix this for camorama by adding the "color correction" filter.

---

### Post by Swoop on 2007-05-15
Thanks.
With force_rgb = 0 and color filter in camora it all works great ;) Now is there any way to make camora default start with the filter :D I know im being picky now but heck might as well get the perfect setup :D

---

### Post by forevertheuni on 2007-05-16
put "options gspca force_rgb=0" in /etc/modprobe.d/options

---

### Post by martinrandau on 2007-05-21
I have an ACER 5600. With Ubuntu 7.04 my integrated logitech webcam worked out of the box. I was so happy. But then it stopped working. I installed the latest gspca driver following this guide, but there's still no /dev/video*.

I have no idea what suddenly made it stop working. 

Not much to do, just wanted to let you know that this seems to be 50/50 business...

---

### Post by Swoop on 2007-05-21
what is the output from 
```
lsusb
```
and 
```
dmesg
```

 ??

---

### Post by martinrandau on 2007-05-22
```
martin@yeah:~$ lsusb
...
Bus 001 Device 004: ID 046d:c03d Logitech, Inc. 
...
```

```
martin@yeah:~$ dmesg | tail
[  228.104000] usb 5-6: USB disconnect, address 22
[  228.344000] usb 5-6: new high speed USB device using ehci_hcd and address 23
[  228.516000] usb 5-6: configuration #1 chosen from 1 choice
[  228.516000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
[  228.732000] ubuntu/media/gspcav1/gspca_core.c: Failed to configure camera
[  228.732000] gspca: probe of 5-6:1.0 failed with error -5
[  228.732000] usb 5-6: device_add(5-6:1.0) --> -5
[  228.860000] usb 5-6: USB disconnect, address 23
[  229.100000] usb 5-6: new high speed USB device using ehci_hcd and address 24
[  229.228000] usb 5-6: device descriptor read/64, error -71
```

Thanks, mate.

---

### Post by Swoop on 2007-05-22
As you can see that isnt supported on the compatibility list here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

At least not as far as i can see... my own output from lsusb is:

```
Bus 005 Device 002: ID 046d:0896 Logitech, Inc.
```

And i match this entry on the chart:

```
Logitech 	222 	0x046d 	0x0896 	Orbicam 		Vc0321 	PO3130Nc 	Test 	yuyv 	gspcav1 	***
```

So i think its because you simply have an unsupported chipset perhaps ?

---

### Post by martinrandau on 2007-05-22
Yes that might be. 

But how strange is it then that it worked out of the box at first install?

---

### Post by Swoop on 2007-05-23
yes .. im not expert on the webcams but perhaps there is a different driver you can use ?

But at least that seems to be the reason that this driver isnt working out the issue :D

---

### Post by brazzmonkey on 2007-05-24
just to let you know that you can get it work on feisty using sources from regular repos :
```
sudo apt-get install gspca-source
```
once you're done, run module assistant :
```
sudo module-assistant
```
and follow on-screen instructions : select, build and install gspca module.
you're done. follow the rest of the very first post (install camorama if needed, check /dev/video*, load the module, etc...)

---

### Post by GoldWing on 2007-05-27
Very strange thing here, somebody in this thread had a TM 6460 with a logitech webcam, my webcam has another !

Bus 005 Device 003: ID 064e:a111 Suyin Corp. 

Does somebody has any idea how to proceed here ?

I can't find any info about this.

---

### Post by Sebastral on 2007-05-28
> **brazzmonkey said:**
> just to let you know that you can get it work on feisty using sources from regular repos :
```
sudo apt-get install gspca-source
```
once you're done, run module assistant :
```
sudo module-assistant
```
and follow on-screen instructions.
you're done. follow the rest of the very first post (install camorama if needed, check /dev/video*, load the module, etc...)
Thanks! Very hopefull. When I do PREPARE it says;

Kernel headers available in /lib/modules/2.6.20-16-generic/build

Then I do LIST, SEARCH, GET for the spca5xx module, but LIST then states 

Binary package for kernel:

(2.6.20-16-generic): not found

and refuses to build the module :(

Synaptic says I seem to have all the relevant generic packages installed?

---

### Post by brazzmonkey on 2007-05-28
@GoldWing : your webcam isn't supported
@Sebastral : please select and build gspca module, not spca5xx.

---

### Post by PfD on 2007-05-28
Anyone knows if the above work on Debian Etch?
Thanx.

---

### Post by brazzmonkey on 2007-05-28
i'm no debian user, but i see no reason why it wouldn't work. should module-assistant not be in debian repos, method described in my very first post should work (make sure you do use latest version's link).

---

### Post by Sebastral on 2007-05-28
In a flash of wishful thinking I thought brazzmonkey refered 'it' to martinrandau's problem and provided the solution :rolleyes:
> **martinrandau said:**
> I have an ACER 5600. With Ubuntu 7.04 my integrated logitech webcam worked out of the box. I was so happy. But then it stopped working. I installed the latest gspca driver following this guide, but there's still no /dev/video*.

I have no idea what suddenly made it stop working. 

Not much to do, just wanted to let you know that this seems to be 50/50 business...
I installed the latest driver but no luck either. I put gspca on /etc/modprobe.d/blacklist so boot splash isn't interrupted by it.
When I modprobe the module the camera disappears from lsusb :/ and keeps repeating
[INDENT][  989.964000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
[  990.176000] ubuntu/media/gspcav1/gspca_core.c: Failed to configure camera
[  990.176000] gspca: probe of 1-4:1.0 failed with error -5
[  990.176000] usb 1-4: device_add(1-4:1.0) --> -5
[  990.324000] usb 1-4: USB disconnect, address 12
[  990.564000] usb 1-4: new high speed USB device using ehci_hcd and address 13
[  990.720000] usb 1-4: configuration #1 chosen from 1 choice[/INDENT]
I guess praying it moves from TEST to WORKS is left ;-)

---

### Post by brazzmonkey on 2007-05-28
> **Sebastral said:**
> When I modprobe the module the camera disappears from lsusb :/ 
that's really weird ! :confused:

---

### Post by muratkaya on 2007-05-28
so there is no ls /dev/video* directory,and you know we can not opened a folder into the dev,what am i gonna do? (also i installed some packages from synaptic(spca,gspca))

cheers!

---

### Post by brazzmonkey on 2007-05-29
i don't understand what you mean muratkaya.
what gives lsusb ? did you compile gspca (either from gspca's website sources or using module-assistant) ?

---

### Post by muratkaya on 2007-05-29
enki@babylon:~$ lsusb
Bus 002 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0402:5602 ALi Corp. 
Bus 001 Device 001: ID 0000:0000  

this is the result of lsusb.i tried whatever you show into this topic about gspca not only compile,but use different ways.

---

### Post by Swoop on 2007-05-30
Muratkaya:

Did you check to see if your webcam is supported on the compatibility list ?
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

As far as i can see its not supported thus wont work.

---

### Post by muratkaya on 2007-05-30
so? what can i do,may i destroy it or?  i do everything with linux but i did not find a solution to use my webcam

---

### Post by brazzmonkey on 2007-05-30
your webcam is NOT supported by GSPCA (yet), as Swoop kindly explained.
there's nothing you can do except wait or create the driver if you're skilled.

---

### Post by Swoop on 2007-05-30
Or perhaps contact the author of gspca and get involved with adding support for your specific webcam ? ;)

---

### Post by PfD on 2007-05-30
Hi! I've done all the above and my camera works in camorama, but has the problem with the colors mentioned above (in the first pages of the topic).
The problem is that there isn't any options file in the /etc/modprobe.d directory. It is not a hidden file either.
Any tips on how to fix the colors problem another way? Or somewhere else where I can find the file?
I'm using Debian Etch.

---

### Post by Swoop on 2007-05-30
The color problem should only be in camorama.
Try adding Color Correction filter in camorama and it should look normal :D :D Works for me :D

---

### Post by tonti on 2007-05-31
lsusb out

bus 005 device 002: ID 064e:a111 Suyin Corp.

so probably my acer cam doesn't have support yet :(

---

### Post by Swoop on 2007-05-31
not if its not on the list

---

### Post by hfdragon on 2007-07-18
> **Swoop said:**
> The color problem should only be in camorama.
Try adding Color Correction filter in camorama and it should look normal :D :D Works for me :D

Sorry, but where do i add this correction filter with camorama ?:confused::confused:

---

### Post by markbirss on 2007-07-27
hi hfdragon

do the following
* open camorama
* press CTRL + E to toggle the effects panel
* right mouse click in the effects pane and select "Add Filter"
* left click on "Color Correction"
that should do it :)

---

### Post by Mchipser on 2007-08-03
just so everyone knows... Acer uses 3 different types of webcams... Logitech, Bison, and suyin

---

### Post by wedderburn on 2007-08-03
cam works though the quality is shot to hell and back, i've looked around and couldn't find it but does anyone know if theres a svn or git for the unstable versions?

---

### Post by tcoffeep on 2007-08-30
Bus 003 Device 002: ID 0402:5602 ALi Corp. Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

This is what I get when I type 'lsusb'.

I've got an Acer Aspire 5100, and it's a logitech. How come it's always coming up differently?

---

### Post by delbene on 2007-09-01
I follow this procedure, but I only get a black screen from the webcam. Any idea?

*SOLVED: Turn some more lights on. :)

---

### Post by aswinms on 2007-09-18
Now, i know that my device isn't supported.. but i'm posting this here so that if anybody finds a way to help me out i'd pray that they be showered with unlimited supply of chocolates! 

this is is my device id - ID 064e:a100 Suyin Corp.

 I don't think it's supported.. nevertheless I tried all the commands that he asked to try and after i downloaded the tar file, it didn't uncompress... when i tried uncompressing, it showed me the following error :(

tar: ggspcav1-20070508.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


 HELP!!

---

### Post by Swoop on 2007-09-18
> **aswinms said:**
> Now, i know that my device isn't supported.. but i'm posting this here so that if anybody finds a way to help me out i'd pray that they be showered with unlimited supply of chocolates! 

this is is my device id - ID 064e:a100 Suyin Corp.

 I don't think it's supported.. nevertheless I tried all the commands that he asked to try and after i downloaded the tar file, it didn't uncompress... when i tried uncompressing, it showed me the following error :(

tar: ggspcav1-20070508.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


 HELP!!

Well seems like you are trying to untar the wrong file dude. Make sure the actual filename you downloaded is what it says. The guide might be out of date, so substitute filename for correct one.

---

### Post by ramadhian on 2007-10-21
Orbicam Not Work on my Acer Aspire 5051ANWXMi

rama@mylappy:~$ lsusb 
Bus 003 Device 003: ID 0c45:6260 Microdia 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 15ca:00c3  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

Detected as Microdia Chipset

Im so confuse with this webcam chipset

some user reported it work gspca
Some said it using Linux UVC Driver
Some said it will only work with sn9xxx Driver

So Which one is the right driver ?

---

### Post by gdoutch on 2007-11-12
** removed by poster **

---

### Post by skidzo on 2007-11-18
> **tcoffeep said:**
> Bus 003 Device 002: ID 0402:5602 ALi Corp. Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

This is what I get when I type 'lsusb'.

I've got an Acer Aspire 5100, and it's a logitech. How come it's always coming up differently?

With my Aspire 5100:

```
Bus 003 Device 003: ID 0402:5602 ALi Corp. 
```

seems to me that the device number an differ...

cam not working still have to stay with WIN for video...

---

### Post by kaarthik on 2008-05-10
hi,

I tried this but not able to succeed.

when i try the make command, it returns with an error as below:

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/kaarthirathnaa/Desktop/gspca-01.00.18 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/kaarthirathnaa/Desktop/gspca-01.00.18/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/kaarthirathnaa/Desktop/gspca-01.00.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2

Please could you help me in this regard.

Cheers,
Kaarthik

---

### Post by Swoop on 2008-05-11
Well i just wanted to add that the webcam in Acer previously mentioned is now supported out of the box.
My webcam works right away in 8.04 and did a few releases back actually ;)

---

### Post by medic2000 on 2008-05-30
Is there anyone who got a proper display with this camera? Mine is awful

---

### Post by GoldWing on 2008-05-30
mine works out of the box as well now.
But ... the image is upside down :guitar: I believe that is a known issue (I had it in windows as well.)

---

### Post by medic2000 on 2008-05-30
Can you post a screenshot? I want to compare it with mine. Did you tweaked it? By the way what is your lsusb? My chipset is:
046d:0896

---

### Post by GoldWing on 2008-05-31
> **medic2000 said:**
> Can you post a screenshot? I want to compare it with mine. Did you tweaked it? By the way what is your lsusb? My chipset is:
046d:0896
Bus 005 Device 009: ID 064e:a111 Suyin Corp. 

No tweaking, out of the box !

screenshot attached, very strange.

---

### Post by d4rkkn16ht on 2008-06-16
Need help here...
My Acer Orbicam Suyin is not working on my Hardy (but worked when using gutsy)...:(

The LED is glowing green but only green box on the screen (Ekiga).
On Cheese,nothing appear,only gnome foot & green LED.

If tried GSPCA but isn't working.

---

### Post by d4rkkn16ht on 2008-06-16
> **GoldWing said:**
> mine works out of the box as well now.
But ... the image is upside down :guitar: I believe that is a known issue (I had it in windows as well.)

You said your Windows Orbicam is upside down?
Your Windows Driver is obsolete...:)
Try [COLOR="Blue"][http://www.theacerguy.com]("http://www.theacerguy.com")[/COLOR] & find the correct driver :D

---

