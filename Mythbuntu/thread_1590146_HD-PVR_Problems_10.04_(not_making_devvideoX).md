---
title: "HD-PVR Problems 10.04 (not making /dev/videoX)"
date: 2010-10-07
forum: Mythbuntu
---

### Post by Jynxter on 2010-10-07
So Box history. 
Started as a Mythbuntu 8.04 box, and have upgraded it to where it is now, 10.04.  
```
uname -a 
Linux matxmyth 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 0:26:08 UTC 2010 i686 GNU/Linux  
```Have HD Homerun recording with no problems to the box for 2 years now.   Purchased a HD-PVR, and have encountered problems getting it to work.  Installed it in windows, did the driver/firmware update from the support page. Made sure it works in windows for my sanity test.

However in mythbuntu, it just doesn't work. if I modprobe the driver, it loads, but never makes a /dev/videoX device. 

When I do modprobe the driver I get this: 
```
Oct  7 00:17:31 matxmyth kernel: [  230.201682] usbcore: registered new interface driver hdpvr  
```and nothing after that. 
lsusb:
```
lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 2040:4903 Hauppauge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I've downloaded and recompilied v4l-dvb modules to no avail. I've tried different USB ports, power cycling the hd-pvr, rebooting, and just nothing seems to work. I don't see anything in dmesg, /var/log/messages,syslog,kernel that gives me any idea about what the problem is.

the Hauppage_HD_PVR is listed in /var/log/udev if that matters.

I'm not sure why its not working, and could use any assistance is determining whats going on.

Thanks!

---

### Post by LowSky on 2010-10-07
Hmmm odd issue.

Bus 001 Device 002: ID 2040:4903 Hauppauge
thats the device.

run this command to make sure the driver is installed ```
locate cx88-dvb.ko |grep `uname -r`

```

try a test using

cat /dev/video1 > test.ts
 just give it a try once If it works reboot and startinstalling it in Myth

Otherwise go back to the windows machine and reinstall the drivers once again.

---

### Post by Jynxter on 2010-10-07
found the correct cx88 file. Reloaded the driver (HcwDriverInstall.exe) in windows
Here is the message log when I power cycle the hd-pvr while its connected

```
Oct  7 12:49:11 matxmyth kernel: [  124.448985] usb 1-4: USB disconnect, address 3
Oct  7 12:49:17 matxmyth kernel: [  130.640044] usb 4-1: new full speed USB device using ohci_hcd and address 2
Oct  7 12:49:18 matxmyth kernel: [  131.264031] usb 4-1: new full speed USB device using ohci_hcd and address 3
Oct  7 12:49:20 matxmyth kernel: [  133.792044] usb 1-4: new high speed USB device using ehci_hcd and address 5
Oct  7 12:49:20 matxmyth kernel: [  133.952443] usb 1-4: configuration #1 chosen from 1 choice
Oct  7 12:51:03 matxmyth kernel: [  236.915304] usbcore: registered new interface driver hdpvr


```

on bootup, the hdpvr module is not being loaded. The Last line shows up after I modprobe hdpvr. Nothing goes after that.

there is no /dev/video0 or /dev/video1 to capture from. Just gives me a no such file/directory.






> **LowSky said:**
> Hmmm odd issue.

Bus 001 Device 002: ID 2040:4903 Hauppauge
thats the device.

run this command to make sure the driver is installed ```
locate cx88-dvb.ko |grep `uname -r`

```try a test using

cat /dev/video1 > test.ts
 just give it a try once If it works reboot and startinstalling it in Myth

Otherwise go back to the windows machine and reinstall the drivers once again.

---

### Post by LowSky on 2010-10-07
run this command

```
dmesg | grep hdpvr
```

you should see something similar to this. 

```
john@jpc-desktop:~$  dmesg | grep hdpvr
[    5.657199] hdpvr 1-5:1.0: untested firmware version 0x15, the driver might not work
[    5.970462] hdpvr 1-5:1.0: device now attached to video0
[    5.970496] usbcore: registered new interface driver hdpvr
```

if not the device isn't loading correctly.

---

### Post by LowSky on 2010-10-07
ok I might have found something
[http://forums.gentoo.org/viewtopic-t-815587-view-previous.html?sid=13249a4bba5b5656eed491f346979bb3](http://forums.gentoo.org/viewtopic-t-815587-view-previous.html?sid=13249a4bba5b5656eed491f346979bb3)
[http://mythtv.org/pipermail/mythtv-users/2010-February/281462.html](http://mythtv.org/pipermail/mythtv-users/2010-February/281462.html)


what is the output of 

```
modinfo hdpvr
```
if it comes up empty you might need to edit the hdpvr driver to include your model

you might have to modify the driver to add your model of the hdpvr so it works
look for
```
**4903**
``` like in this 

```
alias:          usb:v2040p**4903**d*dc*dsc*dp*ic*isc*ip*
```
 if you dont see it you will have to modify the driver.
I noticed my version of the driver doesn't use it. but i'm using the Ubuntu kernel driver and not the v4l driver


Your model might be so new its not included in the kernel yet. sorry to break the news to you. but a simple modification could fix it.

---

### Post by Jynxter on 2010-10-07
```
dmesg | grep hdpvr
[  236.915304] usbcore: registered new interface driver hdpvr
```
Hmm, heres modinfo and lsusb again

```
paul@matxmyth:/var/cache/apt/archives$ dmesg | grep hdpvr
[  236.915304] usbcore: registered new interface driver hdpvr
paul@matxmyth:/var/cache/apt/archives$ modinfo hdpvr
filename:       /lib/modules/2.6.32-25-generic/kernel/drivers/media/video/hdpvr/hdpvr.ko
description:    Hauppauge HD PVR driver
author:         Janne Grunau
license:        GPL
srcversion:     B42A1796FAC59BB0C93FE94
alias:          usb:v2040p4982d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4900d*dc*dsc*dp*ic*isc*ip*
depends:        videodev,v4l2-common
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586
parm:           video_nr:video device number (-1=Auto) (array of int)
parm:           hdpvr_debug:enable debugging output (int)
parm:           default_video_input:default video input: 0=Component / 1=S-Video / 2=Composite (uint)
parm:           default_audio_input:default audio input: 0=RCA back / 1=RCA front / 2=S/PDIF (uint)
parm:           boost_audio:boost the audio signal (bool)
paul@matxmyth:/var/cache/apt/archives$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 2040:4903 Hauppauge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Looks like I have 4903 and the driver only has 4902

Great find there!!

Thats a huge point in the right direction thats for sure.

So I need to modify the v4l-dvb driver and add in another alias, then recompile I take it.

---

### Post by Jynxter on 2010-10-07
I found the alises in the hdpvr-mod.c file. Added 4903 and am recompiling.
I'll let you know how it goes...

