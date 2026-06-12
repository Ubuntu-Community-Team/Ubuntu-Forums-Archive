---
title: "wireless stopped showing in nm-applet"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by korihor on 2008-12-13
I have been using wireless successfully on my Samsung NC10 for some time now after installing the ath5k driver. For the second time, wireless has disappeared from nm-applet, but this time it has not come back on its own.

I've researched this problem all I could and the only concrete thing I've found is that /etc/network/interfaces should not have your device info in it (or alternatively, should only have the first two lines, depending on who you ask):

My /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

The ath5k driver is installed and lsmod lists it, and lshw associates it with the card normally.

This I think might be the problem, the "DISABLED" bit in lshw:
```
        *-network DISABLED
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:21:63:3a:75:fc
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
```

Yes, NetworkManager is running.

If you want it, here's my iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

***************
That's all the info I know. Any ideas?
***************

---

### Post by iponeverything on 2008-12-13
Maybe it's the same issue? :

[http://ubuntuforums.org/showthread.php?t=988564](http://ubuntuforums.org/showthread.php?t=988564)

---

### Post by korihor on 2008-12-13
Okay weird thing happened.
Ubuntu is my only OS so I didn't think this would help, but I checked it out anyway. In BIOS "always on" was already selected. I then reboot WITHOUT saving changes (not that I made any). And sure enough, wireless worked.

That despite having restarted maybe 10 times today trying to get it working, and restarting networking at the command line about 20 times.
Sometimes I swear computers are not deterministic.

I'm inclined to call the BIOS viewing a coincidence. I don't see how just *viewing* cmos settings could do anything.

Still though, I would be open to anyone's ideas about this problem. I now remember that this is actually the THIRD time this has happened. The first time I just reformatted thinking wireless was broken, and it was only because I didn't have a disc handy the second time that I got to see wireless come back on its own like tonight.

I'll store away any suggestions for the next time this happens.

---

### Post by Psyman on 2008-12-22
Possibly related, possibly not- but worth a mention.

Shortly after I got my nc10 (within a couple of hours) installed Ubuntu 8.10. Later on that day all wireless networks disappeared out of nm-applet as described above. At the time i just rebooted into XP, thinking "i'll deal with it later" but the XP wireless wasn't working either! I uninstalled the driver, rebooteed to redetect and all was well again. then rebooted into ubuntu - under which the wireless ALSO worked. Coincidence, i thought at the time, but its just happened again- wireless not working under either OS. And the only thing that got it sorted again was to remove the driver from XP, power off and power on again. Hardware fault maybe?

---

