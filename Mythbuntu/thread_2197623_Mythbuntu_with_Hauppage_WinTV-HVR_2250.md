---
title: "Mythbuntu with Hauppage WinTV-HVR 2250"
date: 2014-01-04
forum: Mythbuntu
---

### Post by raj-cherchattil on 2014-01-04
I am using Mythbuntu (Ubuntu 12.04.3 LTS) with Hauppauge WinTV-HVR-2250. I am unable to configure the capture card setup for card type DVB DTV capture card (v3.x)

DVB device was identified in the backend setup tool. However, Frontend ID information was not retrieved by the tool. Subtype field showed "Unknown Error"


Please help with the situation.

Please see below that I was able to load the drivers and firmware successfully:

dmesg | grep saa7164
[    7.278093] saa7164 driver loaded
[    7.279106] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,insmod option]
[    7.279112] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb800000
[    7.438276] saa7164_downloadfirmware() no first image
[    7.438322] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    7.546269] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    7.546273] saa7164_downloadfirmware() firmware loaded.
[    7.546293] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    7.546300] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    7.546301] saa7164_downloadfirmware() BSLSize = 0x0
[    7.546301] saa7164_downloadfirmware() Reserved = 0x0
[    7.546302] saa7164_downloadfirmware() Version = 0x1661c00
[   14.400677] saa7164_downloadimage() Image downloaded, booting...
[   14.504666] saa7164_downloadimage() Image booted successfully.
[   17.231697] saa7164_downloadimage() Image downloaded, booting...
[   19.103049] saa7164_downloadimage() Image booted successfully.
[   19.151787] saa7164[0]: Hauppauge eeprom: model=88061
[   19.918205] DVB: registering new adapter (saa7164)
[   19.918211] saa7164 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   22.841034] DVB: registering new adapter (saa7164)
[   22.841040] saa7164 0000:03:00.0: DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   22.841296] saa7164[0]: registered device video0 [mpeg]
[   23.071862] saa7164[0]: registered device video1 [mpeg]
[   23.283348] saa7164[0]: registered device vbi0 [vbi]
[   23.283384] saa7164[0]: registered device vbi1 [vbi]

---

### Post by anoldguy on 2014-11-18
[QUOTE=raj-cherchattil;12891475]I am using Mythbuntu (Ubuntu 12.04.3 LTS) with Hauppauge WinTV-HVR-2250. I am unable to configure the capture card setup for card type DVB DTV capture card (v3.x)

DVB device was identified in the backend setup tool. However, Frontend ID information was not retrieved by the tool. Subtype field showed "Unknown Error"


Please help with the situation.

Please see below that I was able to load the drivers and firmware successfully:

-----

In the MythTV version 0.27 release notes, it explains that the 
DVB DTV capture card (v3.x) 
card type name is changed to 
DVB-T/S/C, ATSC or ISDB-T tuner card.  

Even though I was using the MythTV Backend Setup program that shut down the Backend, I had to force it down by opening a terminal window and typing:  
sudo stop mythtv-backend 
before the Backend Setup program would recognize the Hauppage HVR 2250 as 
DVB-T/S/C, ATSC or ISDB-T tuner card.

---

### Post by dannyboy79 on 2014-11-19
if having issues, i suggest using the mythtv-setup function to completely remove all tuners from all backends and then re-add them.

---