---

### Post by Jynxter on 2010-10-07
Have to modify these two files to add a new Model Device to the code.

./v4l-dvb/linux/drivers/media/video/hdpvr/hdpvr.h
I added ID4
```
/* Define these values to match your devices */
#define HD_PVR_VENDOR_ID        0x2040
#define HD_PVR_PRODUCT_ID       0x4900
#define HD_PVR_PRODUCT_ID1      0x4901
#define HD_PVR_PRODUCT_ID2      0x4902
#define HD_PVR_PRODUCT_ID3      0x4982
#define HD_PVR_PRODUCT_ID4      0x4903
```./v4l-dvb/linux/drivers/media/video/hdpvr/hdpvr-core.c
Added ID4 here too.
```
/* table of devices that work with this driver */
static struct usb_device_id hdpvr_table[] = {
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID1) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID2) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID3) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID4) },
        { }                                     /* Terminating entry */
};
```make clean
sudo make install
sudo reboot

dmesg | grep hdpvr:
```
paul@matxmyth:~$ dmesg | grep hdpvr
[   12.788568] hdpvr 1-4:1.0: untested firmware version 0x15, the driver might not work
[   13.100908] hdpvr 1-4:1.0: device now attached to video0
[   13.100937] usbcore: registered new interface driver hdpvr

```Now to wait an hour to get home to start testing it out.. :P

---

### Post by Jynxter on 2010-10-08
After the recompile, everything is working in myth!

Lowsky, thanks for your help, that was an awesome find, and one more thing to add to the list of troubleshooting for myself with linux hardware.

---

### Post by LowSky on 2010-10-08
Your welcome Jynxter, it was really an important find. I'm betting this might effect many new users if the driver is not properly updated in the kernel.

It also reminded me I should update my HDPVR's firmware.

---

### Post by tfreak on 2010-10-11
> **Jynxter said:**
> After the recompile, everything is working in myth!

Lowsky, thanks for your help, that was an awesome find, and one more thing to add to the list of troubleshooting for myself with linux hardware.


Jynxter, I think I have the same problem that you started the thread with.  I have a hdpvr with 4903 in the id.  Using the same mods that you did to add that to the product ID list, I too am able to get /dev/videoX to show up.

But, I haven't advanced beyond that.  When I try to test /dev/video0 with cat, I get an i/o error.  /var/log/messages shows that hdpvr found 0 for width/length/fps, and then fails to open the stream.  

i tried to ignore the cat error, and went to mythtv.  but mythtv barfs on live tv.  curiously though, when i try to do livetv on myth, it doesn't cause anything onto /var/log/messages.

