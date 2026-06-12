---
title: "Linux-headers 2.6.38.7 problems with Natty"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gdiloren on 2011-03-22
I just upgraded from 10.10 to 11.04 alpha 3 and unlike my old pc on the new one I can't boot with the newest linux-header. Seems the video is bad and the login seldom appears, it boots but then the mouse pointer is unusable. When I boot into the old linux-headers (the last of 10.10) everything is fine but I have message errors about system application failures. What to do?

---

### Post by uRock on 2011-03-22
If you are going to test the developmental release, then please post in the NNT&D sub-forum.

Moved to NNT&D

Regards,
uRock

---

### Post by cariboo on 2011-03-22
We need some system specifications, specifically graphics adapter, in order to help you solve your problem. BTW it looks like your problem has nothing to do with the kerenel.

---

### Post by gdiloren on 2011-03-23
Well, I have Natty 11.04 alpha 3, I can boot into Kernel Linux 2.6.35-28 generic-pae but not into 2.6.38.7. I have 4 GB RAM but my system monitor indicates 3.2 GB. I have Processors  0 & 1 both at 2140 @ 1.60 GHz. Available disk space:249.1 on 320 GB. It's an ACER ASPIRE desktop computer E2140 AST-690. I can't find the rest of the info you want. How do you do that?

---

### Post by cariboo on 2011-03-23
Open a terminal and type:

```
lspci | grep VGA
```

The result of the above command should look something like this:

```
lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)

```

---

### Post by dino99 on 2011-03-23
> **gdiloren said:**
> Well, I have Natty 11.04 alpha 3, I can boot into Kernel Linux 2.6.35-28 generic-pae but not into 2.6.38.7. I have 4 GB RAM but my system monitor indicates 3.2 GB. I have Processors  0 & 1 both at 2140 @ 1.60 GHz. Available disk space:249.1 on 320 GB. It's an ACER ASPIRE desktop computer E2140 AST-690. I can't find the rest of the info you want. How do you do that?

install the generic-pae kernel instead of the default generic, that way your ram will be fully used. Boot on 35 kernel then remove/purge (into synaptic: right click) the 38 installed one; and now install 38 generic-pae header and 38 generic-pae image, then reboot

---

