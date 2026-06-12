---
title: "Blue Snowflake not showing name in system settings"
date: 2014-06-10
forum: Multimedia Software
---

### Post by bhweb on 2014-06-10
I recently updated from Ubuntu 12.10 to 13.10.  I have a Blue Snowflake microphone and in the system settings under Sound, input devices, it used to show up as "Blue Snowflake".  Now I noticed today that it no longer shows up that way.  I see "Microphone 1.1 root hub" which appears to be the Snowflake.  It kind of works, except I think the volume is much lower than it used to be.  I used to have it at 100% and it was fine, but when recording a video today, I noticed I had to turn it up almost all the way to get the sound the right level.

I unplugged it and plugged it back in so I could see the messages in syslog which follow.  Is there a way to get this showing up correctly and working like it used to?

```

Jun  9 22:30:48 BRUCE-CUSA kernel: [37713.997399] usb 4-3: new full-speed USB device number 6 using ohci-pci
Jun  9 22:30:48 BRUCE-CUSA kernel: [37714.164485] usb 4-3: New USB device found, idVendor=b58e, idProduct=f5a5
Jun  9 22:30:48 BRUCE-CUSA kernel: [37714.164497] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun  9 22:30:48 BRUCE-CUSA kernel: [37714.164505] usb 4-3: Product: Blue Snowflake
Jun  9 22:30:48 BRUCE-CUSA kernel: [37714.164510] usb 4-3: Manufacturer: Blue
Jun  9 22:30:48 BRUCE-CUSA mtp-probe: checking bus 4, device 6: "/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3"
Jun  9 22:30:48 BRUCE-CUSA mtp-probe: bus: 4, device: 6 was not an MTP device
Jun  9 22:30:48 BRUCE-CUSA pulseaudio[2465]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Jun  9 22:30:48 BRUCE-CUSA pulseaudio[2465]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-Blue_Blue_Snowflake-00-Snowflake" card_name="alsa_card.usb-Blue_Blue_Snowflake-00-Snowflake" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.

```

---