what version of the hdpvr folder are you using?  from kernel (which #), or from linuxtv.org directly?  I tried the latest kernel ad thing from linuxtv.org, adding the 4903 thing to them, but I get the same /var/log/messages line when I cat. and mythtv doesn't pick any thing up.

---

### Post by Jynxter on 2010-10-12
I downloaded the v4l-dvb drivers and recompiled the modules from it.

(this is a rough idea of what I think I did)
From the [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR) Page

sudo apt-get install build-essential mercurial linux-headers-`uname -r`
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb/linux/drivers/media/video/hdpvr/
nano hdpvr.h
  I added ID4
```
/* Define these values to match your devices */
#define HD_PVR_VENDOR_ID        0x2040
#define HD_PVR_PRODUCT_ID       0x4900
#define HD_PVR_PRODUCT_ID1      0x4901
#define HD_PVR_PRODUCT_ID2      0x4902
#define HD_PVR_PRODUCT_ID3      0x4982
#define HD_PVR_PRODUCT_ID4      0x4903
```./v4l-dvb/linux/drivers/media/video/hdpvr/hdpvr-core.c
Added ID4 here too.
```
/* table of devices that work with this driver */
static struct usb_device_id hdpvr_table[] = {
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID1) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID2) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID3) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID4) },
        { }                                     /* Terminating entry */
};
```cd back to the root v4l-dvb folder.
make sudo make install
reboot




other then that, I'm running mythbuntu 10.04 that has been upgraded from 8.x originally. 
Current Kernel is 2.6.32-25-generic.


Next I downloaded the 6200ch from here to use firewire to change channels on my Moto DCH-3200
[http://www.mythtv.org/wiki/6200ch](http://www.mythtv.org/wiki/6200ch) 
(made folder 6200ch, and then made a **6200ch.c** and **Makefile**)
copied 6200ch to /var/local/bin.
Then follwed this:
**Steps to Add the HD-PVR as a Capture Device in MythTV (0.22 or later) **

 
[LIST=1]
[*] Compile the driver and test it for proper operation as described above.
[*] Run mythtv-setup, and enter option 2, Capture Cards.
[*] Add a new capture card.  When prompted, select "H.264 Encoder  Card (HD-PVR)" as the card type.  Set the /dev/video node to the number  of your HD-PVR.  Finish adding the new capture card.  You can also set  the audio input on this screen.  All cables must be functional and  properly attached in order for capture to succeed with the HD-PVR.  If  every recording fails with a *"Unknown type, recording width was 0"* error in the mythbackend log, it is possible that one of your cables is faulty or has become disconnected.
[*] Enter option 3, "Video Sources."  Set up a video source for your HD-PVR's tuner as described in [ the manual]("http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend").
[*] Enter option 4, "Input Connections."  Connect the video source to the appropriate input on the HD-PVR.  **Important Note:** You *must*  set a channel change script for the HD-PVR to work properly.  If you  don't care about channel changes, you can set it to /bin/true, but there  absolutely must be a channel change script defined. **Important Note 2:** You *must* leave *Preset tuner to channel* empty or LiveTV and channel changes will not work.
[/LIST]

Pointed Channel change script to /var/local/bin/6200ch
Make sure you pay attention to "Preset Tuner" and leave it blank. Myth bombed every time till I caught that (it defaulted to 1st channel from my source)

After that everything was pretty peachy for the myth side.

I reccomend doing a "sanity check" and get the hd-pvr working in windows first, to make sure you have a working device.

---

### Post by Big Boy Stan on 2010-10-26
I have the same problem with my new HDPVR but my distro (Linhes -Arch) doesnt include any of the driver files. Does anyone know where I can get a copy of the new hdpvr.ko file that includes Product ID 4903?

---

### Post by LowSky on 2010-10-26
Big Boy Stan,. you will have to edit the driver to work like the OP did. Sorry no other workaround until the driver is fixed

---

### Post by phroman on 2010-10-26
Well, I seem to be in the same boat, using a fresh install of 10.10, HD PVR not working.  At the command line, typing: 

cat /dev/video0 > test.ts 

Does create a test file, so something's working, I 'm guessing the module isn't being loaded in mythtv?

I tried to follow Jynxter's instructions from reply #12, I edited the 2 files mentioned. When typing Make, I get this error at the bottom:

  ```
joe@Mythserver:~/Desktop$ cd /home/joe/Desktop/v4l-dvb
joe@Mythserver:~/Desktop/v4l-dvb$ make
make -C /home/joe/Desktop/v4l-dvb/v4l 
make[1]: Entering directory `/home/joe/Desktop/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.35-22-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/joe/Desktop/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/joe/Desktop/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/joe/Desktop/v4l-dvb/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/joe/Desktop/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-22-generic/build
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/joe/Desktop/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tuner-xc2028.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tuner-simple.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tuner-types.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/mt20xx.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tda8290.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tea5767.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tea5761.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tda9887.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/tda827x.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au0828-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au0828-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au0828-cards.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au0828-dvb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au0828-video.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au0828-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au8522_dig.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au8522_decoder.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-sram.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-eeprom.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-misc.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-hw-filter.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/flexcop-dma.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-driver.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-cards.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-if.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-risc.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-gpio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-input.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/bttv-audio-hook.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cpia2_v4l.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cpia2_usb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cpia2_core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-alsa-main.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-alsa-pcm.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-driver.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-cards.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-firmware.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-gpio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-queue.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-streams.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-fileops.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-ioctl.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-controls.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-mailbox.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-audio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-video.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-irq.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-av-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-av-audio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-av-firmware.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-av-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-scb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-dvb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx18-io.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-audio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-video.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-cards.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-avcore.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx231xx-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-cards.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-video.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-dvb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-417.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-ioctl.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-ir.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-input.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23888-ir.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/netup-init.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cimax2.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/netup-eeprom.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx23885-f300.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx25840-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx25840-audio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx25840-firmware.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx25840-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-video.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-mpeg.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-cards.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-tvaudio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-dsp.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cx88-input.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvbdev.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dmxdev.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb_demux.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb_filter.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb_ca_en50221.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb_frontend.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb_net.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb_ringbuffer.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb_math.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/av7110_hw.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/av7110_v4l.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/av7110_av.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/av7110_ca.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/av7110.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/av7110_ipack.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/av7110_ir.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/a800.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/af9005-remote.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/af9005.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/af9005-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/af9015.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/anysee.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/au6610.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/az6027.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/ce6230.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cinergyT2-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cinergyT2-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/cxusb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dib0700_core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dib0700_devices.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dibusb-common.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dibusb-mb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dibusb-mc.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/digitv.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dtt200u.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dtt200u-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dtv5100.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dw2102.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/ec168.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/friio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/friio-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/gl861.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/gp8psk.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/gp8psk-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/m920x.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/nova-t-usb2.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/opera1.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/ttusb2.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/umt-010.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/vp702x.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/vp702x-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/vp7045.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/vp7045-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb-usb-firmware.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb-usb-init.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb-usb-urb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb-usb-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb-usb-dvb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/dvb-usb-remote.o
/home/joe/Desktop/v4l-dvb/v4l/dvb-usb-remote.c: In function 'dvb_usb_remote_init':
/home/joe/Desktop/v4l-dvb/v4l/dvb-usb-remote.c:195: warning: assignment from incompatible pointer type
/home/joe/Desktop/v4l-dvb/v4l/dvb-usb-remote.c:196: warning: assignment from incompatible pointer type
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/usb-urb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/pt1.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/va1j5jf8007s.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/va1j5jf8007t.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/em28xx-audio.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/em28xx-video.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/em28xx-i2c.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/em28xx-cards.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/em28xx-core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/em28xx-input.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/em28xx-vbi.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/et61x251_core.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/firedtv-avc.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/firedtv-ci.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/firedtv-dvb.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/firedtv-fe.o
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/firedtv-fw.o
/home/joe/Desktop/v4l-dvb/v4l/firedtv-fw.c: In function 'model_name':
/home/joe/Desktop/v4l-dvb/v4l/firedtv-fw.c:254: warning: assignment discards qualifiers from pointer target type
/home/joe/Desktop/v4l-dvb/v4l/firedtv-fw.c: In function 'node_probe':
/home/joe/Desktop/v4l-dvb/v4l/firedtv-fw.c:280: warning: passing argument 1 of 'model_name' discards qualifiers from pointer target type
/home/joe/Desktop/v4l-dvb/v4l/firedtv-fw.c:244: note: expected 'u32 *' but argument is of type 'const u32 *'
  CC [M]  /home/joe/Desktop/v4l-dvb/v4l/firedtv-1394.o
/home/joe/Desktop/v4l-dvb/v4l/firedtv-1394.c:22: fatal error: dma.h: No such file or directory
compilation terminated.
make[3]: *** [/home/joe/Desktop/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/joe/Desktop/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/joe/Desktop/v4l-dvb/v4l'
make: *** [all] Error 2
joe@Mythserver:~/Desktop/v4l-dvb$ 
```

Granted I've never re-compiled a driver and modules before but I followed the instructions on the wiki and Jynxter's post closely.  No idea how to proceed now, any help?  Thanks guys!

---

### Post by LowSky on 2010-10-26
phroman can i see the output of the command ```
lsusb
```

if its being seen as /dev/video0 I think your issue is different

---

### Post by phroman on 2010-10-26
Hi LowSky, here's a few different output results:

lsusb
```
joe@Mythserver:~/Desktop$ lsusb
Bus 008 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 008 Device 002: ID 05af:0802 Jing-Mold Enterprise Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0bc7:0008 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2040:4902 Hauppauge HD PVR
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@Mythserver:~/Desktop$ 
```

dmesg | grep hdpvr
```
joe@Mythserver:~/Desktop$ dmesg | grep hdpvr
[   11.709462] hdpvr 2-4:1.0: untested firmware version 0x15, the driver might not work
[   12.008733] hdpvr 2-4:1.0: device now attached to video0
[   12.008754] usbcore: registered new interface driver hdpvr
```

modinfo hdpvr

```
joe@Mythserver:~/Desktop$ modinfo hdpvr
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/media/video/hdpvr/hdpvr.ko
description:    Hauppauge HD PVR driver
author:         Janne Grunau
license:        GPL
srcversion:     F9BCAADA7960A2E15A08EBA
alias:          usb:v2040p4982d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4900d*dc*dsc*dp*ic*isc*ip*
depends:        videodev,v4l2-common
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           video_nr:video device number (-1=Auto) (array of int)
parm:           hdpvr_debug:enable debugging output (int)
parm:           default_video_input:default video input: 0=Component / 1=S-Video / 2=Composite (uint)
parm:           default_audio_input:default audio input: 0=RCA back / 1=RCA front / 2=S/PDIF (uint)
parm:           boost_audio:boost the audio signal (bool)
joe@Mythserver:~/Desktop$ 
```

modprobe hdpvr
```
joe@Mythserver:~/Desktop/v4l-dvb$ sudo modprobe hdpvr
WARNING: All config files need .conf: /etc/modprobe.d/lirc-blacklist, it will be ignored in a future release.
```

Did I mess things up with attempting to re-compile the driver?  Thanks for the help.

---

### Post by LowSky on 2010-10-27
you have the older model so you didnt need to instal the driver
follow this link for help adding the device to mythtv
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Add_the_HD-PVR_as_a_Capture_Device_in_MythTV_.280.22_or_later.29](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Add_the_HD-PVR_as_a_Capture_Device_in_MythTV_.280.22_or_later.29)

---

### Post by phroman on 2010-10-27
I've done those steps actually, configured in mythbackend, all settings are ones that I used in my last working setup.  Since I can record running:

```
cat /dev/video0 > test.ts
```

Would it seem to be a mythtv driver or module?  Thanks again

---

### Post by phroman on 2010-10-27
Well, I went ahead and just re-installed.  

I added the HD PVR in the backend, its not working in mythfrontend to watch live tv.  At least I'm at at clean a beginning ..

---

### Post by LowSky on 2010-10-27
> **phroman said:**
> Well, I went ahead and just re-installed.  

I added the HD PVR in the backend, its not working in mythfrontend to watch live tv.  At least I'm at at clean a beginning ..

Did you install a channel listing and a channel changing command?

Did you load the firmware onto the device from a Windows based machine as instructed by the same guide I posted?

after trying that cat /dev/video0 > test.ts test did you reboot the computer and the hdpvr? if no all of these things can be issues.

---

### Post by phroman on 2010-10-27
Hey LowSky, yes, I did install a channel listing and a channel changing command and channel changing script, the script is executable.

I loaded the firmware on a windows machine.

Right now from this new install, running: cat /dev/video0 > test.ts results in the hdpvr recording a test.ts file on my desktop.  I can't hear audio when playing the file back with vlc.

I do see this flash by during boot up.

```
modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or direcory.

```

lsusb
```
Bus 002 Device 003: ID 2040:4902 Hauppauge HD PVR
```

dmesg | grep usb
```
[   13.151776] usbcore: registered new interface driver usbhid
[   13.151777] usbhid: USB HID core driver
[   13.340368] usbcore: registered new interface driver hdpvr
joe@Mythserver1:~/Desktop$ 

```

dmesg | grep hdpvr
```
joe@Mythserver1:~/Desktop$ dmesg | grep hdpvr
[   13.010993] hdpvr 2-4:1.0: untested firmware version 0x15, the driver might not work
[   13.340350] hdpvr 2-4:1.0: device now attached to video0
[   13.340368] usbcore: registered new interface driver hdpvr
joe@Mythserver1:~/Desktop$ 
```


In the install guide it says:  As of Linux Kernel 2.6.30 the driver for the HD-PVR is now included by default. No compiling of the driver will be necessary assuming you have compiled the driver into the kernel.  The HD-PVR driver is now included in v4l-dvb.  

I don't have a v4l-dvb directory.  Should I try to re-compile the driver as stated in the guide again?

lsmod
```

joe@Mythserver1:~/Desktop$ lsmod
Module                  Size  Used by
nfsd                  241120  13 
exportfs                3449  1 nfsd
nfs                   274966  0 
lockd                  65605  2 nfsd,nfs
fscache                46361  1 nfs
nfs_acl                 2257  2 nfsd,nfs
auth_rpcgss            33937  2 nfsd,nfs
nvidia               9329739  28 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  0 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
sunrpc                193178  14 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
hdpvr                  19894  0 
v4l2_common            17329  1 hdpvr
lirc_atiusb            13123  0 
asus_atk0110           11423  0 
usbhid                 36882  0 
videodev               43098  2 hdpvr,v4l2_common
v4l1_compat            13359  1 videodev
snd                    49006  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lirc_dev                9510  1 lirc_atiusb
hid                    67742  1 usbhid
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
intel_agp              26360  0 
agpgart                32011  2 nvidia,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  1 lp
pata_marvell            2312  0 
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
ahci                   19013  0 
atl1e                  29331  0 
libahci                21667  1 ahci
joe@Mythserver1:~/Desktop$ 

```


Thanks again for the help, I really appreciate it.

---

### Post by dannyboy79 on 2010-11-18
hey guys, i am interested in capturing HD gameplay within ubuntu not really through Mythtv though. Is there a GUI for starting and stopping capture for Ubuntu that anyone is aware of? If not, I know a simple cat /dev/video0 > gameplay.? would work. What type is the file though, .m2ts, .ts or what? I am asking because I would be using Kdenlive to edit my gameplay capture to add commentary, cuts, transitions, and what not. ANy help would be appreciated. I have read the AVCHD is not a very friendly format to perform video editing in (for kdenlive that is) so if it's AVCHD I would need to transcode it first but i wonder how much quality i'll lose.

---

### Post by LowSky on 2010-11-18
use the quick and easy terminal command. 
cat /dev/video1 > videoname.ts


Video is H264  and sound is AAC by default.

visit the [mythtv hdpvr wiki]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") for details on changing the video settings from terminal.

I had to change the sound output to AC3 because my PS3 couldn't play the video files.

---

### Post by dannyboy79 on 2010-11-19
> **LowSky said:**
> use the quick and easy terminal command. 
cat /dev/video1 > videoname.ts


Video is H264  and sound is AAC by default.

visit the [mythtv hdpvr wiki]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") for details on changing the video settings from terminal.

I had to change the sound output to AC3 because my PS3 couldn't play the video files.
interesting that it's h264 and aac but it's packed in the .ts container? OR can I just put it in any extension (container) like .avi? 
```
cat /dev/video1 > filename.avi
```
It's just that I have read bad stories about kdenlive (a non-linear video editor) working with AVCHD files due to a seeking problem but then again that might only be from certain HD camera's output. OR am I mistaken and .ts is something else. I am new to the HD recording scene and really only know formats for SD capture like avi type 2 and mpeg etc etc. I'll check out the wiki on it thanks. As I said, my end goal is to get teh captured files into kdenlive and make edits, cuts, etc etc. I wonder if anyone here could take a .ts file captured from their HD-PVR and bring it into kdenlive for me and see if you can seek, make cuts, etc etc and tell me your experience before I go and spend $200.00.  Thanks for your help thus far.

---

### Post by fullmoonguru on 2010-12-04
Hopefully Jynxster or LowSky can help me.  I am n the sam spot as Jynxster.  Here is the output of my modinfo hdpvr:

```
modinfo hdpvr
filename:       /lib/modules/2.6.32-26-server/kernel/drivers/media/video/hdpvr/hdpvr.ko
description:    Hauppauge HD PVR driver
author:         Janne Grunau
license:        GPL
srcversion:     9E493050A99F9F194A6B10B
alias:          usb:v2040p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4900d*dc*dsc*dp*ic*isc*ip*
depends:        videodev,v4l2-common
vermagic:       2.6.32-26-server SMP mod_unload modversions 
parm:           video_nr:video device number (-1=Auto) (array of int)
parm:           hdpvr_debug:enable debugging output (int)
parm:           default_video_input:default video input: 0=Component / 1=S-Video / 2=Composite (uint)
parm:           default_audio_input:default audio input: 0=RCA back / 1=RCA front / 2=S/PDIF (uint)
parm:           boost_audio:boost the audio signal (bool)
```So it's not showing my 4903.  I added the ID4/4903 line to both of the driver files that Jynxster showed, cd'd to the v4l-dvb directory & ran

```
make clean
sudo make install 
sudo reboot
```Same thing with no /dev/videoX

I didn't do anything with the .ko file.  Was I supposed to?

I also got errors iwhen I ran the kernal install, o v4l make?  A bunch of them are 1394 errors which I assume is because I'm not using a firewire, but there are some others at the bottom:

                     p { margin-bottom: 0.08in; }```
/home/mammy/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':  
 /home/mammy/v4l-dvb/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'  
 make[3]: *** [/home/mammy/v4l-dvb/v4l/firedtv-1394.o] Error 1  
 make[2]: *** [_module_/home/mammy/v4l-dvb/v4l] Error 2  
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-26-server'  
 make[1]: *** [default] Error 2  
 make[1]: Leaving directory `/home/mammy/v4l-dvb/v4l'  
 make: *** [all] Error 2  

```

---

### Post by fullmoonguru on 2010-12-12
Anyone?  Getting kind of desperate.  Spent $200 on this thing & can't use it.  Running out of recordings to watch.  What will I do now, what TV with commercials???

---

### Post by MonsterMaxx on 2010-12-13
I've been in a similar boat as you, mine started as a v8 and got to v10.04, then it got bollixed.  Sometimes with Linux (and windoze) it just gets to the point where you need a clean install.
True some folks are linux experts and can fix stuff like this, but I think you and I are in the same boat, knowing just enough to be dangerous.

Back up your database and reinstall the os clean.

When I did this w/ 10.10 I couldn't believe how much faster it ran.  Very noticeable.  
And much much more stable too (I was having a lot of crashing problems and PVRs not being recognized on boot so I'd have to test them every time and often reboot several times before everything was working.)

W/ 10.10 the HDPVR loaded fine and cohabitates w/ a PVR350 and PVR500.

Good luck

---

### Post by fullmoonguru on 2010-12-14
Interesting about 10.10.  Unfortunately, this is also my server for my small bus., so a reinstall is a bit more complicated.  And my whole thing was to stick with the LTS release exactly for the reason of stability...

---

### Post by newlinux on 2010-12-14
> **fullmoonguru said:**
> Hopefully Jynxster or LowSky can help me.  I am n the sam spot as Jynxster.  Here is the output of my modinfo hdpvr:

```
modinfo hdpvr
filename:       /lib/modules/2.6.32-26-server/kernel/drivers/media/video/hdpvr/hdpvr.ko
description:    Hauppauge HD PVR driver
author:         Janne Grunau
license:        GPL
srcversion:     9E493050A99F9F194A6B10B
alias:          usb:v2040p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4900d*dc*dsc*dp*ic*isc*ip*
depends:        videodev,v4l2-common
vermagic:       2.6.32-26-server SMP mod_unload modversions 
parm:           video_nr:video device number (-1=Auto) (array of int)
parm:           hdpvr_debug:enable debugging output (int)
parm:           default_video_input:default video input: 0=Component / 1=S-Video / 2=Composite (uint)
parm:           default_audio_input:default audio input: 0=RCA back / 1=RCA front / 2=S/PDIF (uint)
parm:           boost_audio:boost the audio signal (bool)
```So it's not showing my 4903.  I added the ID4/4903 line to both of the driver files that Jynxster showed, cd'd to the v4l-dvb directory & ran

```
make clean
sudo make install 
sudo reboot
```Same thing with no /dev/videoX

I didn't do anything with the .ko file.  Was I supposed to?

I also got errors iwhen I ran the kernal install, o v4l make?  A bunch of them are 1394 errors which I assume is because I'm not using a firewire, but there are some others at the bottom:

                     p { margin-bottom: 0.08in; }```
/home/mammy/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':  
 /home/mammy/v4l-dvb/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'  
 make[3]: *** [/home/mammy/v4l-dvb/v4l/firedtv-1394.o] Error 1  
 make[2]: *** [_module_/home/mammy/v4l-dvb/v4l] Error 2  
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-26-server'  
 make[1]: *** [default] Error 2  
 make[1]: Leaving directory `/home/mammy/v4l-dvb/v4l'  
 make: *** [all] Error 2  

```


I'm on 10.04 and I had those compilation errors too. I fixed it by editing "v4l/.config" and changing the line that says "firedtv=m" to "firedtv=n" to skip compiling that then it compiled fine. My research indicated it was due to an error in the packaging of the kernel headers.

---

### Post by fullmoonguru on 2010-12-17
Newlinux, thank yooouu!  That was it.  Compiled fine & set up without problems!  Man. that was a long & frustrating one, thanks again-

---

### Post by newlinux on 2010-12-17
> **fullmoonguru said:**
> Newlinux, thank yooouu!  That was it.  Compiled fine & set up without problems!  Man. that was a long & frustrating one, thanks again-

glad to help. Happy mythbuntuing :)

---

### Post by Jynxter on 2010-12-17
Sorry for not seeing this thread in awhile O.o, have been out of touch with TV for awhile and have not needed it working till tonite :P

Funny how I updated my kernel, and it broke, and I had to come here to remember what I did in the first place to fix it :P

Until the drivers are updated to the latest version this is the only workaround for new Model HDPVRs but at least we have a somewhat guide to fixing it.

I submitted bugs to the kernel tracker, but doesnt look like anyone has fixed it yet, so some of us are still out in the cold with manual patching for now.

Thanks to the other regulars helping out too!

---

### Post by ceenvee703 on 2010-12-25
I want to second the thanks to newlinux and his fix to allow the drivers to compile. I saw the errors after the "make" command and figured it was bad, but had no idea how to fix it. Once I happened across this thread, I made the change, did a make and make install, and I'm happily recording HD. Thanks!

---

### Post by fullmoonguru on 2010-12-26
I have upgraded to .24 & I'm back in (almost) the same situation.  Again, my 4903 is not showing up when I run modinfo.  The two files have retained the 4903 ID4 stuff, the n is in the other file so I'm not getting compilation errors.  No /dev/video0 though, and running dmesg | grep hdpvr doesn't give me any output.

---

### Post by Jynxter on 2010-12-26
> **fullmoonguru said:**
> I have upgraded to .24 & I'm back in (almost) the same situation.  Again, my 4903 is not showing up when I run modinfo.  The two files have retained the 4903 ID4 stuff, the n is in the other file so I'm not getting compilation errors.  No /dev/video0 though, and running dmesg | grep hdpvr doesn't give me any output.

 I redownloaded the source for v4l, edited the files for the 4903, commented out the failing module, (listed a few posts ago) then the standard make, sudo make install, reboot and that fixed it.

---

### Post by fullmoonguru on 2010-12-27
Thanks Jynx, removing & reinstalling it worked.

---

### Post by vronp on 2010-12-27
Unfortunately, this does not appear to be fixed in 10.10.  I have a device ID of 4903 but am experiencing the same problems.

---

### Post by vronp on 2010-12-27
Jynxter, can you provide a hint as to how to get the source code installed along with the 10.04 distribution?  I don't have these files installed.                                                       I appreciate the help!
> **Jynxter said:**
> Have to modify these two files to add a new Model Device to the code.

./v4l-dvb/linux/drivers/media/video/hdpvr/hdpvr.h
I added ID4
```
/* Define these values to match your devices */
#define HD_PVR_VENDOR_ID        0x2040
#define HD_PVR_PRODUCT_ID       0x4900
#define HD_PVR_PRODUCT_ID1      0x4901
#define HD_PVR_PRODUCT_ID2      0x4902
#define HD_PVR_PRODUCT_ID3      0x4982
#define HD_PVR_PRODUCT_ID4      0x4903
```./v4l-dvb/linux/drivers/media/video/hdpvr/hdpvr-core.c
Added ID4 here too.
```
/* table of devices that work with this driver */
static struct usb_device_id hdpvr_table[] = {
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID1) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID2) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID3) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID4) },
        { }                                     /* Terminating entry */
};
```make clean
sudo make install
sudo reboot

dmesg | grep hdpvr:
```
paul@matxmyth:~$ dmesg | grep hdpvr
[   12.788568] hdpvr 1-4:1.0: untested firmware version 0x15, the driver might not work
[   13.100908] hdpvr 1-4:1.0: device now attached to video0
[   13.100937] usbcore: registered new interface driver hdpvr

