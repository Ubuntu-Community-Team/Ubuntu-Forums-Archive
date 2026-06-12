---
title: "Mounting a digital camera problems"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by nick_ed on 2006-12-17
I have a Kodak DX7440 digital camera. When I plug it in, the ubuntu photo wizard pops up, and works fine for simply copying photos off the camer. But I'd like to be able to mount the camera properly as I sometimes use it as a storage device for moving files about etc.

I'm guessing it must actually be mounted already for the photo wizard to use it - but where is it mounted? I can't find it in /media or /mnt. I've tried mounting it myself, but I don't know where it's located, or even what FS it uses. I've tried /dev/sda sda1 etc, but there's nothing there. I also tried /dev/hdc but that resulted in 
```
mount: No medium found
```

When I plug the camera in, dmesg says things like
```
[17211728.904000] usb 3-1: new full speed USB device using ohci_hcd and address 8
[17211729.128000] usb 3-1: configuration #1 chosen from 1 choice

```
I don't know if that helps...  Any suggestions?

---

### Post by scrooge_74 on 2006-12-17
It should probably appear as a usb drive I am using a Sony camera and also the wizard pups up, but if I want to download any videos taken I have to look for them inside the usbb drive my pc sees.

---

### Post by nick_ed on 2006-12-17
Hmm, device /dev/usbb doesn't exist, and I've tried things similar to that. How can I tell where Ubuntu has put the device?

---

### Post by scrooge_74 on 2006-12-17
Either it appear on your desktop or Nautilus will show it as another device

---

### Post by nick_ed on 2006-12-17
I know it **should** show up on the desktop or in nautilus, but it doesn't! And even if it did show a link on the desktop, the device should still actually be mounted somehwere in /media right?

---

### Post by scrooge_74 on 2006-12-17
yes it should be mounted in media.


with dmesg should give more info

---

### Post by nick_ed on 2006-12-17
```
[17220099.336000] usb 3-1: new full speed USB device using ohci_hcd and address 11
[17220099.560000] usb 3-1: configuration #1 chosen from 1 choice

```

Is all that dmesg says after I plug in my camera

---

### Post by nick_ed on 2006-12-18
Anyone have any ideas?

---

### Post by yabbadabbadont on 2006-12-18
With the camera plugged in, what is the output of running, in a terminal window, "ls -lR /dev/bus/usb"?

---

### Post by nick_ed on 2006-12-18
```
nick@asbo:~$ ls -lR /dev/bus/usb
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 80 2006-12-18 23:13 001
drwxr-xr-x 2 root root 80 2006-12-19 00:23 002
drwxr-xr-x 2 root root 60 2006-12-18 23:13 003
lrwxrwxrwx 1 root root 14 2006-12-18 23:13 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 2006-12-18 23:13 001
crw-rw-r-- 1 root root 189, 1 2006-12-18 23:13 002

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root    189, 128 2006-12-18 23:13 001
crw-rw---- 1 root plugdev 189, 129 2006-12-19 00:23 002

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 2006-12-18 23:13 001

```

