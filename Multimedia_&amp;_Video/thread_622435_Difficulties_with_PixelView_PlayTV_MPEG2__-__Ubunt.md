---
title: "Difficulties with PixelView PlayTV MPEG2  -  Ubuntu 7.10"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by elciocs on 2007-11-24
I'm just startin with Linux. I've tried to install PixelView PlayTV MPEG2 card. 
I'm running Ubuntu 7.10. My computer has dual boot so this card is fine in Windows Xp Professional Edition.
I would like to delete Windows XP as soon I put this card running fine in Ubuntu. 
I've followed step by step the recomendations in [http://mstr.ueuo.com/](http://mstr.ueuo.com/) however It did not work for me.
Everything seems to be OK but NO INPUT SIGNAL message appears in the TvTime screen.
I'm attaching the log after every command that I've entered.
Can you help me?
Thanks in advance.

Elcio

 ================== PCI card ====================================
[COLOR="Navy"]My card is PixelView PlayTV MPEG2 [/COLOR]

**lspci**

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)02:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)02:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)   

================= Trying to run TVTime =============================
**tvtime -d /dev/video1A **

correr tvtime 1.0.2.A ler a configuração de /etc/tvtime/tvtime.xmlA ler a configuração de /root/.tvtime/tvtime.xmlvideoinput: Driver won't tell us its norm: Argumento inválidovideoinput: Can't get tuner info: Argumento inválidovideoinput: Driver won't tell us its norm: Argumento inválidovideoinput: Can't get tuner info: Argumento inválidovideoinput: Can't mute card. Post a bug report with yourvideoinput: driver info to [http://tvtime.net/videoinput:](http://tvtime.net/videoinput:) Include this error: 'Argumento inválido' 

================ Checking if BTTV has loaded  in boot =====================
 **grep bttv**

[ 58.085007] bttv: driver version 0.9.17 loaded[ 58.085012] bttv: using 8 buffers with 2080k (520 pages) each for capture[ 58.085077] bttv: Bt8xx card found (0).[ 58.085315] bttv0: Bt878 (rev 17) at 0000:02:07.0, irq: 19, latency: 32, mmio: 0xfe9ff000[ 58.085326] bttv0: detected: Prolink Pixelview PV-BT [card=72], PCI subsystem ID is 1554:4011[ 58.085330] bttv0: using: Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [card=72,insmod option][ 58.085360] bttv0: gpio: en=00000000, out=00000000 in=006fc0ff [init][ 58.641597] bttv0: i2c scan: found device @ 0xa0 [eeprom][ 58.651591] bttv0: i2c scan: found device @ 0xc2 [tuner (analog)][ 58.652178] bttv0: i2c scan: found device @ 0xc6 [???][ 58.665315] bttv0: using tuner=5[ 58.665320] bttv0: i2c: checking for TDA7432 @ 0x8a... not found[ 58.728655] bttv0: i2c: checking for TDA9887 @ 0x86... not found[ 58.751943] bttv0: registered device video0[ 58.751973] bttv0: registered device vbi0[ 58.751999] bttv0: registered device radio0[ 58.752019] bttv0: PLL: 28636363 =35468950 .. ok[ 58.787665] input: bttv IR (card=72) as /class/input/input4 grep tuner[ 58.651591] bttv0: i2c scan: found device @ 0xc2 [tuner (analog)][ 58.665315] bttv0: using tuner=5[ 58.750466] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])[ 58.750491] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))[ 58.750495] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) 

================= Starting TvTime ===============================
 **tvtime -d /dev/video0 **

A correr tvtime 1.0.2.A ler a configuração de /etc/tvtime/tvtime.xmlA ler a configuração de /root/.tvtime/tvtime.xmlObrigado por usar o tvtime.

---

