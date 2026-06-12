---
title: "Undo wireless networking &quot;fix&quot; after kernel upgrade"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by Telescope_Nerd on 2010-02-10
Hi all

I recently upgraded the kernel in 9.10 to fix a problem of no sound on my laptop but this killed wireless :( However I could still boot into the previous kernel to use wireless (albeit without sound).

I found a fix for this problem on the forums: 

[http://ubuntuforums.org/showthread.php?t=1375942&page=5]("http://ubuntuforums.org/showthread.php?t=1375942&page=5")

but It didn't work so well in my case.

Specifically after executing the command 

```
sudo rmmod -f dell_laptop
```

I lost ALL wireless and the output of 
```
iwconfig
```
now shows no wireless card (there was some output before.)

If anyone knows how to undo the rmmod dell_laptop command or has some insight into what I might be able to do please let me know!

Thanks.

---

### Post by kiranmurari on 2010-02-10
Hi,

   You can reload the driver using modprobe.
```
$ sudo modprobe dell_laptop
```Let me know if this fixes the issue.

---

### Post by Telescope_Nerd on 2010-02-10
Thanks for the reply, I tried that already but no joy. If that does undo the effects of the previous command then, I guess I might be miss-attributing it as the source of my problem...?

---

### Post by kiranmurari on 2010-02-10
Hi,

Can you post the output of following commands.
```
 $ dmesg
$ lshw -c network
$ iwconfig
$ uname -a
```Also logs specific to wireless from /var/log/messages might also be helpful for the purpose of debugging.

---

### Post by chili555 on 2010-02-10
A rmmod command will usually be completely undone with:```
sudo modprobe dell-laptop
```As well, these fixes are temporary; that is, they won't survive a reboot. Find out with:```
lsmod | grep dell
```

In order to be permanent, they must be placed in some /etc file or another. The most usual candidate is */etc/modprobe.d/blacklist.conf*. Another is */etc/rc.local*. If either of those has been amended to stop dell-laptop, simply remove it.

---

### Post by Telescope_Nerd on 2010-02-10
Thanks for the help guys I think were getting somewhere. Okay so I guess we can rule out the rmmod command as the source of the problem as. the output of lsmod is 

```
simon@ubuntu:~$ lsmod | grep dell
dell_wmi                3216  0 
dell_laptop             9692  0 
dcdbas                  9136  1 dell_laptop
```

which shows dell_laptop there.

The only other thing I remember changing is adding the package "linux-backports-modules-karmic-generic" although I removed this after things went wrong and nothing improved. I think the best thing to do is to push forward and just try and get wireless working in the latest kernel if I can.

The requested outputs are here

```
simon@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux
```

```
simon@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

My wireless card used to show up here under "eth2"

But the most interesting output comes from lshw -c network. This shows my wireless card with the tag "UNCLAIMED"

```
simon@ubuntu:~$ sudo lshw -c network
[sudo] password for simon: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:20:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:ab:3e:74
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:37 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)
``` 

so is there any way I can "claim" it??!

---

### Post by superprash2003 on 2010-02-10
have you tried system->admin->hardware drivers?

---

### Post by Telescope_Nerd on 2010-02-10
@superprash
Yes I have installed the broadcom propriatery driver. It is listed as "active but not in use"

---

### Post by bkratz on 2010-02-10
Hopefully you can find something useful in this thread

[http://ubuntuforums.org/showthread.php?t=1402769](http://ubuntuforums.org/showthread.php?t=1402769)

---

### Post by superprash2003 on 2010-02-17
you might need to connect your computer to a wired internet connection to enable hardware drivers

---