```Now to wait an hour to get home to start testing it out.. :P

---

### Post by newlinux on 2010-12-27
> **vronp said:**
> Jynxter, can you provide a hint as to how to get the source code installed along with the 10.04 distribution?  I don't have these files installed.                                                       I appreciate the help!

See post #12 from this thread or the Mythtv HD-PVR wiki for instructions.

---

### Post by vronp on 2010-12-28
> **newlinux said:**
> See post #12 from this thread or the Mythtv HD-PVR wiki for instructions.


Does it matter where the v4l-dvb is put prior to editing and compiling ?

---

### Post by vronp on 2010-12-28
Folks may run into these issues:

[http://ubuntuforums.org/archive/index.php/t-1337146.html](http://ubuntuforums.org/archive/index.php/t-1337146.html)

---

### Post by newlinux on 2010-12-29
> **vronp said:**
> Does it matter where the v4l-dvb is put prior to editing and compiling ?

As long as there is space for it and proper permissions for the person compiling it, not it doesn't. The "make install" step puts everything in the right place for it to work.

---

### Post by hansum_rahul on 2011-01-10
I have a **6000:0001** Device from Kanry (Alaska Technovision)... They sell it as SuperTV **USB 2.0 TV BOX** in India. Imported from China.

It does not work on **Ubuntu Maveric Meerkat 10.04** (actually a** Mint 10 **which is based on that)... and my kernel is **2.6.35-24-generic**

Right now I am compiling the entire v4l-dvb tree, lets see...

---

### Post by fullmoonguru on 2011-01-29
Back at the same place again, after doing an update.  Thought I had this figured out.  Here's what I did:

Deleted the v4l folder

Ran:pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }a:link {  }  [B]hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Made the changes in the hdpvr.h & hdpvr-core.c files

Ran:[/B]****[B]

cd v4l-dvb[/B] **make clean** make 
Got the compiling errors, so I changed  all the =m's to =n's, & changed the video hdpvr line back to =m

Ran 

make clean
make
sudo make install
sudo reboot

I must be doing something out of order, the the hg clone file isn't right, I don't know.  I thought it was the same as what I did last time, but I'm back to nt having a /dev/videoX file

[B]


[/B]

---

### Post by fullmoonguru on 2011-02-02
Help!

---

### Post by newlinux on 2011-02-02
> **fullmoonguru said:**
> Back at the same place again, after doing an update.  Thought I had this figured out.  Here's what I did:

Deleted the v4l folder

Ran:pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }a:link {  }  [B]hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Made the changes in the hdpvr.h & hdpvr-core.c files

Ran:[/B]****[B]

cd v4l-dvb[/B] **make clean** make 
Got the compiling errors, so I changed  all the =m's to =n's, & changed the video hdpvr line back to =m

Ran 

make clean
make
sudo make install
sudo reboot

I must be doing something out of order, the the hg clone file isn't right, I don't know.  I thought it was the same as what I did last time, but I'm back to nt having a /dev/videoX file

[B]


[/B]

You only need to change firedtv=n not all options. What  do

lsusb 

and
dmesg | grep hdpvr

return now?

---

### Post by fullmoonguru on 2011-02-02
Thanks so much for replying.  The MythTV wiki makes the point that only the hdpvr (assuming it's the only device you're using) needs the m & that makes compiling much quicker.

lsusb output:

```
Bus 004 Device 002: ID 0c16:000c Gyration, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 2040:4903 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

