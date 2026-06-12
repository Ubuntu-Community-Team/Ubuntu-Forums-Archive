---
title: "EDID check for monitor no longer working?"
date: 2012-05-29
forum: Multimedia Software
---

### Post by salinmooch on 2012-05-29
Hi,

I have an older monitor (a viewsonic VA720) that has been working fine with my various ubuntu distros for a few years now.  I have been using it as a second display for my laptops running unity in 12.04 for a month now and I would plug it in and the resolutions were detected properly (name listed and resolution modes correct) (max is 1280x1024).  Now however it detects the display as "unknown" and only gives a max resolution 1024x768.  I'm sure I could manually find out how to manually set the resolutions but since it worked before I thought I'd ask to see if anyone has any clues to what might have gone wrong.

When I booted up yesterday, and entered the desktop I received an error along the lines that my display settings were in valid and then I had to reset my secondary monitor settings but the monitor now showed up as "unknown" and has limited resolutions available. 

I also had this new error (seen in dmesg):

```

[86349.907194] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 128
[86349.907199] Raw EDID:
[86349.907203]      ff ff 80 ff ff ff ff 00 5a 63 09 6c 01 01 01 01
[86349.907205]      2e 0c 01 03 08 22 1b 78 2a 47 06 a5 5c 47 9c 25
[86349.907207]      1e 4f 54 bf ef 80 81 80 01 01 01 01 01 01 01 01
[86349.907210]      01 01 01 01 01 01 30 2a 00 98 51 00 2a 40 30 70
[86349.907212]      13 00 52 0e 11 00 00 1e 00 00 00 ff 00 41 31 44
[86349.907214]      30 32 34 36 30 30 36 30 32 0a 00 00 00 fd 00 32
[86349.907216]      4b 1e 52 0e 00 0a 20 20 20 20 20 20 00 00 00 fc
[86349.907218]      00 56 41 37 32 30 0a 20 20 20 20 20 20 20 00 0d
[86349.907224] i915 0000:00:02.0: VGA-1: EDID block 0 invalid.

```Some more info on the computer and card:

```
3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
lscpi |grepVGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
```

and

```
sudo get-edid |parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "Intel(r)Crestline Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

parse-edid: EDID checksum passed.

    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:0
    # Block type: 2:0 3:fe
    # Block type: 2:0 3:fc
    Identifier "LP154WX4-TLC8"
    VendorName "LPL"
    ModelName "LP154WX4-TLC8"
    # Block type: 2:0 3:0
    # Block type: 2:0 3:fe
    # Block type: 2:0 3:fc
    # DPMS capabilities: Active off:no  Suspend:no  Standby:no

    Mode     "1280x800"    # vfreq 59.976Hz, hfreq 48.941kHz
        DotClock    69.300000
        HTimings    1280 1328 1352 1416
        VTimings    800 803 809 816
        Flags    "-HSync" "-VSync"
    EndMode
    # Block type: 2:0 3:0
    # Block type: 2:0 3:fe
    # Block type: 2:0 3:fc
EndSection

```Not really sure how to the read the latter but it seems to be detecting the laptop display fine (1280x800) but nothing on the external.

Perhaps something broke in my monitor?  I also stuck this in another laptop running 12.04 and had the same issues.  I borrowed my wife's windows machine and it was able to generate the higher resolutions in the external montiro but it was also displaying a lot of resolutions that the monitor was not capable of so I'm not really sure if it was checking EDIDs.

I don't mind manually setting the resolutions if its relatively easy, but do not want to turn off automatically setting up external displays (which is nice when giving talks, etc.)

Any ideas?

---

### Post by salinmooch on 2012-05-29
Well I'm still not sure why the monitor stopped being automagically detected properly but I was able to get my resolution hacked back to working following this info:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Still would like to see if I can figure out what broke though.

---

