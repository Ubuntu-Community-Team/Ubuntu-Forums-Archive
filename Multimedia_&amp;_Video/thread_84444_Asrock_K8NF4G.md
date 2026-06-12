---
title: "Asrock K8NF4G"
date: 2005-10-31
forum: Multimedia &amp; Video
---

### Post by oldmarti on 2005-10-31
Hi,
I just buy motherboard K8NF4G (from asrock) and install ubuntu 5.10.
But there isn't sound and VGA work only if I set VESA driver in x.org.
I try nv driver and nvidia (from nvidia-glx package) but no effect.
It's written in the manual - VGA is NVIDIA 6100, audio is Realtek ALC850 7.1 channel AC'97 audio codec.
I'll be happy for any advice

---

### Post by mdoering on 2006-02-05
Hi, oldmarti! I have the same board (now), bought yesterday. Graphics work for the new dapper release with modular X. But it could be, that it also would work with the non-modular X11 now. You have to make use of the proprietory nvidia drivers and clean up the monitor section of xorg.config a bit. This is mine now:

```
Section "Monitor"
    Identifier     "SDM-M51"
    Option         "DPMS"
    Option         "UseEdidDpi"   "FALSE"
    Option         "DPI"   "96 x 96"
    DisplaySize     270     203     # 1024x768 96dpi
#       HorizSync       28-49
#       VertRefresh     43-72
EndSection
```

The DPI related settings a specific for the nvidia driver, because otherwise some fonts will be very small. And the must be no sync settings in it!!! This for the device section:

```
Section "Device"
    Identifier     "nVidia 6100"
    Driver         "nvidia"
EndSection
```


I also got the lm-sensors working the get CPU temperature and fan rpm. But I did not yet find a way to activly control both of them.

The sound, I did not get it going yet, though there seems to be support in some newer kernels for this chipset. The gentoo folks seem to have it running. So, it's just a question of time.

I tried to underclock the sempron64 3000+ processor, but my BIOS seems to forget all that till the next reboot - it's not persistent as it seems. My goal was to have a system which has a very low powerconsumption - and I'm very near to this goal.

All in all I'm very happy with the board/processor combination. It's small, has good onboard-graphics and is modern in all ways. Good deal for 59 &#8364;. I would be interested, how far you came with hardware configuration.

---

### Post by sandisn on 2006-02-06
Hi there!

So basically we have to wait untill dapper? Or perhaps it is possible to recompile the kernel?

By the way I have another problem - my computer doesn't turn off. It shuts down and then immediately turns itself on. Could it be related to some weird bios setting?

---

### Post by seconha on 2006-03-05
sorry

---

