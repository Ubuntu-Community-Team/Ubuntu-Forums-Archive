---
title: "Wireless doesn't work after trying out windows drivers"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by blwizard on 2009-10-28
Hi guys. Wireless on my Samsung N110 netbook worked well with the default driver. The other day I was interested to see how the windows driver would go, so I installed ndisgtk and installed the windows wireless driver, but it didn't work. So I uninstalled ndisgtk, and wireless has been down since then. No matter what I try it doesn't work. What should I do to bring wireless back up again? Thanks!

---

### Post by bgeraghty on 2009-10-28
I've never really seen an increase in performance when using ndiswrapper to use a windows driver file on a Linux machine. In my cases, it seemed to reduced speed or eliminate certain capabilities of the card.  I, since then, always stick with the Linux device drivers if they're available for my hardware.

It doesn't sound like too much could have gone wrong here, however.

Assuming you've got ndisgtk purged and uninstalled, what are the outputs of your ifconfig and iwconfig?  Is the device still recognized?  

[http://ubuntuforums.org/showthread.php?t=676384](http://ubuntuforums.org/showthread.php?t=676384)
[http://ubuntuforums.org/showthread.php?t=842586](http://ubuntuforums.org/showthread.php?t=842586)

These threads might aim you in the right direction.

---

### Post by t0mppa on 2009-10-28
> **blwizard said:**
> Hi guys. Wireless on my Samsung N110 netbook worked well with the default driver. The other day I was interested to see how the windows driver would go, so I installed ndisgtk and installed the windows wireless driver, but it didn't work. So I uninstalled ndisgtk, and wireless has been down since then. No matter what I try it doesn't work. What should I do to bring wireless back up again? Thanks!

Why don't you open up a terminal and run **lshw -C network** to see what chip you have and if it's associated with any drivers now.

I'm guessing that you probably unloaded and blacklisted (set it not to load by default during boot up) your original driver, so you should be able to get back to square one by reversing said changes. Blacklist files are located in */etc/modprobe.d/*, so unless you track down your changes (for instance by checking which was the last file edited), you'll just have to go through all of them, although the *blacklist.conf* should be the first place to look, as that's the default place to put these changes.

The only slight issue here is that to find what you're looking for, you'll need to know what the name of the driver you were originally using is.

---

### Post by blwizard on 2009-10-28
> **bgeraghty said:**
> I've never really seen an increase in performance when using ndiswrapper to use a windows driver file on a Linux machine. In my cases, it seemed to reduced speed or eliminate certain capabilities of the card.  I, since then, always stick with the Linux device drivers if they're available for my hardware.

It doesn't sound like too much could have gone wrong here, however.

Assuming you've got ndisgtk purged and uninstalled, what are the outputs of your ifconfig and iwconfig?  Is the device still recognized?  

[http://ubuntuforums.org/showthread.php?t=676384](http://ubuntuforums.org/showthread.php?t=676384)
[http://ubuntuforums.org/showthread.php?t=842586](http://ubuntuforums.org/showthread.php?t=842586)

These threads might aim you in the right direction.

Yes, ndisgtk and ndiswapper have been purged.
Here is the output you asked for:
```

brian@brian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```
By the way, my wireless Lan interface used to be wlan0, but it doesn't appear anymore.

```

brian@brian-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:77:fc:29:ee  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:77ff:fefc:29ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:719416 (719.4 KB)  TX bytes:159219 (159.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```



[Quote=t0mppa]
Why don't you open up a terminal and run lshw -C network to see what chip you have and if it's associated with any drivers now.

I'm guessing that you probably unloaded and blacklisted (set it not to load by default during boot up) your original driver, so you should be able to get back to square one by reversing said changes. Blacklist files are located in /etc/modprobe.d/, so unless you track down your changes (for instance by checking which was the last file edited), you'll just have to go through all of them, although the blacklist.conf should be the first place to look, as that's the default place to put these changes.

The only slight issue here is that to find what you're looking for, you'll need to know what the name of the driver you were originally using is.[/quote]

The wireless still doesn't work.
Here is the output of lshw -C network:
```

brian@brian-laptop:/etc/modprobe.d$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:fc:29:ee
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.10 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:61:9c:4d:e7:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

I played around with the blacklist thing. Here is the content of /etc/modprobe.d/blacklist:
```

brian@brian-laptop:/etc/modprobe.d$ more blacklist
blacklist ath_hal
blacklist ath_pci

```
I thought this is blacklisting my ath5k driver, so I tried removing these two lines but after rebooting, wireless still doesn't work.

and here is the blacklist for madwifi driver if i'm not mistaken:
```

brian@brian-laptop:/etc/modprobe.d$ more blacklist-ath_pci.conf 
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```
I don't think I was using the madwifi driver cuz it was disabled all the time, so this file should be fine, right?

What should I do next?

---

### Post by blwizard on 2009-10-28
By the way, here is the content of blacklist.conf:
```

brian@brian-laptop:/etc/modprobe.d$ cat blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by bkratz on 2009-10-28
Look at this thread especially post 9 and later.  Apparently the driver should have been ath5k, it looks like this person may have done the same as you.

[http://ubuntuforums.org/showthread.php?t=1191178&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=1191178&highlight=AR242x)

---

### Post by blwizard on 2009-10-28
> **bkratz said:**
> Look at this thread especially post 9 and later.  Apparently the driver should have been ath5k, it looks like this person may have done the same as you.

[http://ubuntuforums.org/showthread.php?t=1191178&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=1191178&highlight=AR242x)

His ath5k driver at least works but with some problems. I can't get the driver ath5k up and running. See my output of ifconfig and iwconfig in my previous posts. I think it's probably the blacklist thing, but I tried comment out the thing in /etc/modprobe.d/blacklist and it didn't work.

---

### Post by blwizard on 2009-10-28
Wireless is back up again! Thanks people for all the information you provided. I finally found out the reason why it didn't work. Although I uninstalled ndiswapper, there is still a file called ndiswrapper in /etc/modprobe.d/. I removed that file, as well as /etc/modprobe.d/blacklist which contains two lines:
```
blacklist ath_hal
blacklist ath_pci
```
Before restarting the system, I made sure there is the line:
```
blacklist ath_pci
```
in blacklist-ath_pci.conf.

After rebooting, everything works as before. Cheers!

---

