---
title: "Ubuntu Server VirtualBox MAC Addresses"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by Jax Green on 2010-07-28
Hello,

First let me explain the scenario...

First, I created a VirtualBox (v3.2.2) virtual machine with following specs:

- Host OS: Windows 7
- Guest OS: Ubuntu 10.04 Server (32 bit)
- RAM: 256 MB, Video Memory: 12 MB, 2D, 3D Acc. is Disabled
- Hard Drive: SATA Controller, SATA Port 0, ulinux-server.vdi (Normal, 7.00 GB)
- Network: (two adapters)
  Intel PRO/1000 MT Desktop (NAT)
  Intel PRO/1000 MT Desktop (Host-only adapter, 'VirtualBox Host-Only Ethernet Adapter')
- Audio, USB, Serial Ports are all disabled.

At this point everything worked just perfectly. Ubuntu Server, detected the two network interfaces correctly.

After this, I cloned the virtual hard drive (VDI file) with the command:
```
VBoxManage clonehd <source vdi> <destination vdi>
```and copied it to another computer, and imported it into VirtualBox there.

Now when I ran the Ubuntu server in VirtualBox on the other computer, it DID NOT detect the network interfaces.

The "ifconfig" command showed only the loopback (lo) interface.
The "ifconfig -a" command showed the other two interfaces (eth0, eth1) but they were down.

I tried following commands but nothing worked:
```

sudo ifconfig eth0 up
sudo /etc/init.d/networking restart

```THEN, in my VirtualBox settings menu, I changed the MAC Addresses of the adapters to the exect same ones for the original virtual machine (the one whose virtual hard disk was cloned) . After this, when I ran the virtual machine, Ubuntu detected the two interfaces correctly.

Now, My questions are:

1) Why did Ubuntu Server not detect the interfaces with new MAC Addresses that VirtualBox had assigned automatically?

2) Why Ubuntu could detect the interfaces when I changed the MAC addresses to those of the original virtual machine.

3) What (if at all) is the command to make Ubuntu recognize new MAC addresses.

Even in my original virtual machine, if I change the MAC addresses of the adapters (by pressing the refresh button next to MAC address input box in settings panel of VirtualBox) the same problem arises -- Ubuntu does not detect the network interfaces. When I reset the MAC addresses to previous values, interfaces are detected again.

P.S. Please respond to this rather awkward thread :)

---

### Post by footle on 2011-02-15
I realise it's been a long time since this was posted, but I experienced the same problem and this was among the first results on a Google search for related terms. 

I finally figured out what the problem was and how to solve it, so I signed up to post it here for anyone else trying to figure this out. 

The problem is that the mac address of the NIC is stored in /etc/udev/rules.d/70-persistent-net.rules

Just remove that file, reboot (the file will be regenerated on startup) and all should be well :-)

---

### Post by zerosource on 2011-07-08
Thanks footle.

However, eth0 doesn't get any IP address.

---

### Post by mneisler on 2012-08-08
in centos you have to edit the mac address in /etc/sysconfig/network-scripts/ifcfg-eth0 as well

---

### Post by mneisler on 2012-08-08
virtual box seems to randomly change the virtual network adapters mac address.

---

