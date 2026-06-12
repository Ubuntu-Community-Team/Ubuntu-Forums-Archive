---
title: "Networking nightmare in QEMU."
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by yevgeni on 2008-12-10
Hello all!

I'm running Ubuntu 8.10 32 bit.

I was wondering if anyone would be able to shed some light on this problem. I have QEMU and KQEMU installed and working. User mode networking works fine, but I need tap mode for its obvious benefits. I have everything set up properly because I had tap mode working previously. I restarted my computer and it doesn't work anymore. Here are the settings in my interfaces file:

```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.2.20
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255
	gateway 192.168.2.1
	dns-nameservers 192.168.2.1
	dns-search mshome.net


```

This works fine for my internet connectivity. Here is the command I use to invoke QEMU:

```
qemu -hda hda.img -m 512 -net nic -net tap,ifname=tap0 -kernel-kqemu -localtime
```

I have done "modprobe tun". My qemu-ifup script reads:
```
#!/bin/sh
sudo -p "Password for $0:" /sbin/ifconfig $1 192.168.0.1

```

My guest OS's networking is definitely set up properly.

Also, I've tried about three or four variations of tunctl.

Why did this only work once using this setup, and why doesn't it work now? I've scoured every howto I could find and even searched the forum. Any help would be greatly appreciated.

Edit:
According to gnome's network monitor, the VM and host machine are exchanging packets, but pings from both sides aren't going through.

---

