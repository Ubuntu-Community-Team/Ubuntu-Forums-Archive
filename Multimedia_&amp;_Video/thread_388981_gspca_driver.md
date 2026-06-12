---
title: "gspca driver"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by s57nev on 2007-03-20
I'm trying to install gspca webcam driver on Edgy...The only thing that keeps me from doint that is  how to remove old spca5xx driver. There is no package to remove in synaptic. Should I blacklist spca module or something like that ? Any ideas ?

---

### Post by buntu_hugenewbie11 on 2007-04-06
Did you get a solution to this?

---

### Post by hazelkid on 2007-04-28
just do a 

sudo modprobe -r spca5xx

and install gspcav1

then 

sudo modprobe -v gspca

---

### Post by ramadhian on 2007-07-08
gspca is already provided in Ubuntu 7.04 kernel tree (Linux 2.6.20-16-generic i686)

but still not work properly ,,,
seem like gspca compile with v4l2 which is not all webcam application using v4l2 

same thing happened to me 

I got Lexcron Webcam here which is supported by gspca driver . 

I already used it when I still using Mandriva 2007, webcam can work great there.

here is the details in my Ubuntu 7.04

kenzo@ramadhian:~$ lsusb
Bus 005 Device 007: ID 0ac8:301b   Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 005 Device 006: ID 0df7:0620   Mobile Action Technology, Inc. MA-620 Infrared Adapter
Bus 005 Device 005: ID 147a:e006   Formosa Industrial Computing, Inc. 
Bus 005 Device 003: ID 058f:6254   Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 6547:0232  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:08b2   Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

My Lexcron  Webcam detected as "ZC030" (Z-Star Microelectronics Corp. ZC0301 WebCam)

kenzo@ramadhian:~$ cat /etc/modprobe.d/options | grep cam
options quickcam compatible=2

I dont know if there's any relation with this option parameter to gspca driver 
but that option seems work with my another webcam "Logitech QuickCam Pro 4000"

may be I have to add some options parameter at /etc/modprobe.d/options for GSPCA Driver
to make my Lexcron/Vimicro Webcam can work properly

kenzo@ramadhian:~$ modinfo gspca | grep parm
parm:           autoexpo:Enable/Disable auto exposure (default=1: enabled) (PC-CAM 600/Zc03xx/spca561a/Etoms Only !!!) (int)
parm:           debug:Debug level: 0=none, 1=init/detection, 2=warning, 3=config/control, 4=function call, 5=max (int)
parm:           force_rgb:Read RGB instead of BGR (int)
parm:           gamma:gamma setting range 0 to 7 3-> gamma=1 (int)
parm:           OffRed:OffRed setting range -128 to 128 (int)
parm:           OffBlue:OffBlue setting range -128 to 128 (int)
parm:           OffGreen:OffGreen setting range -128 to 128 (int)
parm:           GRed:Gain Red setting range 0 to 512 /256  (int)
parm:           GBlue:Gain Blue setting range 0 to 512 /256  (int)
parm:           GGreen:Gain Green setting range 0 to 512 /256  (int)
parm:           compress:Turn on/off compression (not functional yet) (int)
parm:           usbgrabber:Is a usb grabber 0x0733:0x0430 ? (default 1)  (int)
parm:           lightfreq:Light frequency banding filter. Set to 50 or 60 Hz, or zero to NoFliker (default=50) (int)
 

I have no documentation about this parameter..

So I still Blank about this GSPCA Driver in Ubuntu 7.04 ..

Any Expertist wanna give some hints about this ??

---

### Post by s57nev on 2007-10-01
Don't know I use Genious Webcam.  You can change module options with : 

```

$sudo -s       
#echo "4" > /sys/module/gspca/parameters/gamma (da parametru gamma spremenimo vrednost na 4)
#echo "240" > /sys/module/gspca/parameters/GRed
#exit 

``` 

Too bad there is no GUI for changing parameters. Gamma changing would be nice for dark rooms...

I wrote a Wiki for webcams. You can find it [SLO Ubuntu Wiki-Webcam]("http://www.ubuntu.si/dokuwiki/doku.php?id=spletna_kamera")

Sory it's in Slovenian but I think you will understand it .

---

