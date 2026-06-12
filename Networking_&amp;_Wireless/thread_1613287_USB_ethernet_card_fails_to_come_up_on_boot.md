---
title: "USB ethernet card fails to come up on boot"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by Phiwum on 2010-11-04
Yesterday, I upgraded my server from Ubuntu 10.04 to 10.10.  Following this, I realized that my internal network was down.  While trying random things, I unplugged the USB ethernet card that I use for eth1 and replugged it.  Viola!  Everything was up and running.

This "fix" is, of course, a pain in the butt, since it involves getting on all fours and reaching into the morass of wires behind the machine.  There must be a better way.

I've re-tested the situation a couple of times now and every time I boot, the card appears in lsusb, but I do not have access to the local network unless I unplug and replug the card.  At that point, I get access immediately (without restarting init.d/networking or anything else).

Here's what lsusb shows regarding the card:

Bus 001 Device 007: ID 2001:3c05 D-Link Corp. [hex] DUB-E100 Fast Ethernet [asix]

(I've seen similar behavior with a USB soundcard.  Plug it in once, and nothing happens.  Unplug and plug it a second time and it works.)

Any help would be greatly appreciated.  Please let me know what diagnostic info I should include.  Here's the relevant bits from dmesg:
...
[   15.759235] eth1: register 'asix' at usb-0000:00:04.1-1, ASIX AX88772 USB 2.0 Ethernet, 00:80:c8:3b:70:33
[   15.759281] usbcore: registered new interface driver asix
...
[   15.802543] eth1: link down
[   15.804121] ADDRCONF(NETDEV_UP): eth1: link is not ready
...
[   18.810039] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   18.812140] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
...
[  147.019474] usb 1-1: USB disconnect, address 2
[  147.019830] eth1: unregister 'asix' usb-0000:00:04.1-1, ASIX AX88772 USB 2.0 Ethernet
[  153.290023] usb 1-1: new high speed USB device using ehci_hcd and address 7
[  153.454303] usb 1-1: configuration #1 chosen from 1 choice
[  154.272803] eth1: register 'asix' at usb-0000:00:04.1-1, ASIX AX88772 USB 2.0 Ethernet, 00:80:c8:3b:70:33
[  154.293085] eth1: link down
[  154.294753] ADDRCONF(NETDEV_UP): eth1: link is not ready
...
[  156.133553] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  156.135668] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1


The first entries are from the boot process (I think) and the later ones from when I unplugged and replugged the device.  (Aside: how do you read these timestamps?)

Much thanks.

---

### Post by chili555 on 2010-11-04
> The first entries are from the boot process (I think) and the later ones from when I unplugged and replugged the device.Correct.> Aside: how do you read these timestamps?
The timestamps are, as nearly as I can tell, seconds. That is, 15.75 seconds after you booted (the BIOS turned over control to GRUB, I believe), the operating system matched up the device and the driver and created an interface 'eth1.' 147.01 seconds after boot, it noticed the device disconnected, and so on.

Since this is a server, are you running a window manager or simply in terminal mode, a.k.a. runlevel 3?

Are you using Network Manager or relying on /etc/network/interfaces?

If Network Manager, is the tickbox checked off to connect automatically?

If /etc/network/interfaces, is the declaration 'auto eth1' present?

---

### Post by Phiwum on 2010-11-04
> **chili555 said:**
> 
Since this is a server, are you running a window manager or simply in terminal mode, a.k.a. runlevel 3?

Are you using Network Manager or relying on /etc/network/interfaces?

If Network Manager, is the tickbox checked off to connect automatically?

If /etc/network/interfaces, is the declaration 'auto eth1' present?

I am running a window manager.

Evidently, I'm using Network Manager, though I didn't realize it.  I've had problems with that application before.  

/etc/network/interfaces *does* have the right info for eth1 (including auto).  I'm not sure about the relationship between Network Manager and the interfaces file, but prior to the upgrade, everything was working peachy.

Thanks for the help (and also the primer on dmesg timestamps).

---

