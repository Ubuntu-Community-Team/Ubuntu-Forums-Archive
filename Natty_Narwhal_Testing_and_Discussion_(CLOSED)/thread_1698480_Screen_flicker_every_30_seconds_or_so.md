---
title: "Screen flicker every 30 seconds or so"
date: 2011-03-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lucasreece on 2011-03-02
Just installed the daily build of Natty on a Dell Dimension E520 with an ATI X1300 graphics card.

Booting from the live CD and subsequently after installing, the screen flickers to black and back every 30 seconds or so.

It's driving me mad. Any ideas please?

Information: Machine was fine with Ubuntu 10.04 and 10.10.

---

### Post by metalf8801 on 2011-03-02
> **lucasreece said:**
> Just installed the daily build of Natty on a Dell Dimension E520 with an ATI X1300 graphics card.

Booting from the live CD and subsequently after installing, the screen flickers to black and back every 30 seconds or so.

It's driving me mad. Any ideas please?

Information: Machine was fine with Ubuntu 10.04 and 10.10.


Have you check on [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) for a bug report that covers this problem and confirmed that you are having the same problem or written your own bug report if one does not already exist? 

Here is A Beginners Guide to Filing Bug Reports  [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by MacUntu on 2011-03-02
It's probably a problem with your monitor (or it's EDID to be more precise). Can you post the output of "dmesg"?

---

### Post by rubenverweij on 2011-03-02
I'm seeing this too with the open source nouveau drivers and a hp 1730 monitor. 
```

dmesg | grep nouveau
[   10.032351] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.076507] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x04a100a1)
[   10.076522] fb: conflicting fb hw usage nouveaufb vs VESA VGA - removing generic driver
[   10.094377] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   10.173557] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   10.173566] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   10.173573] [drm] nouveau 0000:01:00.0: Bios version 05.44.a2.03
[   10.173581] [drm] nouveau 0000:01:00.0: TMDS table version 1.1
[   10.173585] [drm] nouveau 0000:01:00.0: BIT table 'd' not found
[   10.173590] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[   10.173597] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01011310 00000028
[   10.173603] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00000000
[   10.173607] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 020223f1 0000c020
[   10.173614] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 7 2
[   10.173620] [drm] nouveau 0000:01:00.0:   0: 0x00000100: type 0x00 idx 0 tag 0xff
[   10.173625] [drm] nouveau 0000:01:00.0:   1: 0x00001031: type 0x31 idx 1 tag 0x07
[   10.173630] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   10.173635] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   10.173639] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   10.173651] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDD8E
[   10.181967] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE059
[   10.236260] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE491
[   10.236294] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE5EE
[   10.244134] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE6A0
[   10.279569] [drm] nouveau 0000:01:00.0: mem timing table length unknown: 14
[   10.279580] [drm] nouveau 0000:01:00.0: 1 available performance level(s)
[   10.279587] [drm] nouveau 0000:01:00.0: 0: memory 400MHz core 350MHz fanspeed 100%
[   10.279605] [drm] nouveau 0000:01:00.0: c: memory 401MHz core 200MHz
[   10.280647] [drm] nouveau 0000:01:00.0: Detected 128MiB VRAM
[   10.281450] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode
[   10.281456] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   10.289395] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   10.289418] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[   10.289473] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 2)
[   10.553106] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x49000, bo f48d6a00
[   10.555944] fb0: nouveaufb frame buffer device
[   10.555979] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   20.940186] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[   20.940198] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
[   20.951556] [drm] nouveau 0000:01:00.0: 0xD1C8: Parsing digital output script table
[   21.004127] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[   21.004141] [drm] nouveau 0000:01:00.0: Output DVI-D-1 is running on CRTC 1 using output A
[   31.133141] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[   31.153397] [drm] nouveau 0000:01:00.0: 0xD1C8: Parsing digital output script table
[   31.208020] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[   31.208027] [drm] nouveau 0000:01:00.0: Output DVI-D-1 is running on CRTC 1 using output A
[ 2021.670729] [drm] nouveau 0000:01:00.0: PGRAPH - ERROR nsource: (unknown bits 0x00400000) nstatus: PROTECTION_FAULT
[ 2021.670750] [drm] nouveau 0000:01:00.0: PGRAPH - ch 3 (0x00073030) subc 7 class 0x4497 mthd 0x1808 data 0x00000000
[ 8546.165422] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[ 8546.175590] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[ 9999.446016] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[ 9999.462253] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[20232.092276] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[20232.108134] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[23500.945305] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[23500.955266] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[23501.065934] [drm] nouveau 0000:01:00.0: Disabling fbcon acceleration...
[23501.065940] [drm] nouveau 0000:01:00.0: Unpinning framebuffer(s)...
[23501.065986] [drm] nouveau 0000:01:00.0: Evicting buffers...
[23501.252804] [drm] nouveau 0000:01:00.0: Idling channels...
[23501.253214] [drm] nouveau 0000:01:00.0: Suspending GPU objects...
[23501.316400] [drm] nouveau 0000:01:00.0: And we're gone!
[23501.316437] nouveau 0000:01:00.0: PCI INT A disabled
[23501.332027] PM: suspend of drv:nouveau dev:0000:01:00.0 complete after 266.098 msecs
[23501.428018] nouveau 0000:01:00.0: BAR 0: set to [mem 0xde000000-0xdeffffff] (PCI address [0xde000000-0xdeffffff])
[23501.428027] nouveau 0000:01:00.0: BAR 1: set to [mem 0xe0000000-0xefffffff pref] (PCI address [0xe0000000-0xefffffff])
[23501.428034] nouveau 0000:01:00.0: BAR 2: set to [mem 0xdd000000-0xddffffff] (PCI address [0xdd000000-0xddffffff])
[23501.428058] nouveau 0000:01:00.0: restoring config space at offset 0x1 (was 0x2b00003, writing 0x2b00007)
[23501.431987] [drm] nouveau 0000:01:00.0: We're back, enabling device...
[23501.431995] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[23501.432020] [drm] nouveau 0000:01:00.0: POSTing device...
[23501.432026] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDD8E
[23501.460254] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE059
[23501.516217] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE491
[23501.516261] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE5EE
[23501.524138] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE6A0
[23501.524235] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode
[23501.524241] [drm] nouveau 0000:01:00.0: Restoring GPU objects...
[23501.533121] [drm] nouveau 0000:01:00.0: Reinitialising engines...
[23501.533426] [drm] nouveau 0000:01:00.0: Restoring mode...
[23501.533559] [drm] nouveau 0000:01:00.0: 0xD1C8: Parsing digital output script table
[23501.645831] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[23501.700045] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 2)
[23501.720575] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[23501.720582] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
[23501.720602] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[23501.741035] [drm] nouveau 0000:01:00.0: 0xD1C8: Parsing digital output script table
[23501.796019] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[23501.796025] [drm] nouveau 0000:01:00.0: Output DVI-D-1 is running on CRTC 1 using output A
[23501.796036] PM: resume of drv:nouveau dev:0000:01:00.0 complete after 364.048 msecs

```

