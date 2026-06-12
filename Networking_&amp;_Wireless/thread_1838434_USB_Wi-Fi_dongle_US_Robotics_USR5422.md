---
title: "USB Wi-Fi dongle US Robotics USR5422"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by Antonjo on 2011-09-03
I have an USB Wi-Fi dongle US Robotics USR5422.

I followed the procedure described here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The adapter works for a few seconds, then the system completely freezes and I have to hard reset.

I tried to compile myself the ndiswrapper-1.56.tar.gz but I get the error:

Unknown field 'ioctl' specified in initializer


I tried also to install/compile ndiswrapper dpkg. 
  
I wire-connected the laptop and updated the system.

No luck in any cases.

Note that I ran a live Puppy Linux on an USB stick and the adapter was recognised automatically out of the box.
 
Can you help?


I have an AMD Athlon XP m 2600 laptop, 512 Mega RAM DDR, 
with Lubuntu 11

Thanks in advance
Antonio

---

### Post by praseodym on 2011-09-03
Hi,

please show:

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Antonjo on 2011-09-03
Here is it. 

```


### I need to remove driver to avoid freezing when plugging the stick:

antonio@paris:~/Desktop$ ndiswrapper -l
rsc4usb : driver installed
antonio@paris:~/Desktop$ sudo ndiswrapper -r rsc4usb
[sudo] password for antonio:
antonio@paris:~/Desktop$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0baf:0118 U.S. Robotics U5 802.11g Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

### Unplug stick and reinstall driver 

antonio@paris:~/Desktop$ sudo ndiswrapper -i ndis/USRob/unzipped_exe/Driver/RSC4USB.inf 
installing rsc4usb ...
forcing parameter EnableRadio from 0 to 1
antonio@paris:~/Desktop$ sudo depmod -a
antonio@paris:~/Desktop$ sudo modprobe ndiswrapper
antonio@paris:~/Desktop$ lsmod >lsmod.txt

Module                  Size  Used by
savage                 35490  1 
drm                   184164  2 savage
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_via82xx            24685  1 
gameport               15027  1 snd_via82xx
snd_mpu401_uart        13865  1 snd_via82xx
snd_via82xx_modem      18305  0 
snd_ac97_codec        105614  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
i2c_viapro             12969  0 
via_ircc               26953  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
irda                  185091  1 via_ircc
pcmcia                 39671  0 
psmouse                73312  0 
serio_raw              12990  0 
snd_page_alloc         14073  3 snd_via82xx,snd_via82xx_modem,snd_pcm
yenta_socket           27230  0 
soundcore              12600  1 snd
pcmcia_rsrc            18292  1 yenta_socket
crc_ccitt              12595  1 irda
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
ndiswrapper           183882  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
cb710_mmc              13380  0 
firewire_ohci          31504  0 
via_rhine              27131  0 
pata_via               13368  2 
cb710                  13734  1 cb710_mmc
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


antonio@paris:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

### Of course there would be wlan0 here with the USB dongle plugged, but just some for moments before freezing. 

antonio@paris:~/Desktop$ rfkill list 
antonio@paris:~/Desktop$ 
### Blank output for rfkill.


```

Antonio

---

### Post by praseodym on 2011-09-03
Which Windows driver do you use? I would recommend Win2000 or XP. Checks:

```
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
dmesg | grep ndis
```

---

### Post by Antonjo on 2011-09-03
```
antonio@paris:~/Desktop$ ndiswrapper -l
rsc4usb : driver installed
antonio@paris:~/Desktop$ cat /etc/modprobe.d/ndiswrapper.conf 
alias usb:v0BAFp0118d*dc*dsc*dp*ic*isc*ip* ndiswrapper
antonio@paris:~/Desktop$ dmesg | grep ndis
[   15.154872] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   15.265536] usbcore: registered new interface driver ndiswrapper
antonio@paris:~/Desktop$ 

```


The driver and the .inf are unique. I see that inside there are sections for XP:

