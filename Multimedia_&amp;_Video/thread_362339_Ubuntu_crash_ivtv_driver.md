---
title: "Ubuntu crash ivtv driver"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by bnuytten on 2007-02-15
Hi,

I'm installing the ivtv modules for a Hauppauge PVR-500. The hardware is detected when the driver is loaded and the /dev/video* devices are created. But when I want to test capture the entire system crashes and reboots. Just like someone would have pulled the power plug!
```
cat /dev/video0 > /tmp/test_capture.mpg
```

I followed this guide: [https://help.ubuntu.com/community/Install_IVTV_Edgy]("https://help.ubuntu.com/community/Install_IVTV_Edgy"). An identical setup with Fedora Core 5 and MythTV 0.20 worked flawlesly a few days ago. So I guess it's not the hardware.

Below is the (shortened) output of /var/log/messages when loading the ivtv module:

```
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  ==================== START INIT IVTV ====================
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  version 0.7.0 (tagged release) loading
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  In case of problems please include the debug info between
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
Feb 15 18:40:54 juno kernel: [17180580.500000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 18 (level, low) -> IRQ 201
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0060: TEA5767 detected.
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb 15 18:40:55 juno kernel: [17180580.816000] tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
Feb 15 18:40:55 juno kernel: [17180580.836000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
Feb 15 18:40:59 juno kernel: [17180585.604000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Feb 15 18:40:59 juno kernel: [17180585.724000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: Hauppauge model 23559, rev E491, serial# 9578267
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: audio processor is CX25843 (idx 37)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: has radio, has no IR remote
Feb 15 18:40:59 juno kernel: [17180585.788000] ivtv0: This is the first unit of a PVR500
Feb 15 18:41:00 juno kernel: [17180586.568000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
Feb 15 18:41:00 juno kernel: [17180586.784000] ivtv0: Encoder revision: 0x02050032
Feb 15 18:41:00 juno kernel: [17180586.784000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
Feb 15 18:41:00 juno kernel: [17180586.788000] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
Feb 15 18:41:00 juno kernel: [17180586.788000] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
Feb 15 18:41:01 juno kernel: [17180586.924000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
Feb 15 18:41:01 juno kernel: [17180586.928000] ivtv0: Create encoder radio stream
Feb 15 18:41:01 juno kernel: [17180586.928000] tuner 0-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
Feb 15 18:41:01 juno kernel: [17180587.172000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
Feb 15 18:41:01 juno kernel: [17180587.176000] ivtv:  ======================  NEXT CARD  ======================
[COLOR="Red"]<snip>[/COLOR]
Feb 15 18:41:07 juno kernel: [17180593.704000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
Feb 15 18:41:07 juno kernel: [17180593.704000] ivtv:  ====================  END INIT IVTV  ====================

```

---

### Post by superm1 on 2007-02-15
> **bnuytten said:**
> Hi,

I'm installing the ivtv modules for a Hauppauge PVR-500. The hardware is detected when the driver is loaded and the /dev/video* devices are created. But when I want to test capture the entire system crashes and reboots. Just like someone would have pulled the power plug!
```
cat /dev/video0 > /tmp/test_capture.mpg
```I followed this guide: [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy). An identical setup with Fedora Core 5 and MythTV 0.20 worked flawlesly a few days ago. So I guess it's not the hardware.

Below is the (shortened) output of /var/log/messages when loading the ivtv module:

```
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  ==================== START INIT IVTV ====================
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  version 0.7.0 (tagged release) loading
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  In case of problems please include the debug info between
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
Feb 15 18:40:54 juno kernel: [17180580.500000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
Feb 15 18:40:54 juno kernel: [17180580.500000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 18 (level, low) -> IRQ 201
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0060: TEA5767 detected.
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
Feb 15 18:40:54 juno kernel: [17180580.568000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb 15 18:40:55 juno kernel: [17180580.816000] tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
Feb 15 18:40:55 juno kernel: [17180580.836000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
Feb 15 18:40:59 juno kernel: [17180585.604000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Feb 15 18:40:59 juno kernel: [17180585.724000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: Hauppauge model 23559, rev E491, serial# 9578267
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: tuner model is Philips FQ1216AME MK4 (idx 91, type 56)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: audio processor is CX25843 (idx 37)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
Feb 15 18:40:59 juno kernel: [17180585.788000] tveeprom 0-0050: has radio, has no IR remote
Feb 15 18:40:59 juno kernel: [17180585.788000] ivtv0: This is the first unit of a PVR500
Feb 15 18:41:00 juno kernel: [17180586.568000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
Feb 15 18:41:00 juno kernel: [17180586.784000] ivtv0: Encoder revision: 0x02050032
Feb 15 18:41:00 juno kernel: [17180586.784000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
Feb 15 18:41:00 juno kernel: [17180586.788000] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
Feb 15 18:41:00 juno kernel: [17180586.788000] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
Feb 15 18:41:01 juno kernel: [17180586.924000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
Feb 15 18:41:01 juno kernel: [17180586.928000] ivtv0: Create encoder radio stream
Feb 15 18:41:01 juno kernel: [17180586.928000] tuner 0-0061: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4))
Feb 15 18:41:01 juno kernel: [17180587.172000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
Feb 15 18:41:01 juno kernel: [17180587.176000] ivtv:  ======================  NEXT CARD  ======================
[COLOR=Red]<snip>[/COLOR]
Feb 15 18:41:07 juno kernel: [17180593.704000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
Feb 15 18:41:07 juno kernel: [17180593.704000] ivtv:  ====================  END INIT IVTV  ====================

```

Just to be sure it can't be blamed on other things, can you try booting with noapic and nosmp?  I've read a few things pointing at these being trouble for some people.  Also, are you running cpufreqd or anythign similar?

---

### Post by bnuytten on 2007-02-15
Okay, several things happened in the meantime. The kernel was updated from the "stock" Edgy kernel to 2.6.17-11. After booting the new kernel with the noapic and nosmp options set the system did not crash anymore.

Kernel version:
```
Linux juno 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
```

Contents of /boot/grub/menu.lst
```

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash [COLOR="Red"]noapic nosmp[/COLOR]
#kernel         /vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
#quiet
savedefault
boot
```


Possible causes/solutions:
[LIST=1]
[*]update from 2.6.17-10 to 2.6.17-11
[*]noapic, nosmp
[*]SMP kernel on "non-smp" CPU: AMD Athlon(TM) XP 2500+
[/LIST]

I may do some further testing to see if I can crash the machine again by removing the noapic and nosmp options to point out the real cause.

---

### Post by bnuytten on 2007-02-15
The test results:

2.6.17-11 default options: crash
2.6.17-11 noapic nosmp: crash, went fine once 
2.6.17-11 noapic: crash
2.6.17-11 nosmp: crash

Some more info:
```
uname -a
Linux juno 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

dpkg --list | grep ivtv
ii  ivtv-firmware                              0.20061007                           Firmware used by the IVTV project
ii  ivtv-modules-2.6.17-10-generic             0.7.0-2+2.6.17-10.33                 ivtv Linux kernel module (0.6 branch)
ii  ivtv-modules-2.6.17-11-generic             0.7.0-2+2.6.17.1-11.35               ivtv Linux kernel module (0.6 branch)
ii  ivtv-source                                0.7.0-2                              source for ivtv drivers (0.7 branch)
ii  ivtv-utils                                 0.7.0-2                              utilities for use with the ivtv kernel drive
ii  libvideo-ivtv-perl                         0.13-3                               Perl extension for using V4l2 in the ivtv pe

```

---

### Post by superm1 on 2007-02-15
> **bnuytten said:**
> The test results:

2.6.17-11 default options: crash
2.6.17-11 noapic nosmp: crash, went fine once 
2.6.17-11 noapic: crash
2.6.17-11 nosmp: crash

Some more info:
```
uname -a
Linux juno 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

dpkg --list | grep ivtv
ii  ivtv-firmware                              0.20061007                           Firmware used by the IVTV project
ii  ivtv-modules-2.6.17-10-generic             0.7.0-2+2.6.17-10.33                 ivtv Linux kernel module (0.6 branch)
ii  ivtv-modules-2.6.17-11-generic             0.7.0-2+2.6.17.1-11.35               ivtv Linux kernel module (0.6 branch)
ii  ivtv-source                                0.7.0-2                              source for ivtv drivers (0.7 branch)
ii  ivtv-utils                                 0.7.0-2                              utilities for use with the ivtv kernel drive
ii  libvideo-ivtv-perl                         0.13-3                               Perl extension for using V4l2 in the ivtv pe

```
Okay next order of business is to try the newer version of ivtv.  At that same wiki page, there are directions how to move up to the latest version (0.7.3).  It may be more stable, and if its not - the first question that the ivtv mailing list is going to ask is if you are on the latest version.

---

### Post by bnuytten on 2007-02-15
> **superm1 said:**
> Okay next order of business is to try the newer version of ivtv.  At that same wiki page, there are directions how to move up to the latest version (0.7.3).  It may be more stable, and if its not - the first question that the ivtv mailing list is going to ask is if you are on the latest version.


Well, glad I read your post. I just compiled the ivtv driver from source. Off course I read the README file :wink:. It states clearly that for kernel versions 2.6.17 ivtv version 0.7.x has to be used! Still wondering why a driver from the 0.6.x branch is in the repositories...

Test capture works. For now that is :)

---

### Post by superm1 on 2007-02-15
> **bnuytten said:**
> Well, glad I read your post. I just compiled the ivtv driver from source. Off course I read the README file :wink:. It states clearly that for kernel versions 2.6.17 ivtv version 0.7.x has to be used! Still wondering why a driver from the 0.6.x branch is in the repositories...

Test capture works. For now that is :)
That one you built was 0.7.0, just the packager at the time forgot to update a 0.6 "number" in the build files.  I'm the packager for everything beyond 0.7.0, and so that's been fixed now.  Hope this keeps up being stable!

---