### Post by gdiloren on 2011-03-23
Sorry for delay, got it from launchpad:
Title:    i946gz  GPU lockup  ESR: 0x00000001 IPEHR: 0x87000000  Status in “xserver-xorg-video-intel” package in Ubuntu:   New  Bug description:   Binary package hint: xserver-xorg-video-intel    Upgraded from 10.10 to 11.04 and upon booting in had a lot of   "application problems" apport-gpu-error-intel.py    ProblemType: Crash   DistroRelease: Ubuntu 11.04   Package: xserver-xorg-video-intel 2:2.14.0-4ubuntu4   ProcVersionSignature: Ubuntu 2.6.35-28.49-generic-pae 2.6.35.11   Uname: Linux 2.6.35-28-generic-pae i686   NonfreeKernelModules: slamr   Architecture: i386   Chipset: i946gz   CompizPlugins: No value set for `/apps/compiz-1/general/screen0/options/active_plugins'   CompositorRunning: None   DRM.card0.VGA.1:    status: connected    enabled: enabled    dpms: On    modes: 1680x1050 1600x1200 1280x1024 1280x1024 1440x900 1440x900 1152x864 1024x768 1024x768 1024x768 832x624 800x600 800x600 800x600 800x600 640x480 640x480 640x480 640x480 720x400    edid-base64: AP///////wAEcgkAJJuAlDATAQNoLx54KscgpFVJmScTUFS/74BxT4GAlQ+VAKlAswABAQEBITmQMGIaJ0AYsDZA2SgRAAAcAAAA/wBMQVAwODA3NjQyMTYKAAAA/QA4TB5TEQAKICAgICAgAAAA/ABBY2VyIFgyMjNXCiAgAJk=   Date: Tue Mar 22 11:06:16 2011   DistUpgraded: Log time: 2011-03-22 08:45:05.580438   DistroCodename: natty   DistroVariant: ubuntu   DkmsStatus:    sl-modem, 2.9.11~20100718, 2.6.38-7-generic-pae, i686: installed     sl-modem, 2.9.11~20100718, 2.6.35-28-generic-pae, i686: installed   DuplicateSignature: (ESR: 0x00000001 IPEHR: 0x87000000)   ExecutablePath: /usr/share/apport/apport-gpu-error-intel.py   GraphicsCard:    Intel Corporation 82946GZ/GL Integrated Graphics Controller [8086:2972] (rev 02) (prog-if 00 [VGA controller])      Subsystem: Elitegroup Computer Systems Device [1019:2196]   InstallationMedia: Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)   InterpreterPath: /usr/bin/python2.7   MachineType: Acer Aspire T690   ProcCmdline: /usr/bin/python /usr/share/apport/apport-gpu-error-intel.py   ProcEnviron:       ProcKernelCmdLine: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=54da4311-9f75-4421-83b2-c90142cc330c ro quiet splash vt.handoff=7   ProcKernelCmdLine_: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=54da4311-9f75-4421-83b2-c90142cc330c ro quiet splash vt.handoff=7   RelatedPackageVersions:    xserver-xorg             1:7.6~3ubuntu11    libdrm2                  2.4.23-1ubuntu5    xserver-xorg-video-intel 2:2.14.0-4ubuntu4   Renderer: Unknown   SourcePackage: xserver-xorg-video-intel   Title: [i946gz] GPU lockup (ESR: 0x00000001 IPEHR: 0x87000000)   UpgradeStatus: Upgraded to natty on 2011-03-22 (0 days ago)   UserGroups:       dmi.bios.date: 04/16/2007   dmi.bios.vendor: Phoenix Technologies, LTD   dmi.bios.version: R01-C0   dmi.board.name: E946GZ   dmi.board.vendor: Acer   dmi.chassis.type: 3   dmi.chassis.vendor: Broadwater   dmi.chassis.version: 946GZT-AM   dmi.modalias: dmi:bvnPhoenixTechnologies,LTD:bvrR01-C0:bd04/16/2007:svnAcer:pnAspireT690:pvrR01-C0:rvnAcer:rnE946GZ:rvr:cvnBroadwater:ct3:cvr946GZT-AM:   dmi.product.name: Aspire T690   dmi.product.version: R01-C0   dmi.sys.vendor: Acer   version.compiz: compiz 1:0.9.4-0ubuntu7   version.libdrm2: libdrm2 2.4.23-1ubuntu5   version.libgl1-mesa-glx: libgl1-mesa-glx 7.10.1-0ubuntu3   version.xserver-xorg: xserver-xorg 1:7.6~3ubuntu11   version.xserver-xorg-video-ati: xserver-xorg-video-ati 1:6.14.0-0ubuntu4   version.xserver-xorg-video-intel: xserver-xorg-video-intel 2:2.14.0-4ubuntu4   version.xserver-xorg-video-nouveau: xserver-xorg-video-nouveau 1:0.0.16+git20110107+b795ca6e-0ubuntu6

---

### Post by gdiloren on 2011-03-23
> **cariboo907 said:**
> Open a terminal and type:

```
lspci | grep VGA
```The result of the above command should look something like this:

```
lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)

```

00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)

---

### Post by gdiloren on 2011-03-23
> **dino99 said:**
> install the generic-pae kernel instead of the default generic, that way your ram will be fully used. Boot on 35 kernel then remove/purge (into synaptic: right click) the 38 installed one; and now install 38 generic-pae header and 38 generic-pae image, then reboot
I can't boot into BIOS no more.

---

### Post by dino99 on 2011-03-23
> **gdiloren said:**
> I can't boot into BIOS no more.

what that means ? bios & kernel are two different things. Is your bios corrupt ? have you flashed it ? maybe check the motherboard battery (watch the MB doc)

---