```
[PRISM_A021_XP]    ; Winxp
 AddReg         = PRISM_A021.reg, COMMON_A02.reg, COMMON_NDIS.reg.NT, COMMON.reg
 CopyFiles      = PRISM_DRIVER.copy.XP, PRISM_CCU.copy
 BusType        = 0
 Characteristics= 0x84

[PRISM_A021_XP.Services]
 AddService= "RSC4_A02", 2, PRISM_DRIVER_A02.Service, PRISM_DRIVER.EventLog

[PRISM_A021_XP.CoInstallers]
 CopyFiles      = PRISM_COINSTALL.copy.NT
 AddReg         = PRISM_COINSTALL.reg.NT 
 
etc. etc.  

```

---

### Post by praseodym on 2011-09-03
Kernel 2.6.38 s***s, try this patched ndiswrapper installation:

[http://forum.ubuntuusers.de/post/3080287/](http://forum.ubuntuusers.de/post/3080287/)

You have to remove **ndisgtk**, too, otherwise ndisrapper will be overwritten by that dependecies.

Uninstallation with all config files via:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Install the windows driver via terminal.

---

### Post by Antonjo on 2011-09-03
When compiling I get the usual 'ioctl' error mentioned in the first post.


```
antonio@paris:~/Desktop/ndiswrapper-1.56_patch_12$ sudo make 
make -C driver
make[1]: Entering directory `/home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver'
make -C /usr/src/linux-headers-2.6.38-11-generic M=/home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver/loader.o
/home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver/loader.c:834:2: error: unknown field â€˜ioctlâ€™ specified in initializer
/home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver/loader.c:834:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver/loader.o] Error 1
make[2]: *** [_module_/home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/antonio/Desktop/ndiswrapper-1.56_patch_12/driver'
make: *** [all] Error 2

```

Sorry it's very late here in Rome as in Berlin... continue tomorrow, thanks for your experienced help 

Antonio

---

### Post by praseodym on 2011-09-03
Searched for the error messages: You need these patches (both links):

[http://forum.ubuntuusers.de/topic/das-leidige-thema-ubuntu-und-fritz-wlan/#post-2802848](http://forum.ubuntuusers.de/topic/das-leidige-thema-ubuntu-und-fritz-wlan/#post-2802848)

---

### Post by Antonjo on 2011-09-04
Good afternoon praseodym.

Before starting I try to sum up my tasks.

Assuming that: 

```

~/Desktop/ndiswrapper-1.56-2.6.38.patch 

```

contains ([http://chakra-project.org/bbs/viewtopic.php?pid=28458):](http://chakra-project.org/bbs/viewtopic.php?pid=28458):))

```


--- driver/wrapndis.c   (revision 2728)
+++ driver/wrapndis.c   (revision 2729)
@@ -13,16 +13,16 @@
  *
  */

+#include <linux/inetdevice.h>
+#include <linux/ip.h>
+#include <linux/tcp.h>
+#include <linux/udp.h>
+#include <linux/in.h>
 #include "ndis.h"
 #include "iw_ndis.h"
 #include "pnp.h"
 #include "loader.h"
 #include "wrapndis.h"
-#include <linux/inetdevice.h>
-#include <linux/ip.h>
-#include <linux/tcp.h>
-#include <linux/udp.h>
-#include <linux/in.h>
 #include "wrapper.h"

 /* Functions callable from the NDIS driver */



```


The terminal commands should be:

```


# Remove ndiswrapper 
~$ sudo modprobe -rf ndiswrapper
~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
~$ sudo rm -r /etc/ndiswrapper/* 
~$ sudo depmod -a

# Patch ndiswrapper-1.56.tar
~$ cd Desktop/
~/Desktop$ tar zxvf ndiswrapper-1.56.tar
~/Desktop$ cd ndiswrapper-1.56/
~/Desktop/ndiswrapper-1.56$ patch -Np0 < ../ndiswrapper-1.56-2.6.38.patch

# Build and install
~/Desktop/ndiswrapper-1.56$ make uninstall
~/Desktop/ndiswrapper-1.56$ make
~/Desktop/ndiswrapper-1.56$ sudo make install
~/Desktop/ndiswrapper-1.56$ cd ..


# Set ndiswrapper.ko
~/Desktop$ cd /lib/modules/misc
/lib/modules/misc$ sudo cp ndiswrapper.ko ../2.6.38-5-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/misc$ sudo depmod-a
/lib/modules/misc$ sudo modprobe ndiswrapper


# Assuming inf-driver is ~/Desktop/ndis/USRob/unzipped_exe/Driver/RSC4USB.inf 
cd ~/Desktop/
~/Desktop$ sudo ndiswrapper -i ndis/USRob/unzipped_exe/Driver/RSC4USB.inf 
~/Desktop$ sudo depmod -a
~/Desktop$ sudo modprobe ndiswrapper



```


This is how I intend things in:
[http://forum.ubuntuusers.de/topic/das-leidige-thema-ubuntu-und-fritz-wlan/#post-2802848](http://forum.ubuntuusers.de/topic/das-leidige-thema-ubuntu-und-fritz-wlan/#post-2802848)

Actually I do not quite understand if "Set ndiswrapper.ko" code goes after or before "Build and install"


Antonio

---

### Post by praseodym on 2011-09-05
Did you apply [COLOR="Red"]all[/COLOR] patches from both links? After that you should compile and apply ndiswrapper.ko (copy) to your system.

---

### Post by praseodym on 2011-09-05
You may try a Mainline-kernel, namely [2.6.39-4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/"). You need all three possible packages for your 32 or 64 bit system. dkms should be installed before:

```
sudo apt-get install dkms
```
Save the three packages on your desktop and install via:
```
sudo dpkg -i ~/Desktop/linux*.deb
```
and reboot. You may first try the regular ndiswrapper from the repositories with this kernel.

---

### Post by Antonjo on 2011-09-05
Probably I misunderstand something since I am not a German speaker. Anyway, if this is supposed to be the second link for the patch:

Danach die hier erwaehnten:
[http://forum.nginx.org/read.php?31,154520,157836](http://forum.nginx.org/read.php?31,154520,157836)

it seems broken. 
Antonio

---

### Post by praseodym on 2011-09-05
Oh, yes, that link is down now. Which kernel does Puppy use? Can you try the mainline kernel or a similar kernel like the Puppy one?

---

### Post by Antonjo on 2011-09-05
Puppy is Lucid 5.2.8 and on it  uname -r says 2.6.33.2. 

Probably the link [http://forum.nginx.org/read.php?31,154520,157836](http://forum.nginx.org/read.php?31,154520,157836) was just remapped. 

Now do I go with 2.6.39 or Puppy?


Antonio

[EDIT]
This explain things to a newbie like me.  Puppy Lucid 5.2.8 is the current one, but they prefer to be conservative and things keep working. Probably this is why for you I read Ubuntu 10.04 Lucid Lynx.

---

### Post by praseodym on 2011-09-05
2.6.33 is too old (maybe other things dont work with it). Try the mainline kernel.

---

### Post by Antonjo on 2011-09-05
ok, I am doing it.....

an auto install service for ndiswrapper is running!

---

### Post by Antonjo on 2011-09-05
I installed the ndiswrapper and the USB adapter .inf .

First plug of the adapater triggered I kind of immediate reboot to the system. 


After a couple of reboots I see the usual system freeze. Probably the system now lasts longer with adapter plugged before freezing. 

Antonio

---

### Post by praseodym on 2011-09-05
Really strange. I dont think its a kernel thing. Can you reset your BIOS to default settings? Which video card do you use:

```
lspci -nnk | grep -iA2 VGA
```

---

### Post by Antonjo on 2011-09-05
BIOS to default.


antonio@paris:~$ lspci -nnk | grep -iA2 VGA
01:00.0 VGA compatible controller [0300]: S3 Inc. VT8375 [ProSavage8 KM266/KL266] [5333:8d04]
	Subsystem: Packard Bell B.V. Device [1631:e004]
	Kernel modules: savagefb
antonio@paris:~$

---

### Post by Antonjo on 2011-09-05
Note in BIOS I could also disable:

mc97 (modem)
ac97 (audio)
USB emulation 

They are enalbled by with default settings. 

As far it may concern: this is a notebook with no Intel, but: 
AMD Athlon XP M 2600 laptop, 512 Mega RAM DDR. 

Who knows could it be this processor is simply to slow to manage an Internet connection via USB port?

---

### Post by praseodym on 2011-09-05
I found a thread with freezes like that, it was about the driver. You may reinstall it:

```
sudo apt-get update
sudo apt-get install --reinstall xserver-xorg-video-savage
```
and reboot. Do you use Desktop-effects (Compiz)?

---

### Post by Antonjo on 2011-09-05
Of course I  tried first the regular ndiswrapper from the repositories with the new kernel.

So I can probably try other patched versions.

---

### Post by Antonjo on 2011-09-05
I use Lubuntu and I keep the default LXDE shell very simplistic. 

No fancy things, Compiz etc.

 
I am establishing an Ethernet connection for the update.

---

### Post by Antonjo on 2011-09-05
Everything done. 

Adapter plugged for some 7 minutes with no freezing!

Too looooong ... may be the miracle. Now I try to connect to an hotspot.

---

### Post by Antonjo on 2011-09-05
The first attempt to connect to an hot spot involved a pseudo freezing,  that is I could move the mouse pointer. So probably it was the freshly installed xserver.  

After a reboot, everything went very smooth for some 20 minutes. Then, with a very heavy page in Chromimum, I had a crash in the form of an auto reboot, kinda like unplugging the power. 
This may be normal for an old PC with a heavy duty. 
  
So you made, if not a whole, half a miracle. 

Thanks praseodym.

---

### Post by Antonjo on 2011-09-06
As stated in my previous post, ndis-driver was installed, but -- may be because of the "age" of my notebook -- after some time using the stick the system freezes. To completely remove this issue, I started  observing, while running a live Lucid Puppy on the same system, that my stick worked out of the box, in a plug and play fashion. With the help of lsmod I saw that Puppy made the magic without ndiswrapping, but via Prism drivers. 

In fact:
 
```

lsmod |grep p54   

p54usb                  8818  0 
p54common              17863  1 p54usb
led_class               1733  1 p54common
mac80211               99898  2 p54usb,p54common
cfg80211               90319  2 p54common,mac80211
usbcore                91279  6 p54usb,usbhid,usb_storage,uhci_hcd,ehci_hcd 


```

Why not use the same solution in Ubuntu?

I removed ndiswrapper, issuing:

```

sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod –a


```

Therefore I re-enabled Prism where previously blacklisted with:
 
```
 
sudo vim  /etc/modprobe.d/blacklist.conf

```


commenting the lines blacklisting p54 modules:

```

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
#blacklist p54usb
#blacklist p54common

```



Finally I installed the Prism driver like this:

```
sudo apt-get install linux-firmware-nonfree
sudo modprobe p54usb

```

Now everything is at top level and... thanks Puppy

Antonio

*** Important notice ***

Based on my experience USRobotics Wireless USB Adapter USR5422 (or USR805422) can work better without native win32 driver, despite many tutorial, also in this forum, suggest to use the native win32. If you are having problems, try Prism like me.

---

### Post by praseodym on 2011-09-06
Wow, cool stuff, thanks for the reply.

---

### Post by Antonjo on 2011-09-06
Glad you find it interesting. 

I try to give back kindness I receive.

... and more or less I remastered the tricks I learned from you.

:popcorn:

---

