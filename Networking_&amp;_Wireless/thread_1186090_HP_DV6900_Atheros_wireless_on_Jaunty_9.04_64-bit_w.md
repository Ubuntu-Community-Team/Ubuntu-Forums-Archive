---
title: "HP DV6900 Atheros wireless on Jaunty 9.04 64-bit working!"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by beetlejuice321 on 2009-06-13
Hardware: HP Pavilion dv6911us
OS: Ubuntu Jaunty-Jackalope 9.04 64-bit

Had problems with my install, including that annoying [ACPI issue]("http://ubuntuforums.org/showthread.php?t=1137421") with system not booting off of the batter unless a button is pressed (AC power is fine).

As for the Atheros wireless adapter here is how I got mine working successfully.

SOLUTION:
1) install linux-backport-modules and 2) blacklist ath_pci and ath_hal.

To install the backport modules, just search for it on Synaptic or use apt-get or aptitude, it&#8217;s called linux-backports-modules-intrepid. Then on System/Administration/Hardware Drivers make sure Atheros driver is activated.

    ```
sudo aptitude install linux-backports-modules-intrepid
```

For Jaunty Users run the following comamnd

    ```
sudo apt-get install linux-backports-modules-jaunty

```
To blacklist the old modules, do this:

    ```
gksudo gedit /etc/modprobe.d/blacklist
```

And add the following lines At the bottom of the file save and exit

    ```
blacklist ath_hal
blacklist ath_pci
```

Now you need to reboot your system.

IF after this steps you still cannot make it work, you probably have something left still blacklisting ath5k, thus making it not to load. You should search all the files on /etc/modprobe.d for all lines that had:

```
blacklist ath5k
```

And add a # before the start of the line, thus making it into a comment so the above one becomes

    ```
# blacklist ath5k
```

Save and exit the file

I hope this help for some one to fix their wireless problem.

For details regarding these instructions see this [Ubuntu Geek]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html") document.

Also here is the output of my "lshw -C Network":

> *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:68:c1:46:e4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.104 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:a7:58:ba:9d:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

