---
title: "Would you Help me with a Gadmei UTV380 driver?"
date: 2009-09-05
forum: Multimedia Software
---

### Post by xieqiao on 2009-09-05
I'm a searching fervently for a Linux driver for my Gadmei UTV380 USB TV box. 

I have used terminal command "dmesg" to detect my card. The relevant information is probably as follows. 

[ 19.534284] EEPROM ID= 0x9567eb1a, hash = 0x2afc718a
[ 19.534286] Vendor/Product ID= eb1a:2861
[ 19.534288] AC97 audio (5 sample rates)
[ 19.534289] 500mA max power
[ 19.534291] Table at 0x04, strings=0x226a, 0x0000, 0x0000
[ 19.548498] em28xx #0: found i2c device @ 0x4a [saa7113h]
[ 19.564367] em28xx #0: found i2c device @ 0xa0 [eeprom]

[ 19.582123] em28xx #0: Your board has no unique USB ID and thus need a hint to be detected.
[ 19.582128] em28xx #0: You may try to use card=<n> insmod option to workaround that.

[ 8001.924969] em28xx new video device (eb1a:2861): interface 0, class 255
[ 8001.925269] em28xx #0: chip ID is em2860

[ 19.582138] em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
[ 19.582182] em28xx #0: card=21 -> eMPIA Technology, Inc. GrabBeeX+ Video Encoder

There are two lines that are probably very important&#65306;

[ 8002.775409] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 8002.775415] em28xx #0: Found Unknown EM2750/28xx video grabber

I have tried the following methods as learned from other users

Type " sudo chmod 777 /dev/video0" &#65292;, change "/dev/video0" to allowing read/write;

Install the following packages

mercurial
gcc
build-essential
linux-source

Then type the followng commands through terminal :

v4l-config
sudo apt-get install linux-headers-`uname -r`
$ mkdir tvdrviver
$ cd tvdriver                                                   &#65288;error message, can't find directory&#65289;
$ hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel)      &#65288;useless code, error&#65289;

$ cd v4l-dvb-kernel
$ make                               &#65288;can't find , useless code&#65289;
$ sudo make install             &#65288;also useless&#65289;

---

