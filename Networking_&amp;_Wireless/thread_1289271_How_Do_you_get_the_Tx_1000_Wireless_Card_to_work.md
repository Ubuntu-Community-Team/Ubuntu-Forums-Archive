---
title: "How Do you get the Tx 1000 Wireless Card to work"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by OB099 on 2009-10-12
[COLOR=black][FONT=Verdana]Hi, [/FONT][/COLOR]

 
[COLOR=black][FONT=Verdana]I have a Tx 1000 Hp Laptop and I have installed Ubuntu on it but i can not get the wireless to work, i have goggled and read through some forums but still have not managed to get it working, I’m having issues installing the driver (I don’t no how to) any help on this would be appreciated.[/FONT][/COLOR]

---

### Post by atomizer on 2009-10-12
What chipset is your wireless?

---

### Post by chili555 on 2009-10-12
> **atomizer said:**
> What chipset is your wireless?Find out by opening a terminal and doing:```
sudo lshw -C network
```Search for your chipset (Broadcom 431x??) or post back for help.

---

### Post by OB099 on 2009-10-12
*-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:77:cf:06:10:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

hi this is what i got, still need help :)

---

### Post by Ayuthia on 2009-10-12
For some reason the b43 module is loaded by default for this wireless card even though it does not work with it.  You will need to do the following in the Terminal:
```
echo blacklist b43 |sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb |sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules
sudo update-initramfs -u
```These commands will prevent the b43 and ssb modules from loading and make the Broadcom STA (wl) module load when the system starts up.  The final command will make sure that the b43 and ssb modules do not get started up during the initial portion of booting.

Next, go into System->Administration->Hardware Drivers and activate the Broadcom STA option.  

Finally do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```or you can restart your computer.  These two commands will remove the conflicting wireless module and load the Broadcom STA module.

Hope that helps.

---

### Post by OB099 on 2009-10-13
Hi Mate,

i did all that you said, still not working, i did notice that the Broadcom STA Wireless Driver says it is enabled but not in use.

---

### Post by OB099 on 2009-10-13
Latest:

*-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:83:f4:a2:1d:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Ayuthia on 2009-10-13
Can you try the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
sudo iwlist scan
```
We are going to manually remove the possible wireless modules and load the Broadcom STA version.  Then we will scan for wireless sites.  If this works, we will need to backtrack and see why the blacklisting did not work.

---

### Post by OB099 on 2009-10-14
Hi Mate when i did your last it came back with this: 

daniel@daniel-laptop:~$ sudo modprobe -r b43 ssb wl ndiswrapper
[sudo] password for daniel: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
daniel@daniel-laptop:~$ 

Not really sure what this means ?

---

### Post by Ayuthia on 2009-10-14
They are just warnings saying that the two files will need to have a .conf (ndiswrapper.conf instead of ndiswrapper) extension in future releases.  You should be able to go ahead with the commands without any real issue.

If it still does not produce any wireless sites, please post the results of:
```
lshw -C network
dmesg|grep -e wl -e ndis -e b43 -e ssb
```
The last command will search through the message log to see what matches those search strings (wl, ndis, b43, ssb).

---

### Post by OB099 on 2009-10-15
still not working results below:

daniel@daniel-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:a0:52:da:df:07
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
daniel@daniel-laptop:~$ dmesg|grep -e wl -e ndis -e b43 -e ssb
[    5.609979] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
[    5.609989] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    5.680213] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0

---

### Post by Ayuthia on 2009-10-15
> **OB099 said:**
> still not working results below:

daniel@daniel-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:a0:52:da:df:07
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
daniel@daniel-laptop:~$ dmesg|grep -e wl -e ndis -e b43 -e ssb
[    5.609979] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
[    5.609989] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    5.680213] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0

Did you do:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
```
commands before you ran lshw -C network?  Normally the system will either return that the device is UNCLAIMED or else it will show the wl0 module in the driver portion.

If you did, can you post the results of:
```
ls /lib/modules/$(uname -r)/volatile
```This is the location where the wl module is stored.  I want to verify that it is there.

---

### Post by OB099 on 2009-10-15
Hello mat yes i did do it in that order here is what i got back from the last command:

daniel@daniel-laptop:~$ ls /lib/modules/$(uname -r)/volatile
ath_hal.ko            ath_rate_onoe.ko    wlan.ko           wlan_wep.ko
ath_pci.ko            ath_rate_sample.ko  wlan_scan_ap.ko   wlan_xauth.ko
ath_rate_amrr.ko      wlan_acl.ko         wlan_scan_sta.ko  wl.ko
ath_rate_minstrel.ko  wlan_ccmp.ko        wlan_tkip.ko
daniel@daniel-laptop:~$

---

### Post by vxice on 2009-11-18
was this ever solved?  I ask because I have a similar problem, I just installed xubuntu 9.04 on a compaq r4000(long story short was trying many versions and this is the one that finally worked due to a combination of finally thinking to clean the disk and cd lens as well as needing a crt monitor because of poor default settings many disks from different cd burners and versions are in my trash)  there is a bcm4306 v3 wireless controller.  I used the steps at [http://www.darshancomputing.com/r4000/gentoo64-install.html](http://www.darshancomputing.com/r4000/gentoo64-install.html) so have ndiswrapper and the proprietary drivers installed.  step 5 gave me trouble and then I stubled upon this thread and did all those blacklists.  The place where it diverges I guess would be lshw -C network where that first line reads *-network:0 UNCLAIMED.  Am also getting those warnings about the .conf thing.  when i try the modprobe -r b43... gives similar error stating it is ignoring bad line starting with 'ssb' thanks for any help.

---

### Post by vxice on 2009-11-18
ok appear to have gotten a step further reading through a large number of other threads, edited /etc/modprobe.d/blacklist.conf by hand to blacklist ssb for and then reloaded ndiswrapper using modprobe and it now seems to be installed.  I checked on lshw -C network and it now lists ndiswrapper as being the driver for it.  then updated everything using update-initramfs -k all -u.  eventually i need to see a list of wireless networks and encrypted networks, but ill leave those for later.  another set of instructions say that once the ndis is loaded I need to 

iwconfig wlan0 essid YOUR-NETWORK_ID
        iwconfig wlan0 key restricted YOUR-NETWORK-ID
        dhcpcd wlan0

but that 2nd command trips me up.  gives me SET failed on device wlan0 ; Invalid argument. any suggestions?

---

