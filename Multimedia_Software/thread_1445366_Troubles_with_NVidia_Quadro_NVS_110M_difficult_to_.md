---
title: "Troubles with NVidia Quadro NVS 110M difficult to identify"
date: 2010-04-02
forum: Multimedia Software
---

### Post by Le Farfadet Spatial on 2010-04-02
Hello everybody out there!

   Well, I come here every two or three years, when I have some troubles with my graphic card. Indeed, once again...

   Since last Tuesday, I experience some system freeze. Since yesterday, I must run on low graphic mode. As there has not been any X.org or driver update, I suspect that my graphic card is running down. But I do not know how to diagnose this.

   My configuration:

      -- Dell Latitude D820 laptop;

      -- processor Intel Core 2 Duo T7200 (2.0GHz 667MHz FSB);

      -- bi-canal 2x1024Mo DDR2-SDRAM 533MHz memory;

      -- graphic card NVIDIA Quadro NVS 110M 256MB;

      -- 15.4" WSXGGA+ (1680 x 1050) LCD screen;

      -- 100Go SATA (7200 TPM)) hard-drive;

      -- 8x DVD +/- RW burner;

      -- battery 9 cells 85 WHr LI-ION;

      -- Bluetooth card for Latitude;

      -- Intel PRO/Wireless 3945 802.11a/g;

      -- Ubuntu Linux 9.04 Jaunty Jackalope desktop 64 bits real-time kernel.

   Some commands results:

```

$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

```

```

$ dmesg | grep NVRM
[   23.376311] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   25.225275] NVRM: failed to copy vbios to system memory.
[   25.225621] NVRM: RmInitAdapter failed! (0x30:0xffffffff:896)
[   25.225873] NVRM: rm_init_adapter(0) failed
[   25.510578] NVRM: failed to copy vbios to system memory.
[   25.511463] NVRM: RmInitAdapter failed! (0x30:0xffffffff:896)
[   25.511677] NVRM: rm_init_adapter(0) failed
[   25.808332] NVRM: failed to copy vbios to system memory.
[   25.808657] NVRM: RmInitAdapter failed! (0x30:0xffffffff:896)
[   25.808695] NVRM: rm_init_adapter(0) failed
[   26.119871] NVRM: failed to copy vbios to system memory.
[   26.120746] NVRM: RmInitAdapter failed! (0x30:0xffffffff:896)
[   26.120966] NVRM: rm_init_adapter(0) failed
[   26.415824] NVRM: failed to copy vbios to system memory.
[   26.416186] NVRM: RmInitAdapter failed! (0x30:0xffffffff:896)
[   26.416229] NVRM: rm_init_adapter(0) failed
[   26.723314] NVRM: failed to copy vbios to system memory.
[   26.724154] NVRM: RmInitAdapter failed! (0x30:0xffffffff:896)
[   26.724190] NVRM: rm_init_adapter(0) failed

```

My research on the web does not have helped me at all. Therefore, if anybody has any idea how to fix it, or being sure that it is my card that is going down, I will be pleased to hear of it.

   Kind regards.

   The Spatial Sprite

---

### Post by Le Farfadet Spatial on 2010-04-03
Hello everybody out there!

Well, does anybody have an idea for a start?

Kind regards.

The Spacial Sprite

---

### Post by xc3RnbFO8P on 2010-04-03
From bug report:
[https://bugs.launchpad.net/ubuntu/+bug/284715]("https://bugs.launchpad.net/ubuntu/+bug/284715")
> Alberto Milone  wrote on 2008-10-21:  	  #20

Paul: try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

maybe you will find someone who has the same motherboard and managed to solve the problem.

I'm closing this bug report since these problems depend on the BIOS and therefore can't be fixed without a BIOS upgrade/fix.

---

### Post by Le Farfadet Spatial on 2010-04-03
Hello everybody out there!

Thank you Ringi for your answer. Anyway, it does not seem to fit my problem, as the bug report has been closed in 2008, and I did not experience my current trouble before Tuesday, does it?

Kind regards.

The Spacial Sprite

---

### Post by Le Farfadet Spatial on 2010-04-04
Hello everybody out there!

I have somehow found a way to fix my problem: I have two partition on my hard-drive, one for "/", another for "/home". I have simply re-formatted "/" and re-installed Ubuntu. Well, now it works, but I still do not know from where did my troubles come. I hope it will not happen again...

Kind regards.

The Spacial Sprite

---

