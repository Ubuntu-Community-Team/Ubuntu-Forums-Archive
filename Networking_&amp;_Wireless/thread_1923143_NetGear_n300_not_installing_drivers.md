---
title: "NetGear n300 not installing drivers"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by fishstick41 on 2012-02-10
I am using "Wireless network drivers" to install the drivers for my N300. When i try to install  the driver it gives me a black screen and it doesn't return me to the desktop I have the restart the computer. How do i fix this problem If you need anything from me please ask.

---

### Post by fishstick41 on 2012-02-10
Is there anyway to fix this?

---

### Post by chili555 on 2012-02-10
Isn't a Netgear N300 a router? I doubt you need any software at all to set it up. What is the software or driver you are trying to install?

---

### Post by fishstick41 on 2012-02-10
The USB adapter said "Wireless N-300 USB adapter WNA3100" I tried to install the drives with out the USB I guess it did but as soon as I plugged in the USB it when to a black screen with a bunch of code.

---

### Post by chili555 on 2012-02-10
Did you try to install the Windows drivers from the CD? Linux is not Windows, thank heavens!

With the device inserted, run and post: ```
lsusb
uname -r
```Thanks.

We may or may not need the attached. Please wait until I tell you to use them.

---

### Post by fishstick41 on 2012-02-10
martin@martin-OptiPlex-745:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 007 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]


martin@martin-OptiPlex-745:~$ uname -r
3.0.0-15-generic

---