dmesg | grep hdpvr output:

```
[   33.600321] hdpvr 1-5:1.0: untested firmware version 0x15, the driver might not work
[   33.980325] Modules linked in: snd_hda_intel(+) snd_hda_codec hdpvr(+) snd_hwdep snd_pcm_oss snd_mixer_oss v4l2_common snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event arc4 snd_seq nfsd exportfs snd_timer ath9k videodev snd_seq_device nfs fbcon mac80211 lockd nfs_acl tileblit ath font bitblit auth_rpcgss v4l1_compat softcursor snd vga16fb quota_v2 quota_tree vgastate lirc_mceusb cfg80211 sunrpc soundcore joydev snd_page_alloc v4l2_compat_ioctl32 lirc_dev psmouse serio_raw led_class shpchp nvidia(P) i2c_nforce2 lp parport usbhid hid ahci forcedeth
[   33.980501]  [<ffffffffa0f75a89>] hdpvr_register_videodev+0xc9/0x110 [hdpvr]
[   33.980512]  [<ffffffffa0f73df9>] hdpvr_probe+0x6d9/0x940 [hdpvr]
[   33.980627]  [<ffffffffa0f7b000>] ? hdpvr_init+0x0/0x3f [hdpvr]
[   33.980637]  [<ffffffffa0f7b023>] hdpvr_init+0x23/0x3f [hdpvr]
[   33.980681] hdpvr 1-5:1.0: video_device registration failed
[   33.980929] hdpvr 1-5:1.0: registering videodev failed
[   33.981350] hdpvr: probe of 1-5:1.0 failed with error -12
[   33.981443] usbcore: registered new interface driver hdpvr
```

