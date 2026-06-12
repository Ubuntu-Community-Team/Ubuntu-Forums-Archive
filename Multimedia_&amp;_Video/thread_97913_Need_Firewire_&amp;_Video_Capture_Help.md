---
title: "Need Firewire &amp; Video Capture Help"
date: 2005-12-01
forum: Multimedia &amp; Video
---

### Post by jabster on 2005-12-01
Hi.

I just purchased a canon ZR100 DV camcorder. I am trying to capture the video to my computer, but seem unable to do so.

I just bought a firefire card ([http://www.newegg.com/product/product.asp?item=N82E16815124003](http://www.newegg.com/product/product.asp?item=N82E16815124003)) that claims to support linux, and looks to be fully standards compliant. dmesg | grep 1394 gives this:
```
[4294697.545000] ieee1394: Initialized config rom entry `ip1394'
[4294697.554000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294697.558000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[4294697.610000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9c000                            00-f9c007ff]  Max Packet=[2048]
[4294698.877000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004c01000040e7]
[4297876.681000] ieee1394: raw1394: /dev/raw1394 device initialized
[4297914.770000] ohci1394: fw-host0: IR legacy activated
[4297918.825000] ohci1394: fw-host0: IR legacy activated

```

I've got kino installed, and it tells me that the raw1394 driver is not loaded or that it doesn't have read/write access to /dev/raw1394. EVen tried a "sudo modprobe raw1394." From what I've googled, the "unexpected..1000" is not a problem.

I think I have everything I need installed. I searched with adept for 1394, and installed everything except the dev packages.

I am running kubuntu 5.1 with the kde3.5 upgrade. AMD64 3000+, Asus A8V.

Can someone give me some pointers on getting video capture from the camera working? I have no other firewire devices, and am therefore unable to test if the card works. (Tho, actually, I think I may have a USB/FW HD at work that I could borrow for the weekend....will have to check on that.)

According to the camera manual, a computer with a ieee1394 capture card will function. Only mentions windows and mac, of course.

Thanks,
john

---

### Post by GMachine_24 on 2005-12-04
Hi:

Open a terminal window and start Kino with:

>sudo kino
password:XXXXX

This should do it. Don't ask me why. I'd like to know if your audio capture is clear on playback because mine is garbled horribly.

GMachine

---

### Post by binks on 2005-12-05
this works great :cool: 
i have checked my capture and both audio and video are fine ;) :p

---

### Post by Dragonbite on 2006-01-19
Just found someting in another post that says > You need to make sure that you belong to the user group video. If you
need to change the permissions so that they persist from one session to
the next you can do so in the
file /etc/udev/permissions.d/udev.permissions
I believe the problem is with the kernels and udevs incomplete
(Currently) ie1394 support. I believe its important to make sure you
have read write access.

PeterThis posting is [re:MiniDV capture over firewire - Kino]("http://www.ubuntuforums.org/showthread.php?t=117757")

I haven't tried it yet, but this could eliminate having to go into "sudo".

---

