---
title: "How does one use a DV camera over usb/firewire adapter?"
date: 2011-08-01
forum: Multimedia Software
---

### Post by Aisteru on 2011-08-01
I bought a USB to firewire cable to use with a DV camera, but I don't know what to do now. Do I need to enable firewire drivers, or is there something else I should do? I know I should read the manual, but if someone could tell me which manual, I would appreciate it :-)

---

### Post by Steeperton on 2011-08-01
Try installing Kino - that was the only software I could find that could connect to my DV camera. 

That was a couple of years ago mind - it broke, and I've now bought a SD card one,which is much easier to use!

---

### Post by Toz on 2011-08-01
What version of xubuntu are you using? If its 11.04, there is some bad news. See: [https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680]("https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680")

I recently tried to assist someone with getting firewire working with no luck. Have a look at: [http://ubuntuforums.org/showthread.php?t=1772830&highlight=firewire]("http://ubuntuforums.org/showthread.php?t=1772830&highlight=firewire")

There are some reports in both links about people getting it to work.

---

### Post by Aisteru on 2011-08-01
I am using 11.04 :(. 
   However, I am not sure at this point whether I need the firewire drivers, or something else, since I am using a cable that has a firewire plug on one end, & a USB plug on the other. My computer lacks an actual firewire port.

---

### Post by no2498 on 2011-08-01
i use a usb dv cam 
at every reboot i need to click on the back of the cam live as in computer mode
also take all the memory cards out

---

### Post by Aisteru on 2011-08-08
I tried rebooting with the camera playing, still no luck. Window$ does not seem to detect the camera either.

I am using a Canon ZR500 miniDV tape camera with a firewire output, in case it matters. My computer has only USB 2.0, HDMI, telephone, Ethernet, & VGA ports, & an SD card slot, no firewire. I am connecting the two through a cable that has a USB plug at one end, & a firewire plug at the other, just to be perfectly clear.

If I have to spend much more time figuring this out, I will just get a camera that uses SD cards.

---

### Post by no2498 on 2011-08-09
with the cam plugged in and turned on
open a terminal type dmesg click enter
after it stops type lsusb click enter
that should give a number and name for the cam

---

### Post by Aisteru on 2011-09-02
Sorry for the delay, I am terribly scatter-brained.

Here are the results:

Bus 008 Device 016: ID 1241:1122 Belkin Typhoon Stream Optical Mouse USB+PS/2
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

The entry for "Acer/Lenovo Webcam [CN0316]" is likely the built-in webcam, not the camcorder.

---

### Post by no2498 on 2011-09-02
did the dmesg  say anything abought the other cam

---

### Post by Aisteru on 2011-09-03
I do not think so. I have posted some of the output below, none of which looks like it relates to the camcorder as far as I can tell, but maybe you'll see something I missed.  I think it is all the events from when I brought it back from being suspended, so the camera should be in there.

[209460.776289] PM: Finishing wakeup.
[209460.776291] Restarting tasks ... done.
[209460.831637] video LNXVIDEO:00: Restoring backlight state
[209460.845292] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[209460.960075] usb 8-1: USB disconnect, address 16
[209461.095751] r8169 0000:01:00.0: eth0: link down
[209461.095987] ADDRCONF(NETDEV_UP): eth0: link is not ready
[209461.132748] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[209461.240034] usb 8-1: new low speed USB device using uhci_hcd and address 17
[209461.428767] input: HID 1241:1122 as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input26
[209461.428943] generic-usb 0003:1241:1122.0010: input,hidraw0: USB HID v1.00 Mouse [HID 1241:1122] on usb-0000:00:1d.2-1/input0
[209468.995951] wlan0: authenticate with 00:09:5b:c5:74:ca (try 1)
[209468.997963] wlan0: authenticated
[209468.997986] wlan0: associate with 00:09:5b:c5:74:ca (try 1)
[209469.000215] wlan0: RX AssocResp from 00:09:5b:c5:74:ca (capab=0x431 status=0 aid=1)
[209469.000218] wlan0: associated
[209469.000522] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[209479.936031] wlan0: no IPv6 routers present

---

