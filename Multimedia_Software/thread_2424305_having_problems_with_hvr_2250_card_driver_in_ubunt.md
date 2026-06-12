---
title: "having problems with hvr 2250 card driver in ubuntu 18.04"
date: 2019-08-06
forum: Multimedia Software
---

### Post by zikky on 2019-08-06
Hi to all ......I need help because I am new to linux so can someone  help me to get my HVR 2250 to work it scan but no channels in analog i  can get from my country maybe it's the error I am getting  here how do i make a folder for the NXP7164-2010-03-10.1.fw driver please i very little about Linux so if i can get a step by step i will follow how to do it thanks
--------------------------------------------------------------------------------------------------------------------

```
...10.912666] saa7164 driver loaded
[   10.912837] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   10.912840] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 30, latency: 0, mmio: 0xfd800000
[   11.116049] saa7164_downloadfirmware() no first image
[   11.116058] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   11.178955] saa7164 0000:03:00.0: loading /lib/firmware/5.0.0-23-generic/NXP7164-2010-03-10.1.fw failed with error -20
[   11.765183] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   11.765184] saa7164_downloadfirmware() firmware loaded.
[   11.765187] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   11.765191] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.765192] saa7164_downloadfirmware() BSLSize = 0x0
[   11.765192] saa7164_downloadfirmware() Reserved = 0x0
[   11.765193] saa7164_downloadfirmware() Version = 0x1661c00
[   18.728161] saa7164_downloadimage() Image downloaded, booting...
[   18.840055] saa7164_downloadimage() Image booted successfully.
[   21.280152] saa7164_downloadimage() Image downloaded, booting...
[   22.912151] saa7164_downloadimage() Image booted successfully.
[   22.964565] saa7164[0]: Hauppauge eeprom: model=88061
[   23.705698] dvbdev: DVB: registering new adapter (saa7164)
[   23.705706] saa7164 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   26.881824] dvbdev: DVB: registering new adapter (saa7164)
[   26.881830] saa7164 0000:03:00.0: DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   26.917946] saa7164[0]: registered device video0 [mpeg]
[   27.144673] saa7164[0]: registered device video1 [mpeg]
[   27.356544] saa7164[0]: registered device vbi0 [vbi]
[   27.356627] saa7164[0]: registered device vbi1 [vbi]
[   30.730343] saa7164 0000:03:00.0: DVB: adapter 1 frontend 0 frequency 0 out of range (54000000..858000000)
[   33.796387] saa7164 0000:03:00.0: DVB: adapter 0 frontend 0 frequency 0 out of range (54000000..858000000)
```

---

### Post by zikky on 2019-08-06
btw the HVR 2250 do work in windows on my gaming desktop running wintv sofware and it scan the analog channels i want to use it for ...I want to use the HVR 2250 in ubuntu 18.4 now .....

---

### Post by zikky on 2019-08-06
I think I post this on the wrong section ....Can a mod/Admin move my post to the Hardware section on this forum please thanks....
[h=1][/h]

---

### Post by zikky on 2019-08-06
update driver error  fixed  .......but now when i scan in tvheadend for the free 7 analog channels i get none but again if i use the WINTV software in windows it get those 7 channels ....If I have to post more info please tell me what you members need to know and I will post it so I can get my card scanning and working on tvheadend
```
[    9.709313] saa7164 driver loaded
[    9.710914] saa7164 0000:03:00.0: enabling device (0000 -> 0002)
[    9.711031] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    9.711034] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 32, latency: 0, mmio: 0xfd800000
[   10.026586] saa7164_downloadfirmware() no first image
[   10.026598] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   10.263160] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   10.263161] saa7164_downloadfirmware() firmware loaded.
[   10.263165] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   10.263169] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   10.263169] saa7164_downloadfirmware() BSLSize = 0x0
[   10.263170] saa7164_downloadfirmware() Reserved = 0x0
[   10.263171] saa7164_downloadfirmware() Version = 0x1661c00
[   17.430617] saa7164_downloadimage() Image downloaded, booting...
[   17.538710] saa7164_downloadimage() Image booted successfully.
[   19.970599] saa7164_downloadimage() Image downloaded, booting...
[   21.602690] saa7164_downloadimage() Image booted successfully.
[   21.660052] saa7164[0]: Hauppauge eeprom: model=88061
[   26.746670] dvbdev: DVB: registering new adapter (saa7164)
[   26.746676] saa7164 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   29.975997] dvbdev: DVB: registering new adapter (saa7164)
[   29.976004] saa7164 0000:03:00.0: DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   30.012837] saa7164[0]: registered device video0 [mpeg]
[   30.239145] saa7164[0]: registered device video1 [mpeg]
[   30.450331] saa7164[0]: registered device vbi0 [vbi]
[   30.450410] saa7164[0]: registered device vbi1 [vbi]
[   31.139376] saa7164 0000:03:00.0: DVB: adapter 1 frontend 0 frequency 0 out of range (54000000..858000000)
[   34.370976] saa7164 0000:03:00.0: DVB: adapter 0 frontend 0 frequency 0 out of range (54000000..858000000)
```

