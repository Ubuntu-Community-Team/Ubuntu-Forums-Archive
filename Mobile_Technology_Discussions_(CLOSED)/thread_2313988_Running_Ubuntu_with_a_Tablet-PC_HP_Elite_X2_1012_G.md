---
title: "Running Ubuntu with a Tablet-PC HP Elite X2 1012 G1"
date: 2016-02-17
forum: Mobile Technology Discussions (CLOSED)
---

### Post by baumber on 2016-02-17
Hey guys,

I'm interested in buying a Tablet-PC HP Elite X2 1012 G1.

It is a brand-new 2-in-1 Business-Tablet/Convertible. 

Overview
[http://store.hp.com/webapp/wcs/stores/servlet/ContentView?storeId=10151&langId=-1&catalogId=10051&eSpotName=EliteX2_1012](http://store.hp.com/webapp/wcs/stores/servlet/ContentView?storeId=10151&langId=-1&catalogId=10051&eSpotName=EliteX2_1012)

Specs:
[http://www8.hp.com/h20195/v2/GetPDF.aspx/c04895999.pdf](http://www8.hp.com/h20195/v2/GetPDF.aspx/c04895999.pdf)

Has anyone experiences in running this tablet with Ubuntu/Linux?

Should it work with dual boot with Windows 10 or is it locked down with TPM?

- Example Configuration:
HP Elite x2 1012 G1
Intel Core m5-6Y54, 2x 1.10GHz
8 GB RAM
256 GB M.2 SATA SSD
Digitizer-Pen + Travel Keyboard
LTE, NFC, Bluetooth® 4.2
Intel®  Wireless-AC 18260 802.11a/b/g/n/ac
3 Years warranty


Regards, Bernhard

---

### Post by baumber on 2016-03-01
I have tested the tablet with a Kubuntu 16.04 live-usb-stick (built: 20160229) at a HP-demo-day:

The bootup was fast with a usb 3.0 stick: no crashes


[LIST]
[*] WLAN: Only scanning tested, no connection established , Wifi was detected correctly 
[*]Touchscreen: Works, like a mouse, no gestures 
[*]Keyboard + Touchpad + Docking: Works , special keys for brightness control were not working, but with the built-in KDE-applet brightness control was possible 
[*]Docking and undocking the keyboard/touchpad from the tablet works fine (detected as usb device) 
[*]Opengl with KDE effects is no problem (Skylake Graphics) 
[*]Volume control buttons on the left side do not work 
[*]Webcams not tested 
[*]Digitizer-Pen works on the touchscreen 
[*]LTE WWAN + Bluetooth not tested 
[*]Only USB Type A 3.0 tested with the live usb-stick , usb-c 3.1 not tested 
[*]Battery was detected 
[*]Sound not tested 
[/LIST]

---

### Post by fmsafar on 2016-03-02
I´ve got my x2 1012 G1 two days ago. I shrinked the Win10 partition using the Windows DiskManger and installed Ubuntu 15.10 Desktop in the free space without any problems. Grub2 detects the Win10 installation so I can select at the Grub screnn wether to boot Win10 or Ubuntu.

In addition to the above I can say:
- Bluetooth is working
- Audio is working
- external Monitor attached via USB-C to HDMI Adapter is working
- WLAN connection is working but it seems to rescan quite often and interrupts connection from time to time but reconnects automatically
- The pressure sensitivity of the pen is recognised by MyPaint.

There is one strange effect with the menu bar: When the menu bar is displayed on top of the screen (standard setting in Ubuntu) everything works fine, but if the menubar is displayed on top of the application window it works fine when using the external bluetooth mouse or by using the pen, but with the touchpad I cannot select the main menu entries. After opening a main entry by keyboard shortcut (or any other method) I can use the touchpad again to select any subitems or even to change to another main item as long as one main item is open.

---

### Post by baumber on 2016-03-02
Hello fmsafar,

thank you for the feedback!

I have some questions:

Are the webcams working ?

Have you tested the virtual keyboard app onboard?

Is stable working possible, or are there sometimes crashes in Ubuntu?

I assume, the uefi grub install worked fine?

Can you please post/upload the following files/cmd outputs to have an overview about the detected hardware?



dmesg > ELITEX2-dmesg.txt

sudo cat /var/log/syslog >  ELITEX2-syslog.txt

glxinfo > ELITEX2-glx.txt

sudo lspci -vvnn > ELITEX2-lspci.txt

sudo lsusb -vv > ELITEX2-lsusb.txt

sudo cat /var/log/Xorg.0.log > ELITEX2-xorg.txt

lsmod > ELITEX2-lsmod.txt

lsscsi > ELITEX2-lsscsi.txt

acpitool -e > ELITEX2-acpi.txt

cat /proc/cpuinfo  > ELITEX2-cpu.txt

sudo lshw > ELITEX2-lshw.txt

sudo dmidecode > ELITEX2-dmi.txt

xrandr --verbose > ELITEX2-xrandr.txt


Thanks

---

### Post by fmsafar on 2016-03-03
The frontcam is working but I found no way to switch to the backcam. Even in VLC only /dev/video0 can be selected as video recording device so it seems that the backcam is not recognised by the kernel.

The virtual keyboard is working.

Stable working is possible I had no crashes until now the only issue is that with the WLAN interruptions, these problem you can see in dmesg and syslog too.

You can find the requested log files in [https://www.dropbox.com/s/7ylkgak0wfawyu6/u%40x21012.tar.gz?dl=0](https://www.dropbox.com/s/7ylkgak0wfawyu6/u%40x21012.tar.gz?dl=0)

I´ve tried to boot the beta1 from Ubuntu 16.04 from an USB stick and there was no problem with WLAN. But when I tried to install it to a local partition the installer crashed and I´ve sent a bug report.

---

### Post by stefan39 on 2016-03-03
Hello,

great news, that the HP Elite X2 1012 works so well on Linux.

Can anyone confirm, that suspend/resume works?

Thanks.

---

### Post by fmsafar on 2016-03-03
Yes suspend/resume works. 

I just could not manage to get a virtual keboard on the resume screen, so I needed the keyboard to unlock. Does anybody know how to configure that?

---

### Post by stefan39 on 2016-03-03
Thanks for your answer.

I hope these threads will help you with your login problem:

[http://ubuntuforums.org/showthread.php?t=553961](http://ubuntuforums.org/showthread.php?t=553961)
[http://ubuntuforums.org/showthread.php?t=304045](http://ubuntuforums.org/showthread.php?t=304045)

---

### Post by baumber on 2016-03-03
Hello fmsafar,

thank you for the outputs!

Good to hear that the tablet is working fine under Linux.

There are Signal processing controllers and a Multimedia controller visible via lshw. Maybe the second webcam is among these. 

In the specs of HP the following is written: 1080p-FHD-Webcam with 2 MP front; 1080p-FHD-Webcam with 5 MP back => no vendor information

---

### Post by fmsafar on 2016-03-15
I´ve discovered a new problem. Audio worked with the attached USB 3.0 port replicator only. The internal audio is not working, if the port replicator is disconnected, only dummy output is shown in the audio settings.
Are there any ideas how to fix that?

---

### Post by gaussian on 2016-04-29
I am totally shooting in the dark here, since I haven't bought mine yet. Anyways, for Spectre X360 the following fixes the sound: [http://askubuntu.com/questions/600528/is-ubuntu-compatible-with-the-hp-spectre-x360](http://askubuntu.com/questions/600528/is-ubuntu-compatible-with-the-hp-spectre-x360)

Maybe worth testing with Elite X2? Both HP models of similarity vintage.

---

### Post by baumber on 2016-05-16
@fmsafar:

Please try Ubuntu 16.04 kernel 4.4 or test with a vanilla kernel
Link:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

The Skylake audio support is still being worked on:
[https://www.phoronix.com/scan.php?page=news_item&px=Sound-Updates-For-Linux-4.6](https://www.phoronix.com/scan.php?page=news_item&px=Sound-Updates-For-Linux-4.6)

@gaussian:

In my opinion, do not buy this tablet, because there are a lot of bugs in hardware and software (BIOS).

see link:
[http://forum.tabletpcreview.com/threads/hp-elite-x2-1012-discussion-thread.68692/page-49](http://forum.tabletpcreview.com/threads/hp-elite-x2-1012-discussion-thread.68692/page-49)

I brought back this device to the distributor and got my money back.

The reviews are good, but there is no long-term test, so it is better to look at the user forum discussions.

Review; good rating , but useless, when the hardware and software is in beta stage.
[http://www.notebookcheck.net/HP-Elite-x2-1012-G1-Convertible-Review.164293.0.html](http://www.notebookcheck.net/HP-Elite-x2-1012-G1-Convertible-Review.164293.0.html)

---

### Post by stefan39 on 2016-06-09
My HP Elite X2 works with this configuration well:
BIOS: 01.13 Rev.A
Thunderbolt firmware: 16.1.7.0.6 Rev.A
OS: Ubuntu Gnome 16.04
Kernel: 4.6

It is very important to update the BIOS and Thunderbolt firmware. I haven't tested the BIOS versions higher than 01.13 Rev.A.

Things, which work:
[LIST]
[*]keyboard with mousepad 
[*]touchscreen 
[*]USB-A 
[*]USB-C (power, USB and HDMI with Anker Premium USB-C Hub) 
[*]loudspeakers (internal audio is working) 
[*]microphone 
[*]headset jack 
[*]standby 
[*]WLAN 
[*]Bluetooth 
[*]frontcamera 
[/LIST]

Things, which are buggy:
[LIST]
[*]the sound of the HDMI of the USB-C hub. 
[/LIST]

Things, which don't work:
[LIST]
[*]LTE module ([https://forum.ubook.at/index.php?page=Thread&threadID=3308](https://forum.ubook.at/index.php?page=Thread&threadID=3308) doesn't work for me) 
[*]Wacom pen 
[*]backcamera 
[/LIST]

Things, which are not tested:
[LIST]
[*]Thunderbolt dock 
[/LIST]

As virtual keyboard I use onboard, which works very well.

Is anyone able to use the LTE module, the Wacom pen, the backcamera or even the Thunderbolt dock?

---

### Post by stefan39 on 2016-08-04
I updated the BIOS to version 1.16 and the kernel to version 4.7. All things work just as before.

I tested the Thunderbolt dock. Unfortunately, it doesn't work.

---

### Post by Jan_Drewes on 2017-02-11
I'd like to add a few cents myself. I am running Kubuntu 16.10 on my Elite X2 1012 G1, 8GB m5, and almost everything is working.

-Screen works
-Touchscreen works
-Wacom pen works (Touchscreen can be disabled separately, meaning you can then rest your hands fully on the screen and still use the pen)
-Front camera works
-Suspend and Hibernate work, but:
-Bluetooth works, but stops working after suspend. ```
rmmod btusb && modprobe btusb
``` solve the problem - but that's inconvenient if you are using a bluetooth keyboard like me.
-Wifi works

I have no 4G/LTE installed.

-The backcamera doesn't work. No idea how to activate it, there seems to be no driver around that would be able to claim it.
-Fingerprint reader doesn't work. There seems to be binary blob floating around, but it's unfree and requires recompilation of the fingerprint libraries, which I have not done (yet).

I tried a Dell DA200 thunderbolt mini dock, and it worked fine.

There appears to be ways to make the screen rotate automatically, but I currently don't want that so I didn't try.

If anyone has any clue how to make the back camera work, I'd really appreciate a tip!

---

