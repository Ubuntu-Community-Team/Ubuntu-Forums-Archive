---
title: "ATI Radeon X300 - fuzzy display"
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by vrode on 2006-01-11
Hi,

I downloaded (off ATI's website) and installed ati driver v8.20.8 (ATI Radeon x300 card) for my IBM Z60m 17" LCD screen.

I followed the below how-to and it appears to have setup fine except I have shadowing effect (fuzzyness) of characters which is bothering my eyes. 

[http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

I even tried using different fonts w/ ubuntu 5.10 with no avail.

Is there anything in the setup that I can configure to smooth the characters?


fglrxinfo output shows:
OpenGL vendor string: ATI Technologies Inc.
OpenGL vendor string: MOBILITY RADEON X300 Generic
OpenGL vendor string: 1.3.5519 (X4.3.0-8.20.8)

glxgears -iacknowledgethatthisistoolisnotbenchmark
9307 frames in 5.0 seconds = 1861.251 FPS

Resolution supported:
1280x800 800x600 640x480


Let me know if you need any specific outputs.

Any pointers will be greatly appreciated.


regards,
/virendra

---

### Post by vrode on 2006-01-11
thought that I'd provide more information:

output from my xorg.conf:

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "type1"
        Load    "vbe"
EndSectSection "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        65536
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection
ion

/var/log/Xorg.0.log
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.20.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.20g1
(II) ATI Proprietary Linux Driver Build Date: Dec  6 2005 20:05:53
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.20.1-driver-lnx-232334
(--) Chipset MOBILITY RADEON X300 (M22 5460) found


regards,
/virendra

---

### Post by dasteve2 on 2006-05-05
Hello, I have the same problem using a Radeon 9000m, does anyone have any ideas?

---

