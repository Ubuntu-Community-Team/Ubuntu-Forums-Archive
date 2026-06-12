---
title: "Wireless card not detected"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by Culpa on 2011-05-09
Usually when I have a problem a simple search yields a solution. However, since I've updated my Ubuntu version to 11.04, I've lost the ability to use wireless on my laptop. I've tried many things but so far nothing has worked. Here's the abridged output to some commands I ran, hopefully someone here can see a solution.

```
:~$ sudo lspci
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
``````

:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
``````
:~$ sudo lshw -C network
*-network
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0
       resources: irq:17 memory:91000000-9100ffff
``````

:~$ sudo rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```To me it looks like the problem is with the wireless LAN being soft blocked though I'm not entirely sure. If anyone can give some suggestions it would be great.

---

### Post by josephmills on 2011-05-09
try ```
rfkill unblock all 
``` any thing ?

---

### Post by Culpa on 2011-05-09
> **josephmills said:**
> try ```
rfkill unblock all 
``` any thing ?

Doesn't look like that changed anything. rfkill list is still showing Wireless LAN as soft blocked and iwconfig shows no wireless. :/

---

### Post by josephmills on 2011-05-09
```
lspci -nn | grep Ath 
```
```
lsmod | grep ath 
```
```
dmesg | grep ath 
```please paste here thanks

---

### Post by Culpa on 2011-05-09
```
:~$ sudo lspci -nn | grep Ath
08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
```

```
:~$ lsmod | grep ath
{no output}
```

```
:~$ dmesg | grep ath
[    1.092191] device-mapper: multipath: version 1.2.0 loaded
[    1.092195] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.436779] ndiswrapper: driver netathw (,11/05/2010,9.2.0.104) loaded
```

---

### Post by josephmills on 2011-05-09
please see post #4 again thanks

---

### Post by Culpa on 2011-05-09
```
:~$ sudo lspci -nn | grep Ath
08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X  Wireless Network Adapter (PCI-Express) [168c:002a] (rev  01)
``````
:~$ lsmod | grep ath
{no output}
``````
:~$ dmesg | grep ath
[    1.092191] device-mapper: multipath: version 1.2.0 loaded
[    1.092195] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.436779] ndiswrapper: driver netathw (,11/05/2010,9.2.0.104) loaded
```

---

### Post by josephmills on 2011-05-09
please go to ubuntu softtware center then go to Edit-->sotware sources then make sure all are ticked see pic then close out of software sources  and ubuntu software center. then do a```
sudo apt-get update 
```then```
sudo apt-get upgrade
``` then ```
sudo reboot
``` then after reboot please do step #4 again and post here thanks

---

### Post by Culpa on 2011-05-09
Ok did it all. The only source that wasn't checked was "Conical partners (source code)" and when I updated and upgraded nothing new was installed. The reboot took longer than normal but after going through everything again nothing seems to have changed :/

I appreciate all the help though.

---

### Post by josephmills on 2011-05-09
Sorry about the lag I got called in to work:( but you need the ath9k mods to load and you need to get the firmware also. and you will be up and running so there are a couple of ways to do all of this I THINK that you need the linux-firmware so try ```
sudo apt-get install linux-firmware 
``` is it all ready installed? 
next you are going to need the ath9k mods to load try ```
sudo su 
``` then ```
modprobe ath9k
```then ```

echo ath9k >> /etc/modules
``````

exit
```  so the ath9k + linux-firmware= working wireless
also make sure that nothing is blocking it ```
rfkill list 
```

---

### Post by Culpa on 2011-05-09
lol don't worry about the lag. The linux-firmware was already installed and up to date. The modprobe command gave an error however:

```
# modprobe ath9k
WARNING: Error inserting ath9k_hw (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Here's the output from the dmesg:

```
:~$ dmesg | grep ath
[19907.381528] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[19907.381785] ath: Unknown symbol freq_reg_info (err 0)
```

I searched the error up too and haven't found anything that helps me. :/

---

### Post by josephmills on 2011-05-09
could we please see a ```
modinfo ath9k
```

---

### Post by josephmills on 2011-05-09
you could also try this ```
sudo -s

echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
```
then reboot anything?

---

### Post by Culpa on 2011-05-10
Here is the modinfo

```
:~$ modinfo ath9k
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     01818FC37C72588C93B13E4
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,cfg80211,ath9k_common,ath
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
```> **josephmills said:**
> you could also try this ```
sudo -s

echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
```then reboot anything?

Still no wireless after rebooting :/

---

### Post by josephmills on 2011-05-10
ok please go to synaptic and type in firmware into the the search barr please take a screen shot just like mine thanks or just tell me the ones that are installed (green box)

---

### Post by hennesa on 2011-05-10
Same problem with me.

The wireless was working perfect with ubuntu 10.10. then when I upgraded to 11.04. it stoped working.
Strange!!

---

### Post by Culpa on 2011-05-11
> **josephmills said:**
> ok please go to synaptic and type in firmware into the the search barr please take a screen shot just like mine thanks or just tell me the ones that are installed (green box)

Ok the ones installed are:
linux-firmware, syslinux, syslinux-common, hpijs, lshw, and lzma. :)

---

