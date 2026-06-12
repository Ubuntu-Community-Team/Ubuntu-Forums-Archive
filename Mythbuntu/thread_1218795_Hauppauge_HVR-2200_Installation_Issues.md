---
title: "Hauppauge HVR-2200 Installation Issues"
date: 2009-07-21
forum: Mythbuntu
---

### Post by nasha on 2009-07-21
Hi Guys,
Just purchased a HVR2200 and installed following this guide:
[HTML]http://ubuntuforums.org/showthread.php?p=7331198[/HTML]
Everything seemed fine until it got to scanning in channels in mythtv-setup.
I get no channels when i attempt to scan, the signal bar or lock doesnt even move the entire scan.
This prompted me to check dmesg, which is where i've found errors (see below). Seems the tda firmware isn't loading for some reason? And i assume that this is causing the errors with the saa drivers?

Any help would be greatly appreciated :)
```

nasha@MythTV:~$ dmesg|grep saa
[    4.639381] saa7164 driver loaded
[    4.639419] saa7164 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.639690] CORE saa7164[0]: dev->lmmio  = 0xf8d80000
[    4.639691] CORE saa7164[0]: dev->lmmio2 = 0xf7e00000
[    4.639693] CORE saa7164[0]: dev->bmmio  = 0xf8d80000
[    4.639694] CORE saa7164[0]: dev->bmmio2 = 0xf7e00000
[    4.639695] CORE saa7164[0]: subsystem: 0070:8980, board: Hauppauge WinTV-HVR2200 [card=4,autodetected]
[    4.639701] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe800000
[    4.639706] saa7164 0000:03:00.0: setting latency timer to 64
[    4.800505] saa7164_downloadfirmware() no first image
[    4.800514] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[    4.800517] saa7164 0000:03:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[    6.232078] saa7164_downloadfirmware() firmware read 3978608 bytes.
[    6.232082] saa7164_downloadfirmware() firmware loaded.
[    6.232090] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[    6.232095] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    6.232097] saa7164_downloadfirmware() BSLSize = 0x0
[    6.232098] saa7164_downloadfirmware() Reserved = 0x0
[    6.232099] saa7164_downloadfirmware() Version = 0x51cc1
[   13.088013] saa7164_downloadimage() Image downloaded, booting...
[   13.192016] saa7164_downloadimage() Image booted successfully.
[   15.316011] saa7164_downloadimage() Image downloaded, booting...
[   16.980015] saa7164_downloadimage() Image booted successfully.
[   16.980969] saa7164[0]: i2c bus 0 registered
[   16.981001] saa7164[0]: i2c bus 1 registered
[   16.981031] saa7164[0]: i2c bus 2 registered
[   17.016186] saa7164[0]: Hauppauge eeprom: model=89619
[   17.372821] DVB: registering new adapter (saa7164)
[   17.656657] DVB: registering new adapter (saa7164)
[   32.256010] saa7164_api_i2c_write() error, ret(2) = 0x32
[   33.256006] saa7164_api_i2c_write() error, ret(1) = 0x32
[   34.253876] saa7164_api_i2c_write() error, ret(1) = 0x32
.....output omitted
[  120.276033] saa7164_api_i2c_read() error, ret(1) = 0x32
[  121.296019] saa7164_api_i2c_read() error, ret(1) = 0x32
[  122.308031] saa7164_api_i2c_read() error, ret(1) = 0x32
[  123.324032] saa7164_api_i2c_read() error, ret(1) = 0x32
.....output omitted
[  287.792033] saa7164_cmd_send() No free sequences
[  287.792036] saa7164_api_i2c_write() error, ret(1) = 0xc
[  287.792043] saa7164_cmd_send() No free sequences
[  287.792046] saa7164_api_i2c_write() error, ret(1) = 0xc
```

```
nasha@MythTV:~/$ dmesg|grep tda
[  102.260039] tda10048_writeregbulk(): writereg error err -5
[  103.260027] tda10048_writeregbulk(): writereg error err -5
....
[  120.276037] tda10048_readreg: readreg error (ret == -5)
[  121.296023] tda10048_readreg: readreg error (ret == -5)
[  122.308036] tda10048_readreg: readreg error (ret == -5)
....
[  144.660047] tda10048_firmware_upload: firmware upload failed
[  145.660042] tda10048_writereg: writereg error (ret == -5)
[  146.660036] tda10048_writereg: writereg error (ret == -5)
....
[  206.780032] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[  206.780036] i2c-adapter i2c-2: firmware: requesting dvb-fe-tda10048-1.0.fw
[  206.784636] tda10048_firmware_upload: firmware read 24878 bytes.
[  206.784641] tda10048_firmware_upload: firmware uploading
[  207.784028] tda10048_readreg: readreg error (ret == -5)
[  208.784029] tda10048_writereg: writereg error (ret == -5)
....
[  213.784027] tda10048_readreg: readreg error (ret == -5)
[  214.784027] tda10048_writereg: writereg error (ret == -5)
[  215.793598] tda10048_writereg: writereg error (ret == -5)
[  216.792031] tda10048_writeregbulk(): writereg error err -5
[  217.792030] tda10048_writeregbulk(): writereg error err -5
[  218.792036] tda10048_writeregbulk(): writereg error err -5

```

---

### Post by Caysho on 2009-07-21
Check that /lib/firmware/dvb-fe-tda10048-1.0.fw exists.

---

### Post by nasha on 2009-07-21
Already done, it exists

---

### Post by Caysho on 2009-07-21
A google search on 
```
tda10048_writereg: writereg error
```
found [some advice about removing LIRC]("http://www.isely.net/pipermail/pvrusb2/2009-March/002234.html")
Part of the post is about the channel scanning error.

---

### Post by nasha on 2009-07-21
Google search doesnt return alot of helpful links, but i will try removing lirc and see if that has any effect.
Thanks for the suggestion :)

---

### Post by nasha on 2009-07-21
Removing lirc followed by a cold boot produces the same problem

---

### Post by Caysho on 2009-07-22
Maybe contact Steve Toth at kernellabs.com ?
If it is a problem with the driver then he will be interested.

---

### Post by nasha on 2009-07-23
I dont think its a driver issue... Infact i have no idea what the issue is...

Things only get stranger....
I thought i'd attempt a complete OS reinstall, much to my disgrace.
However this seemed to fix the problems, card was detected fine, scanned in my channels, great!
Then i decided to continue setting up other features of the machine nfs samba torrents etc. and left it at that last night. I come home today to find that im experiencing the same errors... Ive attempted a cold reboot, to no avail.
Is it possible some of the software i installed is effecting the driver in someway? From memory i installed Vuze (azureus), java and nautilus, nothing more.

---

### Post by Caysho on 2009-07-24
> **nasha said:**
> 
Is it possible some of the software i installed is effecting the driver in someway? From memory i installed Vuze (azureus), java and nautilus, nothing more.

Odd ... throwing out ideas here to see what sticks ...

At what point are you doing the driver build/install ?
I have seen two kernel updates for jaunty since it was released, and the module compilation is specific to the kernel at the time of the compile.  I decided to deal with the source from a fresh state, so I completely removed the previous kernel sources and pulled the stoth source fresh, compiled/installed.

Maybe you have the modules installed in the correct location but compiled against the wrong kernel ?

Attach the entire dmesg.

Time to take notes to ease the troubleshooting ;)

---

