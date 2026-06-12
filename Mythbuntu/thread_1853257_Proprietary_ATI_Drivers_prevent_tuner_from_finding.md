---
title: "Proprietary ATI Drivers prevent tuner from finding channels"
date: 2011-10-01
forum: Mythbuntu
---

### Post by celinedrules on 2011-10-01
I have an ATI 2600XT HD video card and a WinTv-HVR-950q tv tuner.

I can run mythtv just fine when I use the open source drivers but I can't enable dual displays. If I install the proprietary ATI drivers, I can use dual displays just fine however my tuner stops working. It won't lock on to any channels. If I try and do a rescan of channels, nothing is found. If I switch back to the open source driver, the channels are all found but no dual displays.

With the open source drivers, I can select to use both displays but it still only shows on the primary display.

Any help would be appreciated.

---

### Post by thatguruguy on 2011-10-01
That is... really odd.  Have you checked your back-end logs?

---

### Post by klc5555 on 2011-10-02
Things like this are not infrequently vmalloc issues, where a proprietary video driver consumes too much of the virtual memory allocation at boot to allow the driver for the tuner card or some other kernel driver to load properly. On the other hand, when you can't get locks (though scanning works), some portion of the tuner's firmware has often failed to load. That might be the significant factor here as the kernel firmware doesn't actually load for this particular USB tuner until the first time an application (in this case mythtv-setup) tries to access it. (As described here in the section "Sample Kernel Output": [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q) )

Check the output from dmesg (or maybe: dmesg | grep xc5000) at a prompt (after a failed scan/lock attempt), and see if the output is giving you any errors pertaining to firmware (or driver) loading for your tuner. If vmalloc were to need to be increased at boot, this can be easily done.

---

### Post by celinedrules on 2011-10-04
Even if I have everything running fine with the open source drivers and I restart the computer the same thing happens. After a restart, I ran dmesg | grep xc5000 this is what I get:

[   22.593111] xc5000 2-0061: creating new instance
[   22.598437] xc5000: Successfully identified at address 0x61
[   22.598440] xc5000: Firmware has not been loaded previously
[   22.639654] xc5000 2-0061: attaching existing instance
[   22.662694] xc5000: Device not found at addr 0x61 (0x704)

Edit:

Never mind, I fixed it by following this post [http://ubuntuforums.org/showthread.php?t=1332986](http://ubuntuforums.org/showthread.php?t=1332986).

---

### Post by thatguruguy on 2011-10-05
Dealing with the time-out issue on the 950Q was specifically dealt with in the HOW-TO I posted about that tuner, which you can find [here]("http://ubuntuforums.org/showthread.php?t=1634328").  You may want to review that thread.

If your issue is resolved, you may consider marking this thread as solved.

---

### Post by PhilWig on 2011-10-05
Just a wild stab in the dark.

I don't run your hardware but this is a bit like a problem I had with a Hauppauge T500 tuner and nvidia graphics.  Changing video settings (vga to HDMI or vice versa) upsets the tuner and changing them back mends it. 

Have you tried a close down, turn power off completely at the wall, leave 10 seconds then power up again?  I had to do that after each video setting change.

HTH
Phil

---

### Post by thatguruguy on 2011-10-05
The OP stated that the problem was fixed.

---

### Post by PhilWig on 2011-10-07
> The OP stated that the problem was fixed
Quite right.  Apologies.
Phil

---

### Post by thatguruguy on 2011-10-07
No reason to apologize.  You're absolutely right that sometimes it is worthwhile to shut down the computer completely if you're having troubles getting the usb tuner to tune anything.  I think what happens, on occasion, is that there can be a race condition when the computer first starts up where the computer will try to start using the tuner before it is completely initialized, which can cause all subsequent attempts to use the tuner to fail.  Sometimes doing a completely cold boot can fix that.

---

