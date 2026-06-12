---
title: "Ubuntu 9.10 and OpenDNS - connected to internet but NM not working"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by psrivats on 2010-02-28
Folks,

I was seeing a lot delay with opening webpages in Karmic 9.10 recently. First, I tried turning off the IPV6 in grub by editing the GRUB_CMDLINE_LINUX_DEFAULT in /etc/grub/default. That did not work - ie IPV6 was turned off, but I saw no change in webpage loading.

Next, I followed the instructions here to setup OpenDNS:
[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

It worked like a charm and my pages load very fast now. However, I have a strange issue. When I made the changes described above using the 'Edit Connections' in NetworkManager Applet, things were fine - NM applet still saw my eth0. However, after a reboot, I was not able to connect to the internet. I had the following errors when I tried ifdown/ifup:

```

$sudo ifdown eth0 && sudo ifup eth0 

ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
```

Then I went and checked my /etc/network/interfaces file:

```

$ cat /etc/network/interfaces

auto lo
iface lo inet loopback
```

Knowing something was up, I added the following lines to /etc/network/interfaces:

```
iface eth0 inet dhcp
auto eth0

```

With this, sudo ifdown eth0 && sudo ifup eth0 worked and I was able to connect to the internet.

However, NM applet still said 'eth0 not managed' and there was a red 'x' mark (ie the disconnected icon). So I searched a bit and found this:
[http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

I checked my /etc/NetworkManager/nm-system-settings.conf file and saw :

```

[main]
plugins=ifupdown,keyfile

no-auto-default=00:15:58:2f:c0:df,

[ifupdown]
managed=false

```

I changed the last line to read managed=true and now NM applet does not show the 'eth0 not managed' error again. However, it still shows the disconnected icon. If I try and connect via the 'Auth eth0' like before, it fails and I am not connected to the internet anymore. I have to do a sudo ifdown/ifup to get connected again.

edit: Wireless works without any issues, btw.

What did I do wrong? Does anyone know the fix for this?

---

### Post by gfuggs on 2010-02-28
Anything you add to /etc/network/interfaces won't be managed by NM.

If you want to use it to manage eth0, you should only have:
auto lo	
iface lo inet loopback

I think if you change that, and do a "sudo ifconfig eth0 down" and a "sudo service network-manager restart" it should pick it up.  Of course, that's completely ignoring whatever changed when you installed opendns.

---

### Post by psrivats on 2010-02-28
> **gfuggs said:**
> 
I think if you change that, and do a "sudo ifconfig eth0 down" and a "sudo service network-manager restart" it should pick it up.  Of course, that's completely ignoring whatever changed when you installed opendns.

This works, sort of ... I have ifupdown (eth0) in network manager now.

---

