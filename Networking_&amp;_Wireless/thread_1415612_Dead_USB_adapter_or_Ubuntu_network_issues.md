---
title: "Dead USB adapter or Ubuntu network issues?"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by hungsolo on 2010-02-25
I'm fairly new to Linux/Ubuntu so please excuse my ignorance.

I just installed Ubuntu 9.10 about a week ago.  I plugged in my D-Link WUA-1340 USB adapter and could connect to my router right away.  After updating however, my connection would start to drop intermittently.  Usually, it would reconnect soon after, but after awhile, it would ask for my password again and still not reconnect.  I would have to reboot my computer.  I read that installing WICD would help solve the issue, but I couldn't connect at all afterwards.  Frustrated, I reinstalled Ubuntu.  However, the adapter seemed to work for about 1 second (found my router, but wouldn't/couldn't connect or see the connection afterwards).  Most of the time, the light remains off on the adapter.  When it does light up, it's solid (doesn't blink) and still doesn't show any wireless networks.  When I type the command lsusb, I get the following:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have read that ndiswrapper may be able to help, but the rt73 driver needs to be blacklisted.  I do not know exactly what this does or how to reverse the action if I need to, so I haven't done this (blacklisted rt73).  er Ubuntu, the adapter should work "out of the box" with the rt73 driver; no need to blacklist.  I have installed ndiswrapper anyway and get the following when typing ndiswrapper -l:

dr71wu : driver installed

Somewhere I have read that there needs to be device info or such after this or the device driver isn't installed correctly.  Not sure how valid that is though. 

I have also read that the latest kernel(2.6.31-19) might be the culprit.  There seems to be many issues involved with this version.

So, in summary, I do not know if I have a dead adapter, a kernel issue, or a driver issue.  Any and all help is greatly appreciated.

By the way, my wired connection works fine.  Don't know if that's of any use.

---

### Post by chili555 on 2010-02-25
In my opinion, your device is not dead. It's dying and will soon be dead. First, if it isn't recognized at all in *lsusb*, that's a symptom. Next, when the LED doesn't even glow or blink, that's a symptom and finally, ndiswrapper should report:> dr71wu : driver installed; [COLOR="Red"]hardware present[/COLOR]You might get some additional clues by opening a terminal and doing:```
sudo tail -f /var/log/messages
```Now remove and reinsert the device and see if you get any recognition. Does it matter which USB slot you use?

If it works for a few moments and then doesn't, it may be a heat issue. It is conceivable that some tiny resistor or some such is not operating correctly, gets very hot and the resistance goes super-nova and the device quits.

With respect to the driver and the kernel; that is, the software, the device should be recognized in any event, even if the software couldn't effectively drive the device; that is, connect, stay connected, handle encryption, etc.

---

### Post by hungsolo on 2010-02-25
Thanks for the input.  I tried the code you had and this is the output:

> Feb 25 07:06:19 OG kernel: [49617.496243] usb 2-2: not running at top speed; connect to a high speed hub
Feb 25 07:06:19 OG kernel: [49617.613561] usb 2-2: configuration #1 chosen from 1 choice
Feb 25 07:06:20 OG kernel: [49617.904098] usb 2-2: reset full speed USB device using ohci_hcd and address 35
Feb 25 07:06:22 OG kernel: [49620.422062] wlan0: ethernet device 00:22:b0:6b:0f:a2 using NDIS driver: dr71wu, version: 0x0, NDIS version: 0x500, vendor: 'D-Link USB Wireless LAN Card', 07D1:3C04.F.conf
Feb 25 07:06:22 OG kernel: [49620.422098] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (00010003)
Feb 25 07:06:22 OG kernel: [49620.422106] wlan0: encryption modes supported: none
Feb 25 07:06:22 OG kernel: [49620.508023] ndiswrapper: changing interface name from 'wlan0' to 'wlan4'
Feb 25 07:06:22 OG kernel: [49620.508023] udev: renamed network interface wlan0 to wlan4
Feb 25 07:06:31 OG kernel: [49629.003000] usb 2-2: USB disconnect, address 35
Feb 25 07:06:32 OG kernel: [49629.913407] ndiswrapper: device wlan4 removed

Not sure why the interface was renamed or why no encryption modes are supported.  After removing and reinserting the adapter, nothing happened; still unlit.  It doesn't matter which USB port I use.

---