---

### Post by cariboo on 2011-03-02
@rubenverweij

Do you get the same thing when using nvidia-current?

---

### Post by lucasreece on 2011-03-02
> **MacUntu said:**
> It's probably a problem with your monitor (or it's EDID to be more precise). Can you post the output of "dmesg"?

What's the command here please? Just "dmesg"? Thanks.

---

### Post by lucasreece on 2011-03-02
Never mind. I've just filed a bug report to launchpad.

---

### Post by cariboo on 2011-03-02
A link to the bug please.

---

### Post by lucasreece on 2011-03-03
link to bug report... [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727979](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727979)

---

### Post by MacUntu on 2011-03-03
Your monitor's EDID seems fine, so that shouldn't be the problem.

---

### Post by CraigPaleo on 2011-03-21
That happened to me with Kubuntu 11.04, OpenSUSE 11.4 and Chakra. I have a Radeon X1950 Pro.  The problem was my VGA adapter ( I have 2 computers sharing a monitor.) Removing the adapter and using straight DVI fixed it. No more annoying flashes. 

I know some people don't have a choice but it may help fix the bug. Should I add my experience to the bug report?

---

### Post by cariboo on 2011-03-21
I get the same thing on a system currently running Fedora 15, running:

```
dmesg | grep EDID
```

shows me that I'm getting an EDID checksum error with a remainder of 222.

---

### Post by zer010 on 2011-04-02
Yep, I have the same flicker going on with the Beta1 release.  I have trying to figure out how to get the proprietary driver (173) installed, but I haven't figured that one out yet.  I use it in 10.04 and have no major issues with it.

---

### Post by CraigPaleo on 2011-04-03
Do you have a VGA to DVI adapter? That was my problem. Going DVI to DVI solved it for me.

---

### Post by VMC on 2011-04-03
I got that flicker a few days ago. But usually only once maybe twice. Then that's all. I haven't seen it for a few days now. I'll check out your bug report and attach myself also. thanks.

---

