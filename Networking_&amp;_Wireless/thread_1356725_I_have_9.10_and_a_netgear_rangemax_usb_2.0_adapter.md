---
title: "I have 9.10 and a netgear rangemax usb 2.0 adapter WPN111 how do i get it to work"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by jhetty on 2009-12-16
I got a RangeMax wireless adaptor USB 2.0 WPN111 and do not have any idea how to use it I'm trying to use it on a desktop computer please help. Os is xubuntu 9.10 This is for another computer in my house the router is a netgear wireless G WGR614 if that helps.

---

### Post by ThreeColoursBlue on 2010-07-08
I just got my WPN111 working on [32-bit] Ubuntu 9.10, following various posts, maybe this will help you:

Install ndisgtk in the Ubuntu Software Center

Copy the contents of the ndis5 directory on the CD supplied with the WPN111 to somewhere on your hard disk, I used /etc/WPN111-ndis-driver-stuff

Go to: System > Administration > Windows Wireless Drivers > Install New Driver, and browse to the directory you setup in the previous step, select the INF file there.

Go to: System > Preferences > Network Connections > Wireless > Add, and enter the details to connect to your WiFi network

You're done. There's one gotcha though: This will appear to fail horribly when you next reboot the machine. This seems to be because the WPN111 is left in a strange state on shutdown - fix this by unplugging the device and plugging it back in before you turn the machine back on - or turn off power to the machine at the wall and wait a few seconds before restarting it (even though your PC may be 'off', the USB ports may still be powered).

Finally a few useful commands & further notes,

lsusb to list your usb devices, the WPN111 should show up there
iwconfig should include the adapter as wlanX (X=2 for me)
ifconfig should show the network settings in use by wlanX above

Hope that helps.

cheers,

Andrew.

---

### Post by itsjareds on 2010-07-13
Thanks for the post, seems to be the same thought process I had :)

Curious, though, do you have connection reliability problems with your network? I could not keep a solid connection, as it would go out very randomly.

---