### Post by chili555 on 2012-02-10
You do, indeed need the drivers I attached. Download them to your desktop. Right click and select *Extract Here*. Now open a terminal and do:```
sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf
sudo ndiswrapper -a 0846:9020 bcmwlhigh5
sudo modprobe ndiswrapper
```Now let's check:```
ndiswrapper -l
iwconfig
```Is it working now? If not, please post:```
dmesg | grep ndis
```

---

### Post by fishstick41 on 2012-02-10
martin@martin-OptiPlex-745:~$ sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf
driver bcmwlhigh5 is already installed

martin@martin-OptiPlex-745:~$ sudo ndiswrapper -a 0846:9020 bcmwlhigh5
Driver 'bcmwlhigh5' is already used for '0846:9020'

martin@martin-OptiPlex-745:~$ sudo modprobe ndiswrapper

martin@martin-OptiPlex-745:~$ ndiswrapper -l
bcmwlhigh5 : invalid driver!

martin@martin-OptiPlex-745:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

martin@martin-OptiPlex-745:~$ dmesg | grep ndis
[  301.849557] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  301.874637] usbcore: registered new interface driver ndiswrapper
[  425.175212] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'

---

### Post by chili555 on 2012-02-10
It sounds like you already tried this and installed the Windows 7 or Vista .inf file. ndiswrapper requires the XP driver.> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install Windows **XP**  drivers  and kernel module to load the Windows **XP** drivers. Both are called ndiswrapper.Let's do as suggested; check the logs:```
sudo cat /var/log/syslog | grep -i ndis | tail -n20
```

---

### Post by fishstick41 on 2012-02-10
martin@martin-OptiPlex-745:~$ sudo cat /var/log/syslog | grep -i ndis | tail -n20

[sudo] password for martin: 

Feb 10 11:32:50 martin-OptiPlex-745 kernel: [ 2011.176271] usbcore: deregistering interface driver ndiswrapper
Feb 10 11:32:50 martin-OptiPlex-745 kernel: [ 2011.187159] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Feb 10 11:32:50 martin-OptiPlex-745 loadndisdriver: loadndisdriver: load_driver(337): coudln't find valid drivers files for driver bcmwlhigh5
Feb 10 11:32:50 martin-OptiPlex-745 adndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5
Feb 10 11:32:50 martin-OptiPlex-745 loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5
Feb 10 11:32:50 martin-OptiPlex-745 kernel: [ 2011.439207] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
Feb 10 11:32:50 martin-OptiPlex-745 kernel: [ 2011.439251] usbcore: registered new interface driver ndiswrapper
Feb 10 11:56:17 martin-OptiPlex-745 kernel: [ 3418.779801] usbcore: deregistering interface driver ndiswrapper
Feb 10 11:56:17 martin-OptiPlex-745 kernel: [ 3418.790618] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Feb 10 11:56:18 martin-OptiPlex-745 kernel: [ 3419.048359] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
Feb 10 11:56:18 martin-OptiPlex-745 kernel: [ 3419.050453] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
Feb 10 11:56:19 martin-OptiPlex-745 kernel: [ 3419.052709] IP: [<ffffffffa02f2e39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
Feb 10 11:56:19 martin-OptiPlex-745 kernel: [ 3419.052775] Modules linked in: ndiswrapper(+) nls_utf8 isofs snd_hrtimer bnep rfcomm bluetooth snd_hda_codec_analog snd_hda_intel snd_hda_codec snd_hwdep binfmt_misc snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq joydev snd_timer snd_seq_device snd nouveau soundcore snd_page_alloc ttm ppdev drm_kms_helper dcdbas psmouse drm serio_raw i2c_algo_bit mxm_wmi wmi video parport_pc lp parport usbhid hid tg3 [last unloaded: ndiswrapper]
Feb 10 11:56:19 martin-OptiPlex-745 kernel: [ 3419.052928] RIP: 0010:[<ffffffffa02f2e39>]  [<ffffffffa02f2e39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
Feb 10 12:02:04 martin-OptiPlex-745 kernel: [  301.849557] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Feb 10 12:02:04 martin-OptiPlex-745 kernel: [  301.874637] usbcore: registered new interface driver ndiswrapper
Feb 10 12:04:07 martin-OptiPlex-745 loadndisdriver: loadndisdriver: load_driver(337): coudln't find valid drivers files for driver bcmwlhigh5
Feb 10 12:04:07 martin-OptiPlex-745 adndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5
Feb 10 12:04:07 martin-OptiPlex-745 loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5
Feb 10 12:04:07 martin-OptiPlex-745 kernel: [  425.175212] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'

---

### Post by chili555 on 2012-02-10
> ndiswrapper: driver bcmn43x[COLOR="Red"]x64[/COLOR] (,08/26/2009, 5.10.79.30) loaded Is yours a 64-bit system?```
arch
```Please try this:```
sudo ndiswrapper -e bcmwlhigh5.inf
sudo rm -rf /etc/ndiswrapper/*
cd Desktop/wna3100-drivers
mkdir 32bit
cp bcmwlhigh5.inf 32bit
cp bcmwlhigh5.sys 32bit
cp bcmh43xx.cat 32bit
sudo ndiswrapper -i 32bit/bcmwlhigh5.inf
sudo ndiswrapper -a 0846:9020 bcmwlhigh5
sudo modprobe ndiswrapper
```

Now let's check:
```


ndiswrapper -l
iwconfig


```

---

### Post by fishstick41 on 2012-02-10
By the way i'm sorry i didn't tell you i am running ubuntu 11.10

---

### Post by fishstick41 on 2012-02-10
I installed ubuntu 11.10  64BIT

---

### Post by chili555 on 2012-02-10
Is that what is confirmed here?```
arch
```If it says x86_64, then we will take another approach.

---

### Post by fishstick41 on 2012-02-10
x86_64
 is what it said.

---

### Post by chili555 on 2012-02-10
Please download the attached to your desktop. Right-click it and select *Extract Here*. Next, do:```
sudo ndiswrapper -e bcmwlhigh5.inf
sudo rm -rf /etc/ndiswrapper/*
sudo ndiswrapper -i Desktop/ndis_bcmwl/bcmwlhigh5.inf
sudo ndiswrapper -a 0846:9020 bcmwlhigh5
sudo modprobe ndiswrapper
```Now let's check:
```
ndiswrapper -l
iwconfig
```Any improvement?

---

### Post by fishstick41 on 2012-02-10
It is saying the driver is installed, I believe. but when i install the drivers on windows i have to push the bottom on the usb to turn it on. but when i push the bottom now it doesn't turn on.

---

### Post by chili555 on 2012-02-10
Let's see:```
iwconfig
ndiswrapper -l
dmesg | grep wlan
```

---

### Post by fishstick41 on 2012-02-10
martin@martin-OptiPlex-745:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

martin@martin-OptiPlex-745:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present

martin@martin-OptiPlex-745:~$ dmesg | grep wlan
martin@martin-OptiPlex-745:~$ 
 
Nothing came up when i put in "dmesg | grep wlan"

---

### Post by chili555 on 2012-02-10
How about:```
dmesg | grep ndis
```

---------
Reference: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

---

### Post by fishstick41 on 2012-02-10
still nothing 

martin@martin-OptiPlex-745:~$ dmesg | grep ndis
martin@martin-OptiPlex-745:~$ dmesg | grep ndis
martin@martin-OptiPlex-745:~$

---

### Post by chili555 on 2012-02-10
Wow! Let's go back to basics. With the device inserted, please do:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```Also, while the device is inserted, do:```
sudo tail -f /var/log/syslog
```Press the button on the device and see what messages appear. Leave syslog with Ctrl+c.

---

### Post by chili555 on 2012-02-10
Please see attached. Do you have to use WPS to connect in Windows?

---

### Post by fishstick41 on 2012-02-10
martin@martin-OptiPlex-745:~$ sudo modprobe ndiswrapper
[sudo] password for martin: 

martin@martin-OptiPlex-745:~$ ndiswrapper -l

bcmwlhigh5 : driver installed
    device (0846:9020) present

martin@martin-OptiPlex-745:~$ 

martin@martin-OptiPlex-745:~$ dmesg | grep ndis

[13782.596164] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[13783.001529] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[13783.003611] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[13783.005722] IP: [<ffffffffa0d1de39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[13783.005766] Modules linked in: ndiswrapper(+) snd_seq_dummy nls_utf8 udf crc_itu_t bnep rfcomm bluetooth vesafb binfmt_misc nvidia(P) joydev snd_hda_codec_analog snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd serio_raw dcdbas ppdev parport_pc soundcore snd_page_alloc lp parport usbhid hid tg3
[13783.005815] RIP: 0010:[<ffffffffa0d1de39>]  [<ffffffffa0d1de39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[13783.005914]  [<ffffffffa0d06c7a>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[13783.005936]  [<ffffffffa0d1de50>] ? USBD_InterfaceIsDeviceHighSpeed+0x20/0x20 [ndiswrapper]
[13783.005959]  [<ffffffffa0d1de80>] ? USBD_InterfaceReference+0x30/0x30 [ndiswrapper]
[13783.005981]  [<ffffffffa0d1ddf0>] ? USBD_GetUSBDIVersion+0x20/0x20 [ndiswrapper]
[13783.006008]  [<ffffffffa0d1deb0>] ? USBD_InterfaceDereference+0x30/0x30 [ndiswrapper]
[13783.006025]  [<ffffffffa0d1dee0>] ? USBD_InterfaceQueryBusTime+0x30/0x30 [ndiswrapper]
[13783.006041]  [<ffffffffa0d1df10>] ? USBD_InterfaceSubmitIsoOutUrb+0x30/0x30 [ndiswrapper]
[13783.006057]  [<ffffffffa0d1de30>] ? USBD_InterfaceGetUSBDIVersion+0x40/0x40 [ndiswrapper]
[13783.006072]  [<ffffffffa0d0bef0>] ? ExAllocatePoolWithTag.part.9+0x30/0x40 [ndiswrapper]
[13783.006087]  [<ffffffffa0d0dbfa>] ? ExAllocatePoolWithTag+0x1a/0x60 [ndiswrapper]
[13783.006103]  [<ffffffffa0d1e07b>] ? win2lin3+0x11/0x14 [ndiswrapper]
[13783.006125]  [<ffffffffa0d19e02>] ? mp_init+0x72/0x210 [ndiswrapper]
[13783.006141]  [<ffffffffa0d13eca>] ? pdoDispatchPnp+0x5a/0x190 [ndiswrapper]
[13783.006156]  [<ffffffffa0d11bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[13783.006172]  [<ffffffffa0d1afbb>] ? ndis_start_device+0x2b/0x870 [ndiswrapper]
[13783.006192]  [<ffffffffa0d11bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[13783.006207]  [<ffffffffa0d11f26>] ? IoSyncForwardIrp+0x96/0xe0 [ndiswrapper]
[13783.006224]  [<ffffffffa0d1c073>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
[13783.006241]  [<ffffffffa0d1e067>] ? win2lin2+0xe/0x11 [ndiswrapper]
[13783.006256]  [<ffffffffa0d11bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[13783.006271]  [<ffffffffa0d11bdc>] ? IofCallDriver+0x6c/0xc0 [ndiswrapper]
[13783.006289]  [<ffffffffa0d11bb0>] ? IofCallDriver+0x40/0xc0 [ndiswrapper]
[13783.006304]  [<ffffffffa0d138d7>] ? IoSendIrpTopDev+0xd7/0x120 [ndiswrapper]
[13783.006323]  [<ffffffffa0d141dc>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[13783.006339]  [<ffffffffa0d14531>] ? wrap_pnp_start_device+0xd1/0x180 [ndiswrapper]
[13783.006355]  [<ffffffffa0d147bf>] ? wrap_pnp_start_usb_device+0xef/0x120 [ndiswrapper]
[13783.006420]  [<ffffffffa0d0639b>] ? loader_init+0xcb/0x160 [ndiswrapper]
[13783.006430]  [<ffffffffa0cdc07b>] ? wrapper_init+0x7b/0x1000 [ndiswrapper]
[13783.006478] RIP  [<ffffffffa0d1de39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
martin@martin-OptiPlex-745:~$ sudo tail -f /var/log/syslog
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006420]  [<ffffffffa0d0639b>] ? loader_init+0xcb/0x160 [ndiswrapper]
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006430]  [<ffffffffa0cdc07b>] ? wrapper_init+0x7b/0x1000 [ndiswrapper]
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006434]  [<ffffffff81002042>] ? do_one_initcall+0x42/0x180
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006438]  [<ffffffff8109fede>] ? sys_init_module+0xbe/0x230
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006442]  [<ffffffff815fa1c2>] ? system_call_fastpath+0x16/0x1b
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006444] Code: 00 00 83 79 1c 03 b9 10 01 00 00 0f 45 c1 89 46 04 c7 02 01 00 00 00 5d c3 66 0f 1f 84 00 00 00 00 00 55 48 89 e5 66 66 66 66 90 
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006478] RIP  [<ffffffffa0d1de39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006495]  RSP <ffff880036c5d760>
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006497] CR2: 00000000ffffffd0
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006500] ---[ end trace 5dfac297c086e5ab ]---

^Cmartin@martin-OptiPlex-745:~$ clear

martin@martin-OptiPlex-745:~$ sudo tail -f /var/log/syslog
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006420]  [<ffffffffa0d0639b>] ? loader_init+0xcb/0x160 [ndiswrapper]
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006430]  [<ffffffffa0cdc07b>] ? wrapper_init+0x7b/0x1000 [ndiswrapper]
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006434]  [<ffffffff81002042>] ? do_one_initcall+0x42/0x180
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006438]  [<ffffffff8109fede>] ? sys_init_module+0xbe/0x230
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006442]  [<ffffffff815fa1c2>] ? system_call_fastpath+0x16/0x1b
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006444] Code: 00 00 83 79 1c 03 b9 10 01 00 00 0f 45 c1 89 46 04 c7 02 01 00 00 00 5d c3 66 0f 1f 84 00 00 00 00 00 55 48 89 e5 66 66 66 66 90 
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006478] RIP  [<ffffffffa0d1de39>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006495]  RSP <ffff880036c5d760>
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006497] CR2: 00000000ffffffd0
Feb 10 17:49:17 martin-OptiPlex-745 kernel: [13783.006500] ---[ end trace 5dfac297c086e5ab ]---



This is what happen (Thanks for helping me by the way )

---

### Post by fishstick41 on 2012-02-10
Yes, I use WPS when i use it on windows.

---

### Post by fishstick41 on 2012-02-10
I also tried the usb in a different port this is what showed up


martin@martin-OptiPlex-745:~$ sudo tail -f /var/log/syslog

[sudo] password for martin:
 
Feb 10 17:55:24 martin-OptiPlex-745 kernel: [14150.635558] Info fld=0x0
Feb 10 17:55:24 martin-OptiPlex-745 kernel: [14150.635560] sr 1:0:0:0: [sr0]  Add. Sense: Medium not present - tray closed
Feb 10 17:55:24 martin-OptiPlex-745 kernel: [14150.635565] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 62 1c 00 00 02 00
Feb 10 17:55:24 martin-OptiPlex-745 kernel: [14150.635575] end_request: I/O error, dev sr0, sector 100464
Feb 10 17:55:24 martin-OptiPlex-745 kernel: [14150.635578] Buffer I/O error on device sr0, logical block 25116
Feb 10 17:55:24 martin-OptiPlex-745 kernel: [14150.635581] Buffer I/O error on device sr0, logical block 25117
Feb 10 17:55:51 martin-OptiPlex-745 kernel: [14177.470679] usb 1-4: USB disconnect, device number 2
Feb 10 17:56:18 martin-OptiPlex-745 udevd[986]: timeout 'mtp-probe /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3 1 3'
Feb 10 17:56:19 martin-OptiPlex-745 udevd[986]: timeout: killing 'mtp-probe /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3 1 3' [13493]
Feb 10 17:56:50  udevd[986]: last message repeated 31 times
^Cmartin@martin-OptiPlex-745:~$

---

### Post by fishstick41 on 2012-02-10
I will be gone for the weekend I will be back by Sunday late afternoon.

---

### Post by chili555 on 2012-02-12
Wow! That is an unhappy syslog! Let's try a different file.

Please download the attached to your desktop. Right-click it and select *Extract Here*. Next, do:
```
sudo ndiswrapper -e bcmwlhigh5.inf
sudo rm -rf /etc/ndiswrapper/*
sudo ndiswrapper -i Desktop/Broadcom-bcm43xx_USB_32-64bit_v2/bcmn43xx64.inf
sudo ndiswrapper -a 0846:9020 bcmn43xx64
sudo modprobe ndiswrapper
```
Now let's check:
```
ndiswrapper -l
iwconfig
```
Any improvement?

EDIT: Now attached.

---

### Post by fishstick41 on 2012-02-13
Hey i'm just going to give up because i see this is going in circles. i'm sorry for the late respond and I truly thank you for your time helping me.

---