---

### Post by fullmoonguru on 2011-02-04
Bump  Still Stuck on this one.

---

### Post by jfath on 2011-02-05
Warning:  This is the WRONG way to fix this problem.  Don't ever do it.  Ever.  However, it did work for me in 10.04.

Use a hex editor to edit hdpvr.ko

search for text 4901 and replace with 4903
search for hex 0149 and replace with 0349
Save and reload.  Driver now supports ID 4903 but not 4901

---

### Post by fullmoonguru on 2011-02-06
Of course being semi-reckless & completely desperate I tried this.  Still no video0 created though, & the grep output looks the same.

I did't move & redownload v4l.  I backeup the hdpvr.ko file, made the changes with a hex editor, and did this:

make clean
make
sudo make install
sudo reboot

Just so I know; what am I risking with this operation?

---

### Post by newlinux on 2011-02-06
This post won't be helpful - just to tell you I have no ideas on why this worked before and isn't working now... Is there another machine you can hook the HD-PVR up to?

---

### Post by fullmoonguru on 2011-02-07
Well I could install MythTV on another 'buntu machine & set it up.  I assume you are asking so I can verify that the HDPVR actually works.  I'm pretty positive that I did an Ubuntu update & that's when it stopped working.  I assume there was a kernal update in there that broke it.  I'm not to clear on the kernal/header type stuff.

