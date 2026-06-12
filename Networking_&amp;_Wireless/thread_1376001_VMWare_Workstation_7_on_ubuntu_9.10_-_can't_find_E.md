---
title: "VMWare Workstation 7 on ubuntu 9.10 - can't find Ethernet device"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by elenius on 2010-01-08
I just upgraded to VMWare workstation 7. I was previously running v.6, and an older linux version, and everything was working fine. I moved over the same VM files to the new computer, and it doesn't find the ethernet connection.

When I start up the virtual machine, I get an error message:

Could not connect Ethernet0 to virtual network "/dev/vmnet8". More information can be found in the vmware.log file.

There log file doesn't say much more:

Jan 07 17:31:36.928: vcpu-0| VNET: MACVNetPortOpenDevice: Ethernet0: can't open vmnet device (No such device or address)
Jan 07 17:31:36.928: vcpu-0| VNET: MACVNetPort_Connect: Ethernet0: can't open data fd
Jan 07 17:31:36.928: vcpu-0| Msg_Post: Warning
Jan 07 17:31:36.928: vcpu-0| [msg.vnet.connectvnet] Could not connect Ethernet0 to virtual network "/dev/vmnet8". More information can be found in the vmware.log file.
Jan 07 17:31:36.928: vcpu-0| [msg.device.startdisconnected] Virtual device Ethernet0 will start disconnected.

Once xp has booted, I get the "new hardware" wizard, saying that it found an ethernet adapter. However, it can't find any driver for it. I think this dialog started appearing after I added a new virtual network entry using the "Virtual Network Editor". Originally I didn't even have a /dev/vmnet8 file. Now I do.

Any ideas?

---

### Post by darco on 2010-01-08
Try using Bridge networking instead of NAT....

darco

---

### Post by elenius on 2010-01-08
I get the same error message, except it says vmnet0 instead of vmnet8...

---

### Post by darco on 2010-01-08
I cant fire up my VMware at the moment but check this link and hopefully it will help you

[http://blog-rat.blogspot.com/2009/05/bridged-vs-host-only-vs-nat.html](http://blog-rat.blogspot.com/2009/05/bridged-vs-host-only-vs-nat.html)


darco

---

### Post by elenius on 2010-01-08
Fixed it: I had to check the "Use local DHCP service" option in the Virtual Network Editor. A rather poorly named option. Sounds like you want to use a pre-existing DHCP service, which is the opposite of what I needed to do. The option starts and runs a special vmware dhcp service.

---

### Post by lambart on 2010-02-18
I had the same problem with VMWare Player 3.0, and was having no luck getting thing straightened out, until I saw that someone fixed their problems on OSX by rebooting.

I tried to just restart networking (on Ubuntu 9.10) but no luck. However, rebooting the box did fix the problem.

---

### Post by Not_Sure on 2010-10-12
I know this is dated, but I thought I would add an easy fix I just applied for this issue.

I recently replaced my DSL Modem, and I left the default IP Address range in tact.  I also had to reinstall my VMWare Workstation when I was not on my network (using Linux host on a laptop).  

I then came home and started running into this problem with my NAT connection, but not Bridged VMWare Networks.  I went into the Virtual Network Editor, and noticed the NAT (vmnet8) was using 192.168.1.0 - tada.

Changed it to auto-discover an unused network and life is good again.

---