### Post by chili555 on 2010-11-04
Network Manager will manage all interfaces which are ***not*** listed in /etc/network/interfaces. As a first step, I'd comment out all the lines in /etc/network/interfaces except:```
auto lo
iface lo inet loopback
```Other lines should be commented out:```
#auto eth1
#iface eth1 inet dhcp
```Of course, the other approach is to remove Network Manager completely and properly populate *interfaces*. Typically, servers run without Network Manager and use a static IP address.

Which direction would you like to pursue?

---

### Post by Phiwum on 2010-11-04
> **Phiwum said:**
> 
/etc/network/interfaces *does* have the right info for eth1 (including auto).  I'm not sure about the relationship between Network Manager and the interfaces file, but prior to the upgrade, everything was working peachy.

I forgot this important fact:

When I reboot the machine, ifconfig reports that eth1 is present and has the right IP address.  The routing table looks good, too.  Nonetheless, I cannot reach other machines on the LAN.

(How could I forget that? Stupid, stupid!)

---

### Post by chili555 on 2010-11-04
Reach other machines as in ping? Browse shares? Or what? Does it reach the internet?

Did you set the IP address statically in *interfaces*? Did you also populate */etc/resolv.conf*?

---

### Post by Phiwum on 2010-11-04
> **chili555 said:**
> Reach other machines as in ping? Browse shares? Or what? Does it reach the internet?

Did you set the IP address statically in *interfaces*? Did you also populate */etc/resolv.conf*?

The interface eth1 is for my LAN.  I have no trouble with reaching the internet, which is done via eth0 (and which is an onboard ethernet card, not a USB card).

I cannot ping or reach other machines via eth1 in any way at all that I can see (whether by IP address or hostname), until I unplug and replug the USB card after each boot.  Nor can other machines reach the server (and hence they can't reach the internet).

*ifconfig* shows that the eth1 has the correct static IP address and *route* shows the correct routing table, even before I unplug and replug the USB card.  I also tried restarting udev to see if that would fix things without replugging the card, but it didn't.

The IP address is set statically in *interfaces*.  *resolv.conf* is also set up properly.  (In any case, resolv.conf shouldn't matter when I try to reach a machine via IP address, if I understand correctly.)

It seems to me that the various files (*interfaces*, *resolv.conf*, etc.) are unlikely to be the problem, since unplugging and replugging the network card fixes the issue without restarting */etc/init.d/networking*, but I could be mistaken.

Thanks for the help.

---

### Post by Phiwum on 2010-11-04
> **chili555 said:**
> Network Manager will manage all interfaces which are ***not*** listed in /etc/network/interfaces. As a first step, I'd comment out all the lines in /etc/network/interfaces except:```
auto lo
iface lo inet loopback
```Other lines should be commented out:```
#auto eth1
#iface eth1 inet dhcp
```Of course, the other approach is to remove Network Manager completely and properly populate *interfaces*. Typically, servers run without Network Manager and use a static IP address.

Which direction would you like to pursue?

I'm not really a fan of Network Manager.  I'm used to the old way of configuring interfaces.  I'll try disabling it.

Could you refresh my addled mind as to how that's done?  I know I've done it before, but I can't recall how.  Google shows pages for uninstalling it, but I'd prefer to disable without uninstalling (I think).

Thanks.

---

### Post by Phiwum on 2010-11-04
> **Phiwum said:**
> I'm not really a fan of Network Manager.  I'm used to the old way of configuring interfaces.  I'll try disabling it.


I found a method of disabling Network Manager using the following commands:

```
    * sudo mv /etc/init/network-manager.conf /etc/init/network-manager.conf-disabled
    * sudo mv /etc/xdg/autostart/nm-applet.desktop /etc/xdg/autostart/nm-applet.desktop.disabled