---

### Post by newlinux on 2011-02-07
> **fullmoonguru said:**
> Well I could install MythTV on another 'buntu machine & set it up.  I assume you are asking so I can verify that the HDPVR actually works.  I'm pretty positive that I did an Ubuntu update & that's when it stopped working.  I assume there was a kernal update in there that broke it.  I'm not to clear on the kernal/header type stuff.

No I'm not asking to verify if the HD-PVR works, It is to see if something has gone so wrong with your current install that it doesn't work with it but works easily with another install - which might indicate you path of least resistance is a reinstall.

I personally rarely ever update a working machine regularly. Usually only a couple of times a year I will go and update all my machines. Kernel updates often require lots of handholding if you've self compiled modules.

---

### Post by fullmoonguru on 2011-02-08
In other words, if it works on another install the PVR is fine & the install is hosed somehow.  I've certainly thought of reinstalling, but it's also a server so it's not that simple.  I might have to though, & next time I'll do a backup with Remastersys.

I can certainly see the logic in holding off on updates.  I guess I'm assuming there are important security updates in those updates.

---

### Post by newlinux on 2011-02-08
> **fullmoonguru said:**
> In other words, if it works on another install the PVR is fine & the install is hosed somehow.  I've certainly thought of reinstalling, but it's also a server so it's not that simple.  I might have to though, & next time I'll do a backup with Remastersys.

I can certainly see the logic in holding off on updates.  I guess I'm assuming there are important security updates in those updates.

I understand the issues with reinstalling and upgrading the machines that have other functions (many of mine do).  I don't clone any images, but I do do daily backups (on and offsite)  of all important configuration files, code, and other things across all my machines - which have come in handy when doing reinstalls or new installations. I also document what's installed on all my servers, what's custom, etc. It has greatly cut down on the time it takes my to get everything going again after a reinstall (although I usually only do reinstalls once every couple of years). I've got 9 machines that I maintain at home - so the effort to put together the backups and documentation is well worth it (although I need to update my documentation a bit :).

You can pick and choose which updates you install, if you feel something is critical (you'll have to install any dependencies as well - which should be automatic).

---

### Post by LarryJ2 on 2011-02-12
My old 4901 HDPVR failed.  I returned it to Hauppauge under warranty.  They sent back a newer  4903 unit. With the new unit, no /dev/Videox same as the subject of this thread.

So I need to compile v4l-dvb.
     OK,  so I did the 
sudo apt-get install build-essential mercurial linux-headers-`uname -r`
and
sudo apt-get install mercurial
and
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

Made the changes to hdpvr.h
lj@mythtv:~/v4l-dvb/v4l$ cat hdpvr.h | grep PRODUCT
#define HD_PVR_PRODUCT_ID	0x4900
#define HD_PVR_PRODUCT_ID1	0x4901
#define HD_PVR_PRODUCT_ID2	0x4902
#define HD_PVR_PRODUCT_ID3	0x4982
#define HD_PVR_PRODUCT_ID4	0x4903

and to hdpvr-core.c

/* table of devices that work with this driver */
static struct usb_device_id hdpvr_table[] = {
	{ USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID) },
	{ USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID1) },
	{ USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID2) },
	{ USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID3) },
	{ USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID4) },
	{ }					/* Terminating entry */
};

But after
make clean
make

I get compilation errors while attempting to compile firedtv-1394.o   before the hdpvr module is compiled as shown in the compiler output below:

 CC [M]  /home/lj/v4l-dvb/v4l/firedtv-1394.o
/home/lj/v4l-dvb/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/lj/v4l-dvb/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or dir


Has anyone else recently compiled the v4l-dvb modules?

I don't think I need the firedtv-1394 module.  Is there anyway to not compile that part of the code?   Maybe only complile the hdpvr.o  by itself?

If anyone has a working 4903  hdpvr.ko working for the 2.6.32-28-generic-pae  kernel,  I'd would be grateful for a  copy.

Thanks,
Larry

---

### Post by LarryJ2 on 2011-02-12
Possible answer to avoiding the compilation error a which occurred after module firedtv was attempted: (See previous post)

In your  v4l-dvb directory,   
gedit     v4l/.config

Find the line associated with compiling FIREDTV
change the m (make?)  to  n (NO!)  like below:


CONFIG_DVB_FIREDTV=n

Lots of scrolling will occur and then 411 modules later you should find that 

/v4l-dvb/v4l/hdpvr.ko 

was created.

Then after you do "sudo make install"

you should see a fresh recent time stamped  hdpvr.ko
located in
/lib/modules/2.6.32-29-generic-pae/kernel/drivers/media/video/hdpvr

