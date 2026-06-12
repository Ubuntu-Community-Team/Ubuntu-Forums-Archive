---
title: "Problem with Intel WiFi 5100 Link in Ubuntu 10.04"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by squall1986 on 2010-10-11
My problem is a bit of a strange one. I'll start by giving my specs:

Machine: Acer Aspire 8930g
Wireless: Intel Corporation Wireless WiFi Link 5100
Interface: wlan0
No detected modules
'dmesg | grep wlan0' gives about 20 lines of output, not sure how much is relevant to this
network configuration:
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:90:ff:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:d6000000-d6001fff

wlan0     No scan results
Ubuntu 10.04.1 LTS
2.6.32-25-generic i686

Now the problem is that I can connect to my home D-Link router just fine and browse the Internet for a few minutes (about 10 or so). But then it just craps out. It thinks there is still a connection, but no websites resolve and I can't even access my router's admin page at 192.168.0.1. All my other computers on the network running Win7 are still connected and I don't have this problem if I boot into Win7 on this laptop having the issue, either. Also, if I take my laptop to campus I don't have a problem with their network.

Basically I'm wondering how I could just uninstall my current driver and reinstall the original. I think I may have installed a custom driver that supported promiscuity and some other stuff over the summer. At the time I was researching packet injection and wireless security and junk, but I don't need that any more.

Any help would be appreciated.

---

### Post by scokem on 2010-10-11
I have the same chip in my my nettop and found the same issue. After some searches, I found the following ([taken from this site]("http://hardc0l2e.wordpress.com/2010/05/19/intel-5100-agn-on-ubuntu-10-04/")):

```
1. Create a new modprobe configuration, let’s call it options.conf

    sudo vi /etc/modprobe.d/options.conf

2. Add the following code:

    options iwlagn 11n_disable=1 11n_disable50=1

3. Reboot the system and check if it fixes your Intel 5100 AGN wireless device’s problem.

4. Done
```It worked for me, but the speed sometimes drops down to 1MBps for a while which can get annoying. The good news though is that when I've been testing with 10.10, it works flawlessly out of the box so you may want to give that a whirl.

---

### Post by Mobidoy on 2010-10-11
I have the same chip but my problem is different. I have no problem connecting to my network if it is A, B or G, If I set it to N only, the chip see it but wont connect to it. Anyone know what I could try ?

---

### Post by CrIlat on 2010-10-11
> **Mobidoy said:**
> I have the same chip but my problem is different. I have no problem connecting to my network if it is A, B or G, If I set it to N only, the chip see it but wont connect to it. Anyone know what I could try ?

I same equal problem, with intel wifi link 5100 AGN.. waiting solution....

---

### Post by squall1986 on 2010-10-16
Well I upgraded to Ubuntu 10.10 and the problem stopped. My router is still set up to use mixed 802.11 n, g and b and my wireless card doesn't have a problem.

I suspect that the upgrade simply just fixed the customizations I had done over the summer when I was messing with my wireless drivers. Either way, it works fine now.

---

