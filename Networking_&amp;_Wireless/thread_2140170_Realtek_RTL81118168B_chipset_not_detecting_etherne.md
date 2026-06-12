---
title: "Realtek RTL8111/8168B chipset not detecting ethernet on Ubuntu 12.04 LTS"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by GeorgeLSpencer on 2013-04-28
Hi,
I have been having hassles with an Ethernet connection which only rarely works. I posted previously on this topic, but the Ethernet keeps showing in dmesg as "r8169 eth0: link down". I did some checking, and it appears that this problem has been reported for many years with his chipset.
```
george@spencer-i7:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:75:e4:e5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.035.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 ioport:ce00(size=256) memory:fbeff000-fbefffff memory:fbee0000-fbeeffff memory:fbe00000-fbe0ffff

```
A number of users found that this problem could be remedied by using the r8168 driver. This is available from Realtek, so I downloaded the recommended driver and installed it. Unfortunately, this does not appear to have fixed the problem; e.g.
```
george@spencer-i7:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             unavailable
  Default:           no
  HW Address:        00:24:1D:75:E4:E5

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

What should I do next?  

Second question: what is the best way to download ethtool (using Windows) and install it in Ubuntu?

Thanks,
George

---

### Post by Hadaka on 2013-04-28
[http://linux.softpedia.com/progDownload/ethtool-Download-14252.html](http://linux.softpedia.com/progDownload/ethtool-Download-14252.html)
see it this works for you.
and did you try..
code:
sudo gedit /etc/modprobe.d/blacklist.conf
#add this line at the bottom of the file
blacklist r8169
#close and save gedit
sudo modprobe -rfv r8169
sudo modprobe r8168

---

### Post by GeorgeLSpencer on 2013-04-28
Hi Hadaka,

Thanks for the info on ethtool, I downloaded and installed it without any problems. I then tried turning autoneg off, as has been suggested by many of the old forums, but this was without success either. I tried the blacklist suggestions, but the correct module was being loaded anyway, going by the dmesg entries.

What gets me is the fact that networkManager considers the link to be disconnected / unavailable. I wonder why the carrier is "off". Any further ideas?

---

### Post by Hadaka on 2013-04-29
Hi, carrier off is usually an indication that the cable
is unplugged,damaged,open wire...it's not detecting
a carrier signal from the router. look closely for missing
damaged,bent,or shorted connections,and maybe even
try a different cable if you have one laying around. It may 
also be related to the fact you are running 1/2 duplex.
*and..turn autoneg back on...anything changes you make
that doesnt fix the problem,return them to the state you found
them in so as not to add to the problem.

---

### Post by varunendra on 2013-04-29
Just a heads up - the problem with the native r8169 driver has become so rare since 12.04 that most of us consider it as 'gone'. Those few that still arise have been, as far as I have seen, caused by other factors, not the driver itself.

In fact, one of our dedicated members - Brian - with this card reported recently that he got better result this time by 'unblacklisting' the native driver, and using it instead of the proprietary r8168 one : [http://ubuntuforums.org/showthread.php?t=1865436&p=12596089#post12596089](http://ubuntuforums.org/showthread.php?t=1865436&p=12596089#post12596089)
..and mind you, he is not the first one to report that r8169 is working now.

So my approach would be to check the other things first, driver last. Especially when it has already shown no improvement with the changed driver.

Over to Hadaka again.. :)

**PS:**
With "link=no" in lshw, or carrier=off in nm-tool, I believe Hadaka is on right track suggesting a replacement of the cable.

---