---

### Post by wildmanne39 on 2019-08-06
*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

---

### Post by wildmanne39 on 2019-08-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by zikky on 2019-08-06
will do and thank you....

---

### Post by zikky on 2019-08-06
Btw this desktop has dual boot i setup for win7 pro / ubuntu 18.4....

---

### Post by zikky on 2019-08-07
Can someone make a freq patch for tvheadend with the freq the local tv station used in my country thank you....ch2  83.50mhz   ch3  187.50mhz   ch4 205.50mhz   ch5 471.50mhz   ch6 495.50mhz   ch7 537.50mhz    ch8 561.50mhz     this will fix my scanning problems because the usa freq is to far of the scanning range... thanks in advance...can you make it both way eg: ch2  83.50mhz   and ch2  83.25mhz  for all seven freq thanks.

---

### Post by zikky on 2019-08-08
need help driver install for HVR 2250 but still can't get any channels in tvheadend.....

-------------------------------------------------------
 dmesg |grep saa7164
[   10.882597] saa7164 driver loaded
[   10.882764] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   10.882767] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 30, latency: 0, mmio: 0xfd800000
[   11.092704] saa7164_downloadfirmware() no first image
[   11.092713] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   11.663537] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   11.663538] saa7164_downloadfirmware() firmware loaded.
[   11.663541] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   11.663545] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   11.663545] saa7164_downloadfirmware() BSLSize = 0x0
[   11.663546] saa7164_downloadfirmware() Reserved = 0x0
[   11.663546] saa7164_downloadfirmware() Version = 0x1661c00
[   18.636713] saa7164_downloadimage() Image downloaded, booting...
[   18.744707] saa7164_downloadimage() Image booted successfully.
[   21.176755] saa7164_downloadimage() Image downloaded, booting...
[   22.800807] saa7164_downloadimage() Image booted successfully.
[   22.853657] saa7164[0]: Hauppauge eeprom: model=88061
[   25.868136] dvbdev: DVB: registering new adapter (saa7164)
[   25.868141] saa7164 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   29.162069] dvbdev: DVB: registering new adapter (saa7164)
[   29.162076] saa7164 0000:03:00.0: DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   29.197965] saa7164[0]: registered device video0 [mpeg]
[   29.424766] saa7164[0]: registered device video1 [mpeg]
[   29.637264] saa7164[0]: registered device vbi0 [vbi]
[   29.637332] saa7164[0]: registered device vbi1 [vbi]
[  746.536993] saa7164 0000:03:00.0: DVB: adapter 1 frontend 0 frequency 0 out of range (54000000..858000000)
[  749.404214] saa7164 0000:03:00.0: DVB: adapter 0 frontend 0 frequency 0 out of range (54000000..858000000)

---

### Post by sd71 on 2019-08-10
Have you tried installing drivers from [https://www.driverdetective.org.uk]("https://www.driverdetective.org.uk/")[/]("http://www.steventoth.net/linux/hvr22xx/") ? These work for me, perfectly. I would uninstall and try again.

---