To check the time stamp, 

ls -al /lib/modules/2.6.32-29-generic-pae/kernel/drivers/media/video/hdpvr/hdpvr.ko

Remember your kernel (mine was 2.6.32.29...) may be different.  To find your current kernel  enter uname -r in a terminal.  For my current kernel is 2.6.32.30 which replaces the 2.6.32-29 instances above.  To find your current kernel, use  uname -r as shown below.

lj@mythtv:~/v4l-dvb/v4l$ uname -r
2.6.32-30-generic-pae

  Everytime the kernel changes until a developer modifies the source for hdpvr.h  and hdpvr-core.c,  you'll have to go through this drill.  Still I greatly prefer the option to correct the driver source code and recompile rather than begging  M$  to please fix the problem.

Another double check on your compilation.   If you do a modinfo hdpvr, you should see the current version in the line vermagic   and  your problem child 4903 HDPVR unit as in the line "alias"  as shown in these two lines  snipped from my  modinfo hdpvr output. 
Line 1:
alias:          usb:v2040p4903d*dc*dsc*dp*ic*isc*ip*
and  Line 2:
vermagic:       2.6.32-30-generic-pae SMP mod_unload modversions 586TSC 

If these are missing or show a different kernel, something went wrong.


HTH  Larry
Note:  Thanks to all contributors to the forum from whose posts I extracted the above fix.

---

### Post by newlinux on 2011-02-12
Yes, that issue and the fix was posted earlier in this thread. Glad you got it working.

---

### Post by fullmoonguru on 2011-02-15
I tried mine one more time before reinstalling Ubuntu & it worked.  I beleive the only thing different was that I changed the m to n on just the firedtv line.  The mythtv wiki had something saying you could change all of the m's to n's, except the hdpvr line, and save time.  I think that was wrong & it looks like it's not on the wiki anymore.

I do see (on boot I think) something about the v4l I got from running:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) 

It says the v4l is backported & no good enough quality for production.  Is this a problem? (mine seems to be OK)

---

### Post by DrBloodmoney on 2011-02-15
I'm just going to share my notes to myself from when I was doing this in case anyone wants it in one place:

```

# Got help here: http://ubuntuforums.org/showthread.php?t=1590146
# and here: http://www.mythtv.org/wiki/Hauppauge_HD-PVR

# check the driver installed
locate cx88-dvb.ko |grep `uname -r`

dmesg | grep hdpvr


# lacking 4903 - need to recompile the driver
modinfo hdpvr
scott@desktop:~$ modinfo hdpvr
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/media/video/hdpvr/hdpvr.ko
description:    Hauppauge HD PVR driver
author:         Janne Grunau
license:        GPL
srcversion:     F9BCAADA7960A2E15A08EBA
alias:          usb:v2040p4982d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4900d*dc*dsc*dp*ic*isc*ip*
depends:        videodev,v4l2-common
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           video_nr:video device number (-1=Auto) (array of int)
parm:           hdpvr_debug:enable debugging output (int)
parm:           default_video_input:default video input: 0=Component / 1=S-Video / 2=Composite (uint)
parm:           default_audio_input:default audio input: 0=RCA back / 1=RCA front / 2=S/PDIF (uint)
parm:           boost_audio:boost the audio signal (bool)


#
# The Fix
#
sudo apt-get install build-essential mercurial linux-headers-`uname -r`
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb/linux/drivers/media/video/hdpvr/
# gvim hdpvr.h
# added ID_4
/* Define these values to match your devices */
#define HD_PVR_VENDOR_ID        0x2040
#define HD_PVR_PRODUCT_ID       0x4900
#define HD_PVR_PRODUCT_ID1      0x4901
#define HD_PVR_PRODUCT_ID2      0x4902
#define HD_PVR_PRODUCT_ID3      0x4982
#define HD_PVR_PRODUCT_ID4      0x4903        # <--- here

# gvim hdpvr-core.c
# added ID_4 here too
/* table of devices that work with this driver */
static struct usb_device_id hdpvr_table[] = {
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID1) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID2) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID3) },
        { USB_DEVICE(HD_PVR_VENDOR_ID, HD_PVR_PRODUCT_ID4) },  # <---- here
        { }                         /* Terminating entry */
};

# cd back to root v4l-dvb folder
make
sudo make install
reboot


# Some errors in make (apparently a ubuntu packaging issue)
# need to disable firedtv compilation
# Just edit v4l/.config and find CONFIG_DVB_FIREDTV=m and change to =n
# then make again

```

---

### Post by newlinux on 2011-02-16
> **fullmoonguru said:**
> I tried mine one more time before reinstalling Ubuntu & it worked.  I beleive the only thing different was that I changed the m to n on just the firedtv line.  The mythtv wiki had something saying you could change all of the m's to n's, except the hdpvr line, and save time.  I think that was wrong & it looks like it's not on the wiki anymore.

I do see (on boot I think) something about the v4l I got from running:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) 

It says the v4l is backported & no good enough quality for production.  Is this a problem? (mine seems to be OK)

I doubt that's a problem - it's working well for me too.

My guess is by commenting out more things from being compiled some things were left out of the compilation that were actually needed.

Glad it's working.

---

### Post by jfath on 2011-02-28
>Just so I know; what am I risking with this operation?

Hex editing the driver rather than re-compiling everything is the 'wrong way' to do it because in general, you don't want to muck around with compiled binaries - especially drivers that run at privileged levels.  Also, you'll lose the fix the next time you update the kernel.

That being said, I just applied the fix again after upgrading the kernel on my main MythTV box.  'rmmod hdpvr', 'modprobe hdpvr', restart mythtv-backend and my 4903 hdpvr is again working fine.

---

### Post by Nausser on 2011-03-05
Unfortunately for me, these did not work.

I've tried "make clean, make and sudo make install" all with no luck. The entire time my HDPVR was working, lirc was not working either. I don't know for sure if they are related.
I've also tried "sudo rmmod hdpvr and sudo modprobe hdpvr" and then restarting still with no video'x' showing up. I actually linked my mythbackend to /dev/v4l/by-path/...... instead of to /dev/video'x'. It worked perfectly and I didn't need to worry about the system loading different numbers for /dev/video during reboots or power failures. I have to listing in my /dev/v4l/by-path/ anymore either.

My hdpvr still shows up fine when I run lsusb. I can't quite figure this one out.

If anyone needs more info that I've left out, please let me know.

**UPDATE**:
I've found that when doing "make clean, make and make install" it was sticking to the old kernel. I have to do a "sudo make distclean" to get it to stop compiling for the old kernel before the update.
I then rebooted, just to make sure and then did make and make install. I then did the modprobe hdpvr and then rebooted. All is well!

---

