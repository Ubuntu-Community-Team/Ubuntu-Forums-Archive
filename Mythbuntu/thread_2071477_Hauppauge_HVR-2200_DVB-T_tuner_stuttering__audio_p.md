---
title: "Hauppauge HVR-2200 DVB-T tuner stuttering / audio problem"
date: 2012-10-15
forum: Mythbuntu
---

### Post by jugglingcats on 2012-10-15
Hi, I've had this card in a MythTV system since 2010 and after some careful setup it was working great for ages. I then updated to 0.25 and it started giving issues... playback on live TV would fail with "Frame buffering failed too many times". WAF at an all time low, mention of friends with the latest "smart" TVs, etc, etc. You get the picture.

Anyway, I decided it was time for a clean install and went with 12.04.1 - complete re-install. Everything went very smoothly.

Live TV is still giving an issue though, albeit a different one!

What happens is that after a minute or two of watching, the picture starts showing artefacts - a few at first then progressively getting worse until totally unwatchable. The sound also starts progressively getting worse. After enduring this for a minute or two it will fix itself, for a few more minutes then same issue.

The same problem happens in MythTV and with mplayer dvb://xyz. The problem appears on recorded programs too, not surprisingly. I tried increasing the ringbuffer in the backend to no avail.

It doesn't appear to be an aerial/tuning issue as stopping playback (either in Myth or mplayer) and starting again gives a few more minutes of perfect playback.

Lots of decode errors appear in the myth front end log and mplayer console output.

The dmesg output on boot is below. I downloaded the firmware without building it and didn't have to install any kernel modules.

I've scoured the forums and can't find anyone else with this exact problem.

I'm running mobo ASUS AT3IONT-I (Atom based with nvidia ION graphics). The only other thing to mention is that the original issues might have coincided with shifting to an SSD for the system disk, but can't think why this would affect this issue.

Any help on further diagnosis gratefully received - am running out of ideas!

Thanks, Alfie.

```
[    3.599438] saa7164 driver loaded
[    3.600888] saa7164 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 18 (level, low) -> IRQ 18
[    3.603784] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,insmod option]
[    3.603805] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xf9c00000
[    3.603824] saa7164 0000:02:00.0: setting latency timer to 64
[    3.760213] saa7164_downloadfirmware() no first image
[    3.760238] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    4.391881] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    4.391891] saa7164_downloadfirmware() firmware loaded.
[    4.391924] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    4.391936] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    4.391943] saa7164_downloadfirmware() BSLSize = 0x0
[    4.391949] saa7164_downloadfirmware() Reserved = 0x0
[    4.391955] saa7164_downloadfirmware() Version = 0x1661c00
[   11.248045] saa7164_downloadimage() Image downloaded, booting...
[   11.352050] saa7164_downloadimage() Image booted successfully.
[   13.400043] saa7164_downloadimage() Image downloaded, booting...
[   15.064051] saa7164_downloadimage() Image booted successfully.
[   15.108537] saa7164[0]: Hauppauge eeprom: model=89619
[   15.430711] DVB: registering new adapter (saa7164)
[   18.463575] DVB: registering new adapter (saa7164)
[   18.465299] saa7164[0]: registered device video0 [mpeg]
[   18.695371] saa7164[0]: registered device video1 [mpeg]
[   18.906035] saa7164[0]: registered device vbi0 [vbi]
[   18.906221] saa7164[0]: registered device vbi1 [vbi]

```

---

### Post by gambitgeoff on 2012-11-06
I had the exact same problem.  For me the solution was to reinstall *all* of the firmwares for the tuner card.

Initially I had only installed the firmware NXP7164-2010-03-10.1.fw.

If you follow the below and copy all of the .fw's you might have more luck.  I'm using Mythbuntu 12.04.

wget [http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip](http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip)
wget [http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
wget [http://www.steventoth.net/linux/hvr22xx/extract.sh](http://www.steventoth.net/linux/hvr22xx/extract.sh)

sh extract.sh
cp *fw /lib/firmware

You should end up getting more log info in your /var/log/syslog, including:

tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
tda10048_firmware_upload: firmware read 24878 bytes.
tda10048_firmware_upload: firmware uploading
tda18271: RF tracking filter calibration complete

Good luck,

---

### Post by nickrout on 2012-11-07
> **gambitgeoff said:**
> I had the exact same problem.  For me the solution was to reinstall *all* of the firmwares for the tuner card.

Initially I had only installed the firmware NXP7164-2010-03-10.1.fw.

If you follow the below and copy all of the .fw's you might have more luck.  I'm using Mythbuntu 12.04.

wget [http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip](http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip)
wget [http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
wget [http://www.steventoth.net/linux/hvr22xx/extract.sh](http://www.steventoth.net/linux/hvr22xx/extract.sh)

sh extract.sh
cp *fw /lib/firmware

You should end up getting more log info in your /var/log/syslog, including:

tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
tda10048_firmware_upload: firmware read 24878 bytes.
tda10048_firmware_upload: firmware uploading
tda18271: RF tracking filter calibration complete

Good luck,

Don't go outside your packaging system if you can avoid it. Install  	linux-firmware-nonfree (why the hell mythbuntu doesn't install this by default is a too PC thing!)

---

