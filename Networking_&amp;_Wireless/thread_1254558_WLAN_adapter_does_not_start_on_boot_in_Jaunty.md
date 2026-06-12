---
title: "WLAN adapter does not start on boot in Jaunty"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by jwrede on 2009-08-31
I recently upgraded my wife's PC from Hardy to Jaunty (via Intrepid) and her wireless adapter no longer starts and connects on boot-up (works if I start it manually though).  The adapter is a D-Link DWA-130 Wireless N USB.  And here are the details:

As with Hardy, I had to use the Ralink rt2870 drivers (downloaded the latest v2.2.0.0) and add my USB device ID to the usb_main_dev.c file
```
{USB_DEVICE(0x07D1,0x3C13)}, /* D-Link */
```

I first did a "sudo modprobe -r rt2870sta" then renamed the 2870 driver in /lib/modules/2.6.28-15-generic/kernel/drivers/staging/rt2870 to "rt2870sta.ko.disabled".

I ran the "sudo make && make install", received no errors.  I then ran a "sudo modprobe rt2870sta" and again received no errors.

Now, when I boot the machine the light on the adapter comes on and stays solid, but Network Manager doesn't see it.  If I run a "sudo ifconfig" I get:

```
eth0      Link encap:Ethernet  HWaddr 00:1d:92:2e:72:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6664 (6.6 KB)  TX bytes:6664 (6.6 KB)
```

But running "iwconfig" yields:

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA 
```

I can get everything working if I run "sudo ifconfig ra0 up" followed by a "sudo killall NetworkManager" and "sudo NetworkManager"

What am I missing?  I tried to add it to my /etc/network/interfaces, but wound up with NetworkManager telling me that the device was not managed, so I dismissed that approach.

Thanks in advance!
Johann

---

