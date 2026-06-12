---
title: "Hauppauge HVR-2200 installation problems"
date: 2012-01-11
forum: Multimedia Software
---

### Post by Paulgirardin on 2012-01-11
I installed this tuner and followed the procedures here: 
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

When trying to set up the tuner in MythTV backend the card was not being recognised.I was getting this output from demsg | grep saa :

```
paul@myth:~$ dmesg | grep saa
[ 11.677646] saa7164 driver loaded
[ 11.677684] saa7164 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 11.677687] saa7164[0]: Your board isn't known (yet) to the driver.
[ 11.677688] saa7164[0]: Try to pick one of the existing card configs via
[ 11.677688] saa7164[0]: card=<n> insmod option. Updating to the latest
[ 11.677689] saa7164[0]: version might help as well.
[ 11.677691] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[ 11.677693] saa7164[0]: card=0 -> Unknown
[ 11.677694] saa7164[0]: card=1 -> Generic Rev2
[ 11.677695] saa7164[0]: card=2 -> Generic Rev3
[ 11.677697] saa7164[0]: card=3 -> Hauppauge WinTV-HVR2250
[ 11.677698] saa7164[0]: card=4 -> Hauppauge WinTV-HVR2200
[ 11.677700] saa7164[0]: card=5 -> Hauppauge WinTV-HVR2200
[ 11.677701] saa7164[0]: card=6 -> Hauppauge WinTV-HVR2200
[ 11.677702] saa7164[0]: card=7 -> Hauppauge WinTV-HVR2250
[ 11.677703] saa7164[0]: card=8 -> Hauppauge WinTV-HVR2250
[ 11.678297] CORE saa7164[0]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]
[ 11.678301] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb800000
[ 11.678308] saa7164 0000:03:00.0: setting latency timer to 64
```

I followed the next instructions:

"This necessitated the download of [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw) and copy to /lib/firmware/<current kernel> (this firmware version doesn't get generated using the instructions further up the page)."

Then dmesg | grep saa gave:

```
paul@myth:~$ dmesg | grep saa
\[ 14.200625] saa7164 driver loaded
[ 14.200660] saa7164 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 14.201242] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[ 14.201246] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb800000
[ 14.201253] saa7164 0000:03:00.0: setting latency timer to 64
[ 14.359232] saa7164_downloadfirmware() no first image
[ 14.359243] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[ 14.788012] saa7164_downloadfirmware() firmware read 4019072 bytes.
[ 14.788014] saa7164_downloadfirmware() firmware loaded.
[ 14.788022] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[ 14.788028] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[ 14.788030] saa7164_downloadfirmware() BSLSize = 0x0
[ 14.788031] saa7164_downloadfirmware() Reserved = 0x0
[ 14.788032] saa7164_downloadfirmware() Version = 0x1661c00
[ 21.635726] saa7164_downloadimage() Image downloaded, booting...
[ 21.739620] saa7164_downloadimage() Image booted successfully.
[ 23.857542] saa7164_downloadimage() Image downloaded, booting...
[ 25.519905] saa7164_downloadimage() Image booted successfully.
[ 25.564461] saa7164[0]: Hauppauge eeprom: model=89619
[ 25.925131] DVB: registering new adapter (saa7164)
[ 28.555614] DVB: registering new adapter (saa7164)
[ 28.555839] saa7164[0]: registered device video0 [mpeg]
[ 28.786961] saa7164[0]: registered device video1 [mpeg]
[ 28.997134] saa7164[0]: registered device vbi0 [vbi]
[ 28.997156] saa7164[0]: registered device vbi1 [vbi]
paul@myth:~$ \
```

The card now is in the capture cards list but it appears as an analogue card not DVB DTV 

Is this as it should be?

---

### Post by rrofes on 2012-04-16
hi paulgirarin,
I am planning to buy a Hauppauge HVR-2200 too, and set it up with mythubuntu. did you finally get it to work?

---

