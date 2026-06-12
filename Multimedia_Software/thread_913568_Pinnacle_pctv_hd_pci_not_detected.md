---
title: "Pinnacle pctv hd pci not detected"
date: 2008-09-07
forum: Multimedia Software
---

### Post by Yeahmeat on 2008-09-07
Hello Everyone!

I've spent the past few days trying to get this card to work with Hardy, and I've got nothing but headaches.  I've followed instructions from the myth wiki on how to get this card working with Ubuntu, but still no luck.  I'm (mostly) positive I extracted and installed the firmware and drivers properly as outlined here:[http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)]("http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)")

I've followed the instructions to a "t" and still can not get Ubuntu to recognize this device.  I'll include my lspci and dmesg outputs for reference.  Hoping someone is able to help me solve this problem.

lspci:
> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:05.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:05.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:06.0 Communication controller: Conexant Unknown device 2f40
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

relevant dmesg output:
> [   29.782486] cx88[0]/0: Can't get MMIO memory @ 0x0, subsystem: 11bd:0051
[   29.782496] cx8800: probe of 0000:01:05.0 failed with error -22
[   29.809344] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   29.809406] cx88[0]/2: Can't get MMIO memory @ 0x0, subsystem: 11bd:0051
[   29.809416] cx88-mpeg driver manager: probe of 0000:01:05.2 failed with error -22


I hope the dmesg output provided is enough to help pinpoint the problem.  

Thanks in advance for any suggestions.

---

### Post by cariboo on 2008-09-07
Give this a try:

```
modprobe symbol:lgdt330x_attach
modprobe cx88-dvb 
```

it may solve your problem.

Jim

---

### Post by Yeahmeat on 2008-09-08
The first modprobe seemed to work successfully, though the modprobe cx88-dvb returned this:
> FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27-2-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device


---

### Post by jmore9 on 2008-09-14
Maybe if you look at what i did to get it working on my blog :

[http://hdtvonpc.blogspot.com/](http://hdtvonpc.blogspot.com/)

It might help you.  I had to run the dvb-v4l setup again after restarting but only the make not the sudo make install.  It then worked just fine.

Also if you search the ubuntu forums with the following you will get a lot info.

Your milage may vary.  I am still using winxp only because the ATI hs tuner card does not work in linux nor does my pinnacle 800i work as good in linux  as it does in windows.

This is my what i use to view and record my programs so until i get it working as good as windows i will still only need winxp for that.

---

