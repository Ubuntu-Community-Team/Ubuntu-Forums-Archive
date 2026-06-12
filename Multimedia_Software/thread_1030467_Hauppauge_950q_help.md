---
title: "Hauppauge 950q help"
date: 2009-01-04
forum: Multimedia Software
---

### Post by nkatch on 2009-01-04
if anyone can help me out, im new to ubuntu and i cant seem to get my tuner to work... ive read that it is compatible with linux... i am using ubuntu studio 8.04 and when i "dmesg" i get the following:

 [   43.568675] tveeprom 0-0050: Hauppauge model 72001, rev B3F0, serial# 5081438
[   43.568680] tveeprom 0-0050: MAC address is 00-0D-FE-4D-89-5E
[   43.568683] tveeprom 0-0050: tuner model is unknown (idx 150, type 0)
[   43.568686] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   43.568689] tveeprom 0-0050: audio processor is unknown (idx 44)
[   43.568691] tveeprom 0-0050: decoder processor is unknown (idx 42)
[   43.568694] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   43.568696] hauppauge_eeprom: hauppauge eeprom: model=72001
[   43.610725] xc5000: Successfully identified at address 0x61
[   43.610728] xc5000: Firmware has not been loaded previously
[   43.612961] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   43.648405] xc5000: firmware read 12332 bytes.
[   43.648407] xc5000: firmware upload
[   49.482744] DVB: registering new adapter (au0828)
[   49.482748] DVB: registering frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   49.483614] Registered device AU0828 [Hauppauge HVR950Q]
[   49.552227] usbcore: registered new interface driver snd-usb-audio
[   49.552230] usbcore: registered new interface driver au0828
[   49.964642] loop: module loaded
[   50.004967] lp: driver loaded but no devices found
[   50.055170] ndiswrapper version 1.52 loaded (smp=yes, preempt=rt)
[   50.094061] usbcore: registered new interface driver ndiswrapper
[   50.128595] Adding 9068652k swap on /dev/sda5.  Priority:-1 extents:1 across:9068652k
[   50.680490] EXT3 FS on sda1, internal journal
[   51.821006] ip_tables: (C) 2000-2006 Netfilter Core Team
[   52.176727] No dock devices found.
[   55.066398] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   55.066402] apm: disabled - APM is not SMP safe.
[   55.362860] ppdev: user-space parallel port driver
[   55.509367] audit(1231089309.623:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5884 profile="/usr/sbin/cupsd" namespace="default"
[   55.689420] usbcore: deregistering interface driver ndiswrapper
[   55.697333] ndiswrapper version 1.52 loaded (smp=yes, preempt=rt)
[   55.707646] usbcore: registered new interface driver ndiswrapper
[   55.895929] NET: Registered protocol family 10
[   55.896210] lo: Disabled Privacy Extensions
[   56.864212] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   58.469555] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   58.469562] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   58.471569] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   59.638685] Bluetooth: Core ver 2.11
[   59.639247] NET: Registered protocol family 31
[   59.639250] Bluetooth: HCI device and connection manager initialized
[   59.639255] Bluetooth: HCI socket layer initialized
[   59.759170] Bluetooth: L2CAP ver 2.9
[   59.759176] Bluetooth: L2CAP socket layer initialized
[   59.792840] Bluetooth: RFCOMM socket layer initialized
[   59.792852] Bluetooth: RFCOMM TTY layer initialized
[   59.792854] Bluetooth: RFCOMM ver 1.8
[   60.698954] NET: Registered protocol family 17
[   73.375682] eth0: no IPv6 routers present
[   84.594114] mythfilldatabas[6997]: segfault at 00000000 eip 0815a58b esp b48f108c error 6


if anyone can help i would be very greatful... thank you

---

### Post by jcoffi on 2009-04-27
BUMP

I have the same exact problem. The video works fine in TVtime however, still no sound though.

---

### Post by markackerman8@gmail.com on 2010-03-13
Anyone having any succes with the 950Q!!!!!

---

### Post by wkulecz on 2010-03-16
Very limited success.  I can setup a gstreamer pipeline to open it and record Composite or S-Video in 9.10, but none of the tools in the repos will scan the channels.  It is very sensitive to video levels.  I've not got far enough along with it to worry about if the audio works.

The device works great in Windows 7, although the driver install seems flakey and picky about particular USB ports -- only one of my three front panel accessable ports will work.

In both Linux and Windows the Composite and S-Video inputs are very sensitive to video levels -- could only really use it after hooking up my old Sima "Video Color Corrector" box to capture tapes or the output of my DirectTV set top box.

The HDTV recording quality in Windows 7 is very good.  Maybe some day it'll work in Linux.

According to linuxtv.org you need kernel 2.6.26 or newer, so you are in for a rough ride with 8.04.

--wally.

---

### Post by markackerman8@gmail.com on 2010-03-22
I have got it working with TVtime with some special driver, and current v4l installation, in OpenSuse, and "out of the box" in Ubuntu 9.10!!!!

I haven't installed MythTV (the reason I came back to Ubuntu), where I had limited success in OpenSuse (aggravating troubles). 

The sound issue is partly solved; run it with this command:

# tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

but there is an annoying delay. If anyone can suggest a different fix, please tell me.??????

---

