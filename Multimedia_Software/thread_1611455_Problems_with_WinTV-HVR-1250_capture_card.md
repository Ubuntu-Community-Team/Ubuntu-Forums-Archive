---
title: "Problems with WinTV-HVR-1250 capture card"
date: 2010-11-01
forum: Multimedia Software
---

### Post by PrvSAT on 2010-11-01
Hello friends [IMG]http://www.mythtvtalk.com/images/smilies/smile.png[/IMG]

I have bought a WinTV-HVR-1250 based on some reviews that this card is  easy to setup in ubuntu but I have a bad experience so far. I would  appreciate any input.

So here it goes:

 - I run Ubuntu 10.04 with 2.6.32-25 kernel
 - the card is very well inserted and secured in a PCI-e slot
 - when: sudo lshw -C multimedia
I get:
  ```
*-multimedia
       description: Multimedia video controller
       product: Hauppauge Inc. HDPVR-1250 model 1196
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0
       resources: irq:16 memory:fea00000-febfffff
```

 - and when: sudo lspci
I get:
```
03:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)
```

So the card seems to be present...


Based on many readings, what I did:
     ```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install build-essential 
apt-get install mercurial

sudo apt-get install dvb-apps
( I found that the "dvb-utils dvbstream" was replaced with the above in Lucid)

sudo apt-get install mercurial
sudo apt-get install mythtv 
```
 
After running : /usr/bin/mythtv-setup
I tried to set the card under all types listed there (analog, mpeg, etc) and it could not find my card. What did I missed here?

Then from further readings I ran:
lspci and after the long list, my card come up with:
     ```
[   19.093519] Linux video capture interface: v2.00
[   19.100454]   alloc irq_desc for 27 on node -1
[   19.100457]   alloc kstat_irqs on node -1
[   19.100464] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[   19.100469] [drm] set up 127M of stolen space
[   19.101961] cx23885 driver version 0.0.2 loaded
[   19.101993] cx23885 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.101997] cx23885[0]: Your board isn't known (yet) to the driver.
[   19.101997] cx23885[0]: Try to pick one of the existing card configs via
[   19.101998] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   19.101999] cx23885[0]: version might help as well.
[   19.102001] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   19.102003] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   19.102004] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   19.102006] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   19.102007] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   19.102009] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
..... after more cards...
[   19.102038] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[   19.102039] cx23885[0]:    card=25 -> Compro VideoMate E800
[   19.102068] CORE cx23885[0]: subsystem: 0070:2259, board: UNKNOWN/GENERIC [card=0,autodetected]
[   19.129637] lp0: using parport0 (interrupt-driven).
[   19.152792] ppdev: user-space parallel port driver
[   19.202781] usb 6-2: reset full speed USB device using uhci_hcd and address 2
[   19.228686] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   19.228694] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfea00000
[   19.228700] cx23885 0000:03:00.0: setting latency timer to 64
[   19.228704] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs 
```
 Only in the above I could see that "Your board isn't known (yet) to the driver"
And further says: "Try to pick one of the existing card configs via cx23885[0]: card=<n> insmod option"
At this point I have no clue what to do or how to do it.

Thank you for reading this and please help me out.

---

