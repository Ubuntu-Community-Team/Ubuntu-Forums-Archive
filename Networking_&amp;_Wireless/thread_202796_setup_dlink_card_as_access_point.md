---
title: "setup dlink card as access point"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by mrweirdo on 2006-06-24
Hello I have a working D-Link DWL-520 rev a PCI wireless b card setup in my ubuntu server box(no gui only shell) which makes use of the prism 2.5 driver. I got it working buy installing linux-wlan-ng and then adding an entry to /etc/network/interfaces
```

iface eth2 inet static
        address 192.168.2.1
        netmask 255.255.255.0
        broadcast 192.168.2.255
        network 192.168.2.0
        wireless_keymode open
        wireless_essid kellywap

```
then brought up the interface eth2. It is now working with the staticly assigned address. 

What i need to do next is make it into the access point so my apple laptop can connect to it. Any help would be apriciated oh and I will probably want to secure the conection but that comes after I get it working.

---

### Post by mrweirdo on 2006-06-24
for some reason if i do:
sudo iwconfig eth2 mode master
I get the following error:
```

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Operation not supported.

```

but if i do ad-hoc it will allow me to do that then I can access my linux box from my mac by chosing an ad-hoc network. Anyone know why its not letting me set it up as an access point?

---

### Post by tturrisi on 2006-06-24
run iwpriv to see all modes supported in the driver for your wlan.

---

### Post by mrweirdo on 2006-06-26
ah well doesnt look like i need to anyways right now. I just went a got a new wireless card from best buy so I'm swaping them out for faster speeds :) thanks for the response though Ill use that if i have the same problem with the new card.

---

