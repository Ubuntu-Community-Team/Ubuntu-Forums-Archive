---
title: "Connecting two linux computers using a USB bridging cable"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by supernater on 2012-11-09
I wanted to try transferring files between two linux computers using a USB bridging cable.  The first computer is my desktop running Ubuntu 12.04 and my second computer is a laptop running Lubuntu 12.10.  I'm using the Belkin F5U279 USB cable.  When I connect it to my computer I can see that an interface is created called usb0 on both computers.  I followed the instructions [posted on this site]("http://www.linux-usb.org/usbnet/").  I typed sudo ifconfig usb0 192.168.1.1 for the first computer and then I typed sudo ifconfig usb0 192.168.1.2 on the laptop.  However, I was never able to make a connection.  Both computers continually tried to make connections but always failed and generated a notification that said "Wired Network Disconnected".  Any ideas what I should try next?  Thanks.

As appreciative as I am of anyone that takes the time to respond to requests for help; I would ask that you keep replies to this thread on the topic of how to connect two computers using a USB bridging cable.  That is ALL I'm interested in.  I already know that the easiest way to transfer files between computers is to use a crossover cable or connect both computers to a router and use FTP/Samba or any other of the myriad of transfer options that I'm already well aware of.  I'm only trying to make a USB briding cable connection work between two linux computers.  Nothing more.

---

### Post by dgharmon on 2012-11-10
> **supernater said:**
> I typed sudo ifconfig usb0 192.168.1.1 for the first computer and then I typed sudo ifconfig usb0 192.168.1.2 on the laptop

This might help ..

"[Assigning IP addresses]("https://www.ridgerun.com/developer/wiki/index.php/How_to_use_USB_device_networking")"

---

### Post by SeijiSensei on 2012-11-10
Is this the only network connection either computer has?  If one of them is connected to another network, you may have a routing problem.  The networked computer might be sending packets intended for its USB peer out to its default gateway.  Try removing any other network connections if they exist (other than lo/127.0.0.1) and see if you can connect.

If that works, you can add a routing command on the networked computer like this:

```
sudo ip route add 192.168.1.2 dev usb0
```

That tells the computer to send packets for its peer out the USB device.

---