### Post by PrvSAT on 2010-11-03
I got a link where the procedure worked fine for one guy.
[http://www.gossamer-threads.com/lists/mythtv/users/452987](http://www.gossamer-threads.com/lists/mythtv/users/452987)
I have followed this info but unfortunately the card is still not recognized in MythTV. Any input is appreciated.

In a nutshell, this is what I did:
 
 These commands were used before but I did again to make sure I did not forget anything:
```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install build-essential 
sudo apt-get install dvb-apps dvbstream
sudo apt-get install mercurial
sudo apt-get install mythtv
```

 Then based on the link provided:
```
cd /home
mkdir /var/tmp/v4l_source
cd /var/tmp/v4l_source
hg clone http://linuxtv.org/hg/v4l-dv
```... it took about 5 minutes
Then I edited the file ../v4l/.config and change the line for
the firedtv driver from "firedtv=m" to "firedtv=n"
then:
```
cd v4l-dvb
sudo make  -j3
then
make install
```Created the file in /etc/modprobe.d called "hvr1250.conf" and put in it
the following content:
options cx23885 card=20

This might be a problem but do not know:
```
insmod /lib/modules/2.6.32-25-generic/kernel/drivers/media/video/cx23885/cx23885.ko card=20
response:
insmod: error inserting '/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/cx23885/cx23885.ko': -1 File exists
```When: lsmod | grep cx23885
```
cx23885               117158  1 
ir_core                14478  6 ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx23885
cx2341x                12372  1 cx23885
v4l2_common            17381  2 cx23885,cx2341x
videodev               42362  2 cx23885,v4l2_common
videobuf_dma_sg         8898  1 cx23885
videobuf_dvb            5096  1 cx23885
dvb_core               86138  2 cx23885,videobuf_dvb
videobuf_core          16975  3 cx23885,videobuf_dma_sg,videobuf_dvb
btcx_risc               3624  1 cx23885
tveeprom               11038  1 cx23885
```When: sudo modprobe cx23885 there is just the prompt, no other info
Reboot
***Now I have a different info when "dmesg | less" and it shows the "card=20"***
```
[    6.238934] Linux video capture interface: v2.00
[    6.238937] WARNING: You're using an experimental version of the V4L stack. A s the driver
[    6.238938]          is backported to an older kernel, it doesn't offer enough quality for
[    6.238939]          its usage in production.
[    6.238939]          Use it with care.
...
...

[    7.382363] cx23885 driver version 0.0.2 loaded
[    7.382399] cx23885 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.382435] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1255 [card=20,insmod option]
...
...

[    7.528799] tveeprom 5-0050: Hauppauge model 22111, rev E2F5, serial# 7297933
[    7.528802] tveeprom 5-0050: MAC address is 00:0d:fe:6f:5b:8d
[    7.528804] tveeprom 5-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[    7.528806] tveeprom 5-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[    7.528808] tveeprom 5-0050: audio processor is CX23888 (idx 40)
[    7.528810] tveeprom 5-0050: decoder processor is CX23888 (idx 34)
[    7.528812] tveeprom 5-0050: has no radio, has IR receiver, has no IR transmitter
[    7.528814] cx23885[0]: hauppauge eeprom: model=22111
[    7.528816] cx23885_dvb_register() allocating 1 frontend(s)
[    7.528821] cx23885[0]: cx23885 based dvb card
[    7.575844] IR NEC protocol handler initialized
[    7.599777] hda_codec: ALC887: BIOS auto-probing.
```When running: /usr/bin/mythtv-setup, MythTV can not find any card under any card type,
but I understand that for Hauppage cards it should be under MPEG-2 encoder card.
Under Probed info it shows: "Fail to open" and of course the "Video device" is empty.
What else should I do, or what did I do or forget to do?

I understand that this type of card is somewhat popular and it should not be difficult to set it up in ubuntu. Is nobody around running these family of cards?
Any input will be valuable.

---

### Post by lytithwyn on 2010-11-03
I don't know anything about mythtv, but it sounds like you may not have a video device under /dev, or the permissions may be too restrictive.

Try running:
```
ls -l /dev/video*
```

and see what that gives you.

---

### Post by elgordodude on 2010-11-03
Having the exact same problem with an hvr-1250 in 10.04.  The device  seems to be recognized fine, I'm getting the same messages as PrvSAT,but MythTv can not find it.

ls -l /dev/video*

returns:

ls: can not acees /dev/video*: No such file or directory

It looks like I need to use insmod to manually designate card=3, but this is getting way over my head

---

### Post by lytithwyn on 2010-11-04
If you don't have any /dev/video devices, then I would assume the driver isn't detecting your card properly.  I have just been browsing online looking for stuff regarding this card, and several people seem to be saying that newer revisions of the card required them to download the latest v4l/dvb and compile by hand.

You might check out post #6 from this thread.  It's older, but it might get you on the right track:
[http://ubuntuforums.org/showthread.php?t=1014551]("http://ubuntuforums.org/showthread.php?t=1014551")

---

### Post by PrvSAT on 2010-11-04
I have followed the info found at this link:
[http://www.gossamer-threads.com/lists/mythtv/users/452987](http://www.gossamer-threads.com/lists/mythtv/users/452987)
and now I can watch TV, but still plenty to learn about settings.
This card must be set as "card=20", MythTV finds it under DVB card as some Samsung card but it works fine. 

For instance, when choosing the capture card in backend setup:
/usr/bin/mythtv-setup
**This card must be set as DVB card, nothing else**. Unfortunately I was mislead from an official info found in ubuntu wiki where it says that you have to select it as mpeg2 card, which is not true:
[https://help.ubuntu.com/community/MythTV/Install/Server/Backend/run-mythtv-setup](https://help.ubuntu.com/community/MythTV/Install/Server/Backend/run-mythtv-setup)

---

### Post by lytithwyn on 2010-11-04
Great to hear you got it working!  I believe if you sign up for a launchpad account you can actually edit the community wiki and correct the error.  That way, you may save someone else a headache.

Try clicking the link that says "Login to Edit" near the upper-right corner of the page.  If you don't have an account, you have the option of creating a new one there.

---

