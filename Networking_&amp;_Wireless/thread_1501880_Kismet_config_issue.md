---
title: "Kismet config issue"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by Sojurner on 2010-06-04
I think i have pretty much everything set, however im trying to get all the info for my network card

the area im working on in the config file is the Source= part.
I have everything else but when i put in mac80211 at first it came back with a response then i accidentally closed the terminal.

Ive been trying to get that info back but dont know where i need to go or what i need to do to find it.

Any help would be greatly appreciated...

---

### Post by chili555 on 2010-06-04
Here is the source part from my conf file:> # to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,IntelI am not sure the third part really matters; I am going to try the word Momma some day!

I ran the command:```
sudo lshw -C network
```I got this information:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: [COLOR="Red"]wlan0[/COLOR]
       version: 02
       serial: 99:19:22:c2:1b:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR="Red"]iwl3945[/COLOR] I worked all this out when I read /usr/share/doc/kismet/README.gz

Please note that not every wireless driver will go into monitor mode and therefor will not work with Kismet.

---

