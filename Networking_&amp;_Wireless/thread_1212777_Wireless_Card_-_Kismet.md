---
title: "Wireless Card - Kismet"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by shang1 on 2009-07-14
Greetings,
I have been trolling the forums and have come to a dead end so decided to ask for assistance.

I am currently using a HP dv-5 pavillion laptop and am attempting to get kismet to work for me,

I have taken the following steps:
The obvious of,
```
sudo apt-get install kismet
```

However when this did not work as a normal user or as admin, I found out the card type:
```
Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
Subsystem: Intel Corporation Device 1211
Flags: bus master, fast devsel, latency 0, IRQ 2294
Memory at de200000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: iwlagn
Kernel modules: iwlagn
```

Then how it was being used on the network:
```
 *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: X
       logical name: wmaster0
       version: 00
       serial: X
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.4 latency=0 modul
```

All the time hunting for what to put as the:
```
source= in my kismet.conf
```

Lastly I tried to put my card into monitor mode manually using:
```
iwconfig wlan0 mode monitor

```

To which I got another fun error. My question is, are their drivers which can allow me to put my card into this mode? Or is kismet incompatible with this wireless card? If yes, is their another program I can use with the same (or similar) functionality?

Regards,

---

### Post by shang1 on 2009-07-14
*Sigh*
To anyone else who has the above issue(s).
Try this for the intel card:

```
source=iwl4965,wlan0,test
```

(it worked for me)

---

### Post by chili555 on 2009-07-14
You probably need to take the interface down first and use sudo:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Please let us know.

---