### Post by xieqiao on 2009-09-06
[http://ubuntuforums.org/showthread.php?t=869684](http://ubuntuforums.org/showthread.php?t=869684)

By following the above instructions, I have successfully edited the file "linux/drivers/media/video/em28xx/em28xx.h" and the file "linux/drivers/media/video/em28xx/em28xx-cards.c" within the "v4l-dvb" folder , using gedit.  

(A reminder:  You cannot download with the command "hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel/]("http://mcentral.de/hg/%7Emrec/v4l-dvb-kernel/") " because it has moved.  You have to download it from [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/))

Code:

cd v4l-dvb
make
sudo make install

All this is done with  no errors.  But when I tried the Code:

sudo modprobe em28xx

It does have errors. " FATAL: Error inserting em28xx (/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/em28xx/em28xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)"


When I opened TVtime, it shows "No signal, No inputs available, Cannot open capture device /dev/video0.  To avoid conflict, I unplugged Video Camera, but useless.

---

### Post by xieqiao on 2009-09-06
*[I]The solution seems to be re-installing the whole operating system, and update as little as possible unless it is absolutley necessary. *
[/I]

---

### Post by xieqiao on 2009-09-07
After having reinstalled the Ubuntu OS, I re-edited the above mentioned files adding UTV380, then input the following codes. 

cd v4l-dvb
make
sudo make install

No errors, so I tried 

sudo modprobe em28xx

again, no errors, 

But when I opened TVtime, it still showed  "No signal, No inputs available, Cannot open capture device /dev/video0.

---

### Post by xieqiao on 2009-09-08
I decided to give up. I shut down the computer and plugged in an outdated Phillips 7130 PCI TV Tuner card, and rebooted the PC.  Miraculously TVtime recognized the TV card instantly.  I was amazed because the old card did not work on my 64-bit Vista (That's why I replaced it with Gadmei UTV380).   

Praise the Lord.!

---

### Post by jeevas.v on 2010-07-22
Hi,

Currently I am working on adding support for Gadmei  USB TvBox UTV 380 series tuners.

The device I am having is having vendor/Product id eb1a:50a3 and looks like [http://www.gadmeisrilanka.com/380.html](http://www.gadmeisrilanka.com/380.html)

I was able to make it work after patching the latest v4l-dvb drivers. I tested the Television and it was working properly. I couldn't test the Television sound and Composite inputs. I will do that also soon and possibly send a patch to v4l-dvb team.

Please refer to [http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380) for the latest status.

Please let me know if any of you has any other variation under the same product name.

---

### Post by jeevas.v on 2010-07-22
> **xieqiao said:**
> I decided to give up. I shut down the computer and plugged in an outdated Phillips 7130 PCI TV Tuner card, and rebooted the PC.  Miraculously TVtime recognized the TV card instantly.  I was amazed because the old card did not work on my 64-bit Vista (That's why I replaced it with Gadmei UTV380).   

Praise the Lord.!


I think the SAA7130 based cards are still one of the best cards in the market and still in production. So you should be able to ger updated drivers for Vista/Win7. Most of them are flyvideo 2000 clones and probably without a eeprom. You can try downloading drivers from lifeview or mercury-pc websites to make it working on the latest Windows versions so that you won't miss your tv during those unfortunate moments when you can't avoid using a non-open buggy  os...:)

---

### Post by jeevas.v on 2010-07-22
> **xieqiao said:**
> [http://ubuntuforums.org/showthread.php?t=869684](http://ubuntuforums.org/showthread.php?t=869684)

By following the above instructions, I have successfully edited the file "linux/drivers/media/video/em28xx/em28xx.h" and the file "linux/drivers/media/video/em28xx/em28xx-cards.c" within the "v4l-dvb" folder , using gedit.  

(A reminder:  You cannot download with the command "hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-kernel/]("http://mcentral.de/hg/%7Emrec/v4l-dvb-kernel/") " because it has moved.  You have to download it from [http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/))

Code:

cd v4l-dvb
make
sudo make install

All this is done with  no errors.  But when I tried the Code:

sudo modprobe em28xx

It does have errors. " FATAL: Error inserting em28xx (/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/em28xx/em28xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)"


When I opened TVtime, it shows "No signal, No inputs available, Cannot open capture device /dev/video0.  To avoid conflict, I unplugged Video Camera, but useless.
You need to restart the system after installing the new drivers.

---

### Post by saflis on 2011-08-19
> **jeevas.v said:**
> Hi,

Currently I am working on adding support for Gadmei  USB TvBox UTV 380 series tuners.

The device I am having is having vendor/Product id eb1a:50a3 and looks like [http://www.gadmeisrilanka.com/380.html](http://www.gadmeisrilanka.com/380.html)

I was able to make it work after patching the latest v4l-dvb drivers. I tested the Television and it was working properly. I couldn't test the Television sound and Composite inputs. I will do that also soon and possibly send a patch to v4l-dvb team.

Please refer to [http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380) for the latest status.

Please let me know if any of you has any other variation under the same product name.

i still struggling with my Gadmei UTV380 on Natty, my device found as usb device 
Bus 002 Device 003: ID 1f71:3306
but after customize the module, still can't found the device, but on the dmesg log em28xx loaded. totally confusing for me. back to plugin my old pci tv turner bt878, work like a charm on natty :)

---

### Post by xieqiao on 2011-08-21
> **jeevas.v said:**
> Hi,

Currently I am working on adding support for Gadmei  USB TvBox UTV 380 series tuners.

The device I am having is having vendor/Product id eb1a:50a3 and looks like [http://www.gadmeisrilanka.com/380.html](http://www.gadmeisrilanka.com/380.html)

I was able to make it work after patching the latest v4l-dvb drivers. I tested the Television and it was working properly. I couldn't test the Television sound and Composite inputs. I will do that also soon and possibly send a patch to v4l-dvb team.

Please refer to [http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380) for the latest status.

Please let me know if any of you has any other variation under the same product name.

I appreciate your great effort, but the technical instructions on the page ( [http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380)) is too hard for me.  Would you be so kind as to write a small one-click automated program, or a step-by-step instruction so that I could input your commands into the terminal?

By the way, after upgrading to Ubuntu 11.04, my outdated Phillips 7130 PCI TV Tuner card also stopped working properly, even after I unplugged the Gadmei UTV380 to avoid conflict.  For the 7130 card, there is now only black color with distorted screen image and the sound is not working.

---

### Post by gayungan on 2012-08-06
> **xieqiao said:**
> I appreciate your great effort, but the technical instructions on the page ( [http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380)) is too hard for me.  Would you be so kind as to write a small one-click automated program, or a step-by-step instruction so that I could input your commands into the terminal?

By the way, after upgrading to Ubuntu 11.04, my outdated Phillips 7130 PCI TV Tuner card also stopped working properly, even after I unplugged the Gadmei UTV380 to avoid conflict.  For the 7130 card, there is now only black color with distorted screen image and the sound is not working.

yes..me too.. its too hard for me [http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV38:confused:](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV38:confused:)

---