I have a hard drive (mounted) plugged in to one of my usb ports, the camera (turned on) into the other (probably 002 as it's the middle one of the three)

---

### Post by yabbadabbadont on 2006-12-18
First, make sure that your user is a member of the plugdev group.  It should be already, but run "id username" to see your group memberships.  If you are not currently a member of that group, add yourself to it using, "sudo gpasswd -a username plugdev".  If you have to do that, you will need to logout and back in before it will take effect.

Second, please post the output of "cat /proc/bus/usb/devices".

---

### Post by nick_ed on 2006-12-18
yep, i'm definately a member of plugdev. Here's the output of cat /proc/bus/usb/devices

```
nick@asbo:~$ cat /proc/bus/usb/devices

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-386 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:03.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-386 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:03.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=040a ProdID=057d Rev= 1.00
S:  Manufacturer=Eastman Kodak Company
S:  Product=KODAK EasyShare DX7440 Zoom Digital Camera
S:  SerialNumber=KCKDF44803170
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=16ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-386 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:03.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=059f ProdID=0651 Rev= 0.00
S:  Manufacturer=LaCie
S:  Product=LaCie Hard Drive USB
S:  SerialNumber=10000E000A27663D
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

```

---

### Post by yabbadabbadont on 2006-12-18
Ok, it sees the camera, but doesn't assign a driver to it.  Check the settings on your camera and see if there is an option to switch it from PTP mode (Picture Transfer Protocol) to something like USB or "Mass Storage" mode.  If it doesn't support the USB Mass Storage protocol, then you probably won't be able to mount the camera, but you should still be able to transfer pictures from it using camera software like digikam, gphoto2, or f-spot.  The important thing is that the USB subsystem does see the camera and has created a USB device for it (/dev/bus/usb/...)

---

### Post by nick_ed on 2006-12-18
Can't find anything about changing the transfer mode on the camera to USB Mass Storage. Odd coz when I plug it in to a windows computer it immediatly pops up as a USB mass storage device. But it may well use some weird drivers that windows has built in (it used to have an annoying "designed for XP" sicker on it :p).

Oh well, doesn't look like this is going to work. Never mind, like you said I can get pics off the camera without it mounting properly. Thanks very much for your help anyway!

---

### Post by CarlosSN on 2007-01-06
> **yabbadabbadont said:**
> Ok, it sees the camera, but doesn't assign a driver to it.  Check the settings on your camera and see if there is an option to switch it from PTP mode (Picture Transfer Protocol) to something like USB or "Mass Storage" mode.  If it doesn't support the USB Mass Storage protocol, then you probably won't be able to mount the camera, but you should still be able to transfer pictures from it using camera software like digikam, gphoto2, or f-spot.  The important thing is that the USB subsystem does see the camera and has created a USB device for it (/dev/bus/usb/...)

I have the same problem and i do have seting my camera in USB MASS STORAGE MODE.

how i mount the drive on my ubuntu edgy?

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 17 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04b0 ProdID=0306 Rev= 0.00
S:  Manufacturer=NIKON  
**S:  Product=NIKON DSC COOLPIX S9 **
S:  SerialNumber=??????????
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=05 Prot=50 Driver=usb-storage
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=0104 Rev= 1.00
S:  Manufacturer=Hewlett-Packard 
S:  Product=DeskJet 880C
S:  SerialNumber=MX9471T2JSFA
C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=01 Driver=usblp
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

---

### Post by yabbadabbadont on 2007-01-06
Unplug your camera and then plug it back in.  Then please post the output of running "dmesg" in a terminal window.  Also, if using gnome, check your preferences for removable (media/devices not sure what it's called) and make sure the you have it set to either mount your camera or for it to launch a camera application automatically when the camera is detected.

---

### Post by sysctl on 2007-02-12
> **yabbadabbadont said:**
> Ok, it sees the camera, but doesn't assign a driver to it.  Check the settings on your camera and see if there is an option to switch it from PTP mode (Picture Transfer Protocol) to something like USB or "Mass Storage" mode.

Thanks, that worked with Sony Cybershot DSC-W70 (PictBridge mode).

---

### Post by drsaamah on 2007-02-18
uuuuuh okay.  I also have a Sony DSC-W70.  Can someone (maybe the guy who said he got his to work) tell me EXACTLY how to get mine to work with edgy??  All I want to able to do is get my pictures FROM my camera TO my computer's harddrive.
NOTE!!  This is literally my 2nd day running on Linux, so I need EVERY little detail!!  Sorry to be a pain in the ***, but I'm still learning...

---

### Post by yabbadabbadont on 2007-02-18
Please read the whole thread, then post the information that I requested from the other poster.  Just as a quick suggestion though, make sure your camera is set to something like, "USB mass storage" mode.  The exact wording may vary, but that's what you should look for.

---

### Post by drsaamah on 2007-02-23
sorry I've been crazy busy.  I'll make sure to post all the info you want before the upcoming weekend is done. Thanks for your help and patience, I really appreciate it.

---

### Post by drsaamah on 2007-03-04
WOW.  okay im a technical-idiot.
Never mind I figured out how to get it to work.  I was in the USB mode, when I needed to be in PictBridge mode.  Thanks for your help anyways!

---

### Post by TonKi on 2007-03-05
Next one

I've a Nikon D1 and I would like to connect it directly over firewire, right now I take out the SD-Card and put it in my Ixus to import the pictures.

Imho the camera gets connected but nothing shows up (camera and pc)
I had a look into the manual put there is no tpt mode availabe or something similiar.

dmesg output
```
[17179710.304000] ieee1394: Host added: ID:BUS[1-00:1023]GUID[000d6100005fa18c]

```

---

### Post by yabbadabbadont on 2007-03-05
> **TonKi said:**
> Next one

I've a Nikon D1 and I would like to connect it directly over firewire, right now I take out the SD-Card and put it in my Ixus to import the pictures.

Imho the camera gets connected but nothing shows up (camera and pc)
I had a look into the manual put there is no tpt mode availabe or something similiar.

dmesg output
```
[17179710.304000] ieee1394: Host added: ID:BUS[1-00:1023]GUID[000d6100005fa18c]

```

I've never worked with firewire.  From that dmesg output though, I would guess that there should be some device entry for it either in /proc/bus or /dev/bus somewhere.  With it connected, run "ls -lR /dev/bus" and "ls -lR /proc/bus" and please post the output.

---

### Post by TonKi on 2007-03-06
Here's is the requested output, I've removed all other attached storage devices

ls -lR /dev/bus
```
/dev/bus:
total 0
drwxr-xr-x 8 root root 180 2007-03-06 10:30 usb

/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 100 2007-03-06 11:30 001
drwxr-xr-x 2 root root  80 2007-03-06 10:30 002
drwxr-xr-x 2 root root  60 2007-03-06 11:30 003
drwxr-xr-x 2 root root  60 2007-03-06 11:30 004
drwxr-xr-x 2 root root  60 2007-03-06 11:30 005
lrwxrwxrwx 1 root root  14 2007-03-06 10:30 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 2007-03-06 11:30 001
crw-rw-r-- 1 root root 189, 3 2007-03-06 11:30 004
crw-rw-r-- 1 root root 189, 4 2007-03-06 11:30 005

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 2007-03-06 11:30 001
crw-rw-r-- 1 root root 189, 129 2007-03-06 10:30 002

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 2007-03-06 11:30 001

/dev/bus/usb/004:
total 0
crw-rw-r-- 1 root root 189, 384 2007-03-06 11:30 001

/dev/bus/usb/005:
total 0
crw-rw-r-- 1 root root 189, 512 2007-03-06 11:30 001


```

ls -lR /proc/bus
```
/proc/bus:
total 0
dr-xr-xr-x 2 root root   0 2007-03-06 10:39 input
dr-xr-xr-x 6 root root   0 2007-03-06 10:39 pci
drwxr-xr-x 8 root root 180 2007-03-06 10:30 usb

/proc/bus/input:
total 0
-r--r--r-- 1 root root 0 2007-03-06 10:39 devices
-r--r--r-- 1 root root 0 2007-03-06 10:39 handlers

/proc/bus/pci:
total 0
dr-xr-xr-x 2 root root 0 2007-03-06 10:39 00
dr-xr-xr-x 2 root root 0 2007-03-06 10:39 01
dr-xr-xr-x 2 root root 0 2007-03-06 10:39 02
dr-xr-xr-x 2 root root 0 2007-03-06 10:39 03
-r--r--r-- 1 root root 0 2007-03-06 10:39 devices

/proc/bus/pci/00:
total 13
-rw-r--r-- 1 root root 256 2007-03-06 10:39 00.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 01.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 03.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1d.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1d.1
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1d.2
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1d.3
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1d.7
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1e.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1f.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1f.1
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1f.2
-rw-r--r-- 1 root root 256 2007-03-06 10:39 1f.3

/proc/bus/pci/01:
total 2
-rw-r--r-- 1 root root 256 2007-03-06 10:39 00.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 00.1

/proc/bus/pci/02:
total 1
-rw-r--r-- 1 root root 256 2007-03-06 10:39 01.0

/proc/bus/pci/03:
total 6
-rw-r--r-- 1 root root 256 2007-03-06 10:39 01.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 01.1
-rw-r--r-- 1 root root 256 2007-03-06 10:39 03.0
-rw-r--r-- 1 root root 256 2007-03-06 10:39 03.1
-rw-r--r-- 1 root root 256 2007-03-06 10:39 03.2
-rw-r--r-- 1 root root 256 2007-03-06 10:39 0a.0

/proc/bus/usb:
total 0
drwxr-xr-x 2 root root 100 2007-03-06 11:30 001
drwxr-xr-x 2 root root  80 2007-03-06 10:30 002
drwxr-xr-x 2 root root  60 2007-03-06 11:30 003
drwxr-xr-x 2 root root  60 2007-03-06 11:30 004
drwxr-xr-x 2 root root  60 2007-03-06 11:30 005
lrwxrwxrwx 1 root root  14 2007-03-06 10:30 devices -> .usbfs/devices

/proc/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 2007-03-06 11:30 001
crw-rw-r-- 1 root root 189, 3 2007-03-06 11:30 004
crw-rw-r-- 1 root root 189, 4 2007-03-06 11:30 005

/proc/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 2007-03-06 11:30 001
crw-rw-r-- 1 root root 189, 129 2007-03-06 10:30 002

/proc/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 2007-03-06 11:30 001

/proc/bus/usb/004:
total 0
crw-rw-r-- 1 root root 189, 384 2007-03-06 11:30 001

/proc/bus/usb/005:
total 0
crw-rw-r-- 1 root root 189, 512 2007-03-06 11:30 001

```

---

