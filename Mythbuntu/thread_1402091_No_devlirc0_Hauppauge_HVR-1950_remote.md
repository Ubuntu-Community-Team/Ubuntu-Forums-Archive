---
title: "No /dev/lirc0 Hauppauge HVR-1950 remote"
date: 2010-02-08
forum: Mythbuntu
---

### Post by hineas on 2010-02-08
I have the Hauppauge WinTV HVR-1950 (a USB tuner) on my MythTV machine.  I am able to record TV without any errors.  I love it!  However, for the life of me, I cannot figure out how to get the remote working.  I have tried using the "Mythbuntu Control Centre" and "sudo dpkg-reconfigure lirc" by choosing every Hauppauge remote listed without any luck.  I have spent weeks trying to figure this out, but every single thread I have read assumes that lirc sees the device. "ls /dev" only reveals /dev/lircd, but there is no /dev/lirc0 present.  

After restarting lirc successfully, there was still no /dev/lirc0.  

```
$ sudo service lirc restart
 * Stopping remote control daemon(s): LIRC                    [ OK ]
 * Loading LIRC modules                                                   [ OK ]
 * Starting remote control daemon(s) : LIRC                     [ OK ]
``````

$ ls /dev | grep lirc*
lircd

```The reason I am stumped is because every walkthrough I have found assumes that /dev/lirc0 is present.  I cannot even find my IR receiver on the computer.

I also don't find my card listed in /proc/bus/input/devices (I can see my wireless USB keyboard and mouse, and my power button).

I am running mythbuntu 9.10

```

$ dmesg | grep lirc
[   17.338176] lirc_dev: IR Remote Control driver registered, major 61
[672348.300518] lirc_dev: IR Remote Control driver registered, major 61
``````
dmesg | grep pvrusb2
[    8.241807] usbcore: registered new interface driver pvrusb2
[    8.241814] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[    8.241818] pvrusb2: Debug mask is 31 (0x1f)
[    9.277282] cx25840 0-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[    9.278156] pvrusb2: Attached sub-driver cx25840
[    9.950313] tuner 0-0042: chip found @ 0x84 (pvrusb2_a)
[    9.950326] pvrusb2: Attached sub-driver tuner
[   12.643071] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[   12.643077] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[   12.643081] pvrusb2: Setting up 6 unique standard(s)
[   12.643085] pvrusb2: Set up standard idx=0 name=PAL-M
[   12.643087] pvrusb2: Set up standard idx=1 name=PAL-N
[   12.643090] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   12.643093] pvrusb2: Set up standard idx=3 name=NTSC-M
[   12.643096] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   12.643098] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   12.643102] pvrusb2: Initial video standard (determined by device type): NTSC-M
[   12.643116] pvrusb2: Device initialization completed successfully.
[   12.643206] pvrusb2: registered device video0 [mpeg]
[   12.643211] DVB: registering new adapter (pvrusb2-dvb)
[153430.960129] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[153430.960134] pvrusb2: Encoder command: 0x81
[153430.960137] pvrusb2: Giving up on command.  This is normally recovered by the driver.
[324430.567911] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[324430.567917] pvrusb2: Encoder command: 0x81
[324430.567919] pvrusb2: Giving up on command.  This is normally recovered by the driver.
[333431.501224] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[333431.501230] pvrusb2: Encoder command: 0x81
[333431.501232] pvrusb2: Giving up on command.  This is normally recovered by the driver.
[346031.271778] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[346031.271784] pvrusb2: Encoder command: 0x81
[346031.271786] pvrusb2: Giving up on command.  This is normally recovered by the driver.
[524533.815353] pvrusb2: ***WARNING*** device's encoder appears to be stuck (status=0x00000003)
[524533.815358] pvrusb2: Encoder command: 0x81
[524533.815361] pvrusb2: Giving up on command.  This is normally recovered by the driver.

```I wasn't too worried about the above warnings since the card is working well to capture TV.  I don't think those errors are related to the IR receiver.

```

 $ modprobe -l lirc*
kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko
updates/dkms/lirc_ite8709.ko
updates/dkms/lirc_sir.ko
updates/dkms/lirc_streamzap.ko
updates/dkms/lirc_ttusbir.ko
updates/dkms/lirc_ene0100.ko
updates/dkms/lirc_mceusb.ko
updates/dkms/lirc_dev.ko
updates/dkms/lirc_it87.ko
updates/dkms/lirc_atiusb.ko
updates/dkms/lirc_i2c.ko
updates/dkms/lirc_sasem.ko
updates/dkms/lirc_bt829.ko
updates/dkms/lirc_igorplugusb.ko
updates/dkms/lirc_serial.ko
``````

$ dmesg | grep tveeprom
[   12.643038] tveeprom 0-00a2: Hauppauge model 75111, rev D1F5, serial# 6226799
[   12.643044] tveeprom 0-00a2: MAC address is 00-0D-FE-5F-03-6F
[   12.643049] tveeprom 0-00a2: tuner model is NXP 18271C2 (idx 155, type 54)
[   12.643053] tveeprom 0-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   12.643057] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[   12.643060] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[   12.643063] tveeprom 0-00a2: has radio, has IR receiver, has IR transmitter

```Any help would be greatly appreciated!   I am at a complete loss as what to do so I can get a /dev/lirc0 being displayed!  Luckily my wireless keyboard has a good range so I have a "remote" until I get this one working!

---

### Post by rimshot4 on 2010-02-14
I've been having the same issue. From what I've read elsewhere, I don't believe the IR receiver on the HVR-1950 works on Ubuntu. Fortunately IR receivers are relatively cheap on Amaszon.com, and I'm fairly sure that you can get the Hauppage remote to work with another IR receiver. Let me know if you know otherwise, about the IR reciever not working, that is.

-Jesse

---

### Post by pros456 on 2010-02-14
Something changed in 9.10, in 9.04 it works out of the box.

---

### Post by tedrock on 2010-02-16
anyone found any more information about this? why it stopped working? how you can get it to work?

---

### Post by hineas on 2010-02-20
I've still had no luck.  I've almost decided on building my own serial port IR receiver.

[http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html)

Looking on the internet, the components are pretty cheap.

---

### Post by tedrock on 2010-02-20
how about the blaster? have you gotten that to work?

---

### Post by nickrout on 2010-02-20
what kernel module did it use on 9.04? (Maybe boot a mythbuntu 9.04 livecd to check).

Is the same module present on 9.10?

---

### Post by hineas on 2010-02-21
I have not tried the blaster--I have no need in my current setup.  Sorry

---

### Post by hineas on 2010-03-05
My solution to my problem was MythPyWii.  I am now using my Wii controller as a remote.  It was an easy setup, it took only 10-15 minutes to get it working.  It's great!  Someday I would like to get my IR remote working, but this works well so I am happy...

---

### Post by SL666 on 2010-07-16
my remote has worked since 8.04 and has stopped after the last reboot (/dev/lirc0 doesn't exist anymore?) now running 10.04

---