```

I rebooted the machine, confirmed that Network Manager was not running, confirmed that eth1 was up, with the proper static IP address and that the routing table was correct.  Nonetheless, I could not ping other machines on the local network.

I unplugged and replugged the USB card and everything immediately worked correctly.

So, whatever the problem is, it does not appear to be related to Network Manager.

---

### Post by chili555 on 2010-11-04
I'm stumped. We can try the old-fashioned stone ax approach. Edit /etc/rc.local and add three lines above exit 0:```
ifdown eth1
sleep 3
ifup eth1
```

---

### Post by Phiwum on 2010-11-04
> **chili555 said:**
> I'm stumped. We can try the old-fashioned stone ax approach. Edit /etc/rc.local and add three lines above exit 0:```
ifdown eth1
sleep 3
ifup eth1
```

Yeah, I'm stumped too.  The above Hail Mary code didn't do anything for me, I'm afraid.

Worse: about half an hour after a reboot, the LAN stopped working.  It began working again after I unplugged and replugged it.  

I don't think this is really a networking issue.  I think this is a USB issue.  Perhaps I should make another post in a different forum.

I suppose that there's a slight chance that this is a hardware issue, but I doubt it.  I had no troubles until after the upgrade to 10.10.

---

### Post by chili555 on 2010-11-04
> I had no troubles until after the upgrade to 10.10.Is the behavior the same if you revert to an older kernel at the GRUB prompt?

Please try the rc.local commands as:```
rmmod asix
sleep 3
modprobe asix
```I am about out of ammo.

---

### Post by Phiwum on 2010-11-04
> **chili555 said:**
> Is the behavior the same if you revert to an older kernel at the GRUB prompt?


Good question.  I'm not too familiar with GRUB.  How do I select an older kernel?  I don't see a GRUB menu at boot (the machine goes into the graphical screen early in the boot process).

> 
Please try the rc.local commands as:```
rmmod asix
sleep 3
modprobe asix
```I am about out of ammo.

That didn't work, but I accidentally found something of interest.  I changed to console 1 and saw a trillion messages saying:
```
[timestamp] eth1: asix_rx_fixup() Bad Header Length
[timestamp] eth1: asix_rx_fixup() Bad Header Length
[timestamp] eth1: asix_rx_fixup() Bad RX Length 40041

```

The messages stop when I disconnect and reconnect the USB ethernet dongle.

Google brings up a couple of posts with similar messages, but I don't see a fix yet.

---

### Post by Carl Hetherington on 2011-02-13
Hi,

For what it's worth, I am seeing what looks like exactly the same bug with a different ASIX AX88772-based card (the Edimax EU-4207).

I have tried the current bleeding-edge mainline kernel and it doesn't fix it.  I added a bug on kernel.org's bugzilla, #29082:

[https://bugzilla.kernel.org/show_bug.cgi?id=29082](https://bugzilla.kernel.org/show_bug.cgi?id=29082)

so I'll see if anything comes of that.

---

### Post by rachel.greenham on 2011-03-28
I'm getting these exact symptoms using the Apple USB Ethernet Adapter.

Curiously given your problems started on upgrade to Maverick, I had been having *no* problems with this on Maverick, on a different machine (Acer Revo), but encountered problems on trying to use it on a machine running Natty (Acer Aspire One).

However, this does at least strongly suggest a (rather longwinded) solution: Install Lucid from scratch. It's appropriate for a machine intended to be repurposed as a router anyway. I was just trying to get away without having to do it. :-}

---

### Post by ClayMitchell on 2011-04-02
I've got the same problem the Apple usb ethernet adapter on an Acer Revo. It worked just fine on a previous version (10.04 or 09.10 maybe?) but has serious issues with 10.10

Any help would be greatly appreciated.

---

### Post by ClayMitchell on 2011-04-03
Success!

I used the directions here:

[http://tutorialbin.com/tutorials/90473/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-1010-linux](http://tutorialbin.com/tutorials/90473/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-1010-linux)

EXCEPT I used the drivers here:

[http://www.asix.com.tw/FrootAttach/driver/AX88772B_772A_760_772_178_LINUX_Driver_v4.1.0_Source.tar.bz2](http://www.asix.com.tw/FrootAttach/driver/AX88772B_772A_760_772_178_LINUX_Driver_v4.1.0_Source.tar.bz2)

(That's because the drivers pulled in the instructions broke it completely for me)

This was on an Acer Revo 1600 using an Apple USB Network Adapter running 10.10

It works on boot, without having to unplug and plug back in.

---

