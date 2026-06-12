---
title: "Canon Powershot A520"
date: 2009-08-17
forum: Multimedia Software
---

### Post by samirjohn on 2009-08-17
Dear Ubuntu Gurus,

First of all you guys are the best! Ubuntu is far, far superior to ANY MS OS!

Now my problem...

I am trying to copy pictures off my digital camera to disk. The camera is a Canon Powershot A520. When I try to do an "import photos" on gthumb, I get the following message:

[COLOR=Red]**An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4a9, product 0x30c1). Make sure this device is connected to the computer.**[/COLOR]

When I run the following command "[COLOR=Blue]**ls -l /proc/bus/usb/**[/COLOR]" I get "[COLOR=Green]**total 0**[/COLOR]"

How do I get this to work?

Thanks!

---

### Post by tgalati4 on 2009-08-18
Unplug the camera.

In a terminal:

dmesg | tail

Note the time in seconds (since boot) at the bottom of the output.

Plug in the camera.

Post the output of:

dmesg | tail -30

It should be plug-and-play.  Sounds like a hardware fault.  Make sure your batteries are fresh.  If all else fails, pull the memory card and use a card reader.

Perhaps you can reflash your camera with a newer firmware.

---

### Post by samirjohn on 2009-08-18
First off, I should mention that my Ubuntu version is 9.04. The batteries of the camera are fully charged. It's a relatively new camera, but I can check if there are any new updates to its firmware.

Meanwhile...

Here's the dmesg|tail with the camera unplugged:

[   16.449346] Bridge firewalling registered
[   17.857052] ppdev: user-space parallel port driver
[   19.971648] [drm] Initialized drm 1.1.0 20060810
[   19.978364] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.978370] pci 0000:00:02.0: setting latency timer to 64
[   19.978499] pci 0000:00:02.0: irq 2300 for MSI/MSI-X
[   19.978602] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   19.981980] [drm:i915_setparam] *ERROR* unknown parameter 4
[   26.673014] eth0: no IPv6 routers present
[  267.424125] CE: hpet increasing min_delta_ns to 15000 nsec

Here's the dmesg|tail with the camera plugged in:

[   10.821101] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.821188] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.895599] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.000087] Clocksource tsc unstable (delta = -162199540 ns)
[   11.583826] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input8
[   11.611079] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input9
[   12.088076] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x20171704
[   12.415519] lp: driver loaded but no devices found
[   12.539360] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k
[   12.561504] EXT3 FS on sda1, internal journal
[   13.166455] type=1505 audit(1250648811.803:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1954
[   13.219286] type=1505 audit(1250648811.856:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1958
[   13.219429] type=1505 audit(1250648811.856:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1958
[   13.219479] type=1505 audit(1250648811.856:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1958
[   13.219526] type=1505 audit(1250648811.856:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1958
[   13.367507] type=1505 audit(1250648812.004:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1963
[   13.367718] type=1505 audit(1250648812.004:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1963
[   13.399857] type=1505 audit(1250648812.036:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1967
[   16.427096] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.427099] Bluetooth: BNEP filters: protocol multicast
[   16.449346] Bridge firewalling registered
[   17.857052] ppdev: user-space parallel port driver
[   19.971648] [drm] Initialized drm 1.1.0 20060810
[   19.978364] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.978370] pci 0000:00:02.0: setting latency timer to 64
[   19.978499] pci 0000:00:02.0: irq 2300 for MSI/MSI-X
[   19.978602] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   19.981980] [drm:i915_setparam] *ERROR* unknown parameter 4
[   26.673014] eth0: no IPv6 routers present
[  267.424125] CE: hpet increasing min_delta_ns to 15000 nsec

---

### Post by tgalati4 on 2009-08-18
Well, the last entry was at 267 seconds since boot.  On both outputs.  Therefore when you plug your camera in, the computer is not detecting it at all.

Did you try turning your camera on after you plug it in?

Unless it shows up in dmesg, you won't get very far.

Perhaps you have a bad cable, or dirty contacts in the camera's usb port.

---

### Post by alphacrucis2 on 2009-08-19
> **tgalati4 said:**
> Well, the last entry was at 267 seconds since boot.  On both outputs.  Therefore when you plug your camera in, the computer is not detecting it at all.

Did you try turning your camera on after you plug it in?

Unless it shows up in dmesg, you won't get very far.

Perhaps you have a bad cable, or dirty contacts in the camera's usb port.

If that camera is similar to mine, an A560 you also have to slide a switch on the back of the camera to change from "photo" mode to "playback" mode. The camera USB port is disabled when the switch is set to "photo" mode.

---

### Post by tgalati4 on 2009-08-19
I have a powershot A70 and yes, you do have to put it in "playback" mode then turn it on for USB to be recognized.  There is also a setting buried in the camera's connectivity settings for USB mode.  I forget the modes, but there are only two of them, so try each mode.

---

### Post by samirjohn on 2009-08-20
Thank you so much, "**tgalati4**"and "alphacrucis2" - your suggestion about the playback mode worked! I had to flick the switch (behind the camera) from photo to playback mode and presto, Ubuntu detected it beautifully! It even recognized the make of the camera and everything!

:guitar:

Earlier, when I was using MS Windows, I had the drivers already installed from the CD that came with the camera. So simply plugging it in, in any mode launched the software. In this case since there was no deiver explicitly installed (on Ubuntu), I had to trigger the OS to do its own detection, by flicking the switch to playback mode, and it recognized if beautifully!

It's a great OS like Ubuntu and an equally great community of supporters like you all that will take this really far into the future!

Long Live UBUNTU!!

---

### Post by tgalati4 on 2009-08-20
Good.  I couldn't sleep last night thinking about it.

---

