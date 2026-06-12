---
title: "Mini-DVI to Composite for TV"
date: 2013-02-05
forum: Multimedia Software
---

### Post by K3ITHK on 2013-02-05
I have some old CRT TVs that I want to connect my laptop to. I have a late 2006 model MacBook and I have the [Apple Mini-DVI to S-Video/Composite Adapter]("http://support.apple.com/kb/HT3235") (part number M9319G). When I connect everything, and set the monitor VGA1 to 640x480 at 60hz (using gtf and xrandr) I get some output, but it's flickering and it looks like the image is moving across the screen really fast, in black and white. I'm wondering how to properly set this up. I'm using Ubuntu 12.04. 

Thanks!

---

### Post by Thee on 2013-02-05
Try setting the resolution to:
720x576 if your TV is PAL, or
720x480 if your TV is NTSC

---

### Post by K3ITHK on 2013-02-07
Hmm no it's still not quite right. The TV is NTSC. This is the modeline I was using which is from the [MythTV modeline database]("http://www.mythtv.org/wiki/Modeline_Database#NTSC525_itu-r.2Fbt:_470_601_656"):

```
"720x480@30i" 13.5 720 736 799 858 480 486 492 525 interlace -hsync -vsync
```

Note that it works in OSX. Here is some info from OSX:

```
$ system_profiler SPDisplaysDataType
Graphics/Displays:

    Intel GMA 950:

      Chipset Model: GMA 950
      Type: GPU
      Bus: Built-In
      VRAM (Total): 64 MB of Shared System Memory
      Vendor: Intel (0x8086)
      Device ID: 0x27a2
      Revision ID: 0x0003
      Displays:
        Color LCD:
          Resolution: 1280 x 800
          Pixel Depth: 32-Bit Color (ARGB8888)
          Main Display: Yes
          Mirror: Off
          Online: Yes
          Built-In: Yes
        NTSC/PAL:
          Resolution: 720 x 480 @ 60 Hz
          Pixel Depth: 32-Bit Color (ARGB8888)
          Mirror: Off
          Online: Yes
          Rotation: Supported
          Interlaced: Yes
          Television: Yes

```

---

### Post by Thee on 2013-02-08
Try this:

```
xrandr --output NAME_OF_DEVICE --set mode NTSC-M
```

Change the NAME_OF_DEVICE to what ever it is called.

---

### Post by K3ITHK on 2013-02-11
That didn't work, it doesn't seem to know that mode.

```
$ xrandr --output VGA1 --set mode NTSC-M
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  33
  Current serial number in output stream:  33

```

---

### Post by K3ITHK on 2013-02-21
Anyone?

---

