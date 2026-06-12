---
title: "Lost my wifi card after Synaptic &quot;mark all upgrades&quot;"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by spier on 2006-05-01
(Running Ubuntu 5.10, upgraded to 2.6.12-10-686, on Vaio FS740 notebook with  Intel(R) PRO/Wireless 2200/2915 Network Driver)

After running a Synaptic general upgrade ('Mark all upgrades' + 'Apply' - the first time I tried it so far) my wifi interface vanished, i.e., System --> Administration --> Networking shows no wireless card.

Now, selecting the old 2.6.12-9-386 release from grub, my wifi works flawlesly with the same /etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
        map eth0

# The primary network interface
iface eth0 inet static
wireless-essid my_sid
wireless-key s:my_key
address 192.168.1.140
netmask 255.255.255.128
gateway 192.168.1.129

auto eth0

```

Looking at Synaptic history I noticed those upgrades:

linux-headers-2.6.12-10 (2.6.12-10.24) to 2.6.12-10.30
linux-headers-2.6.12-10-386 (2.6.12-10.24) to 2.6.12-10.30
linux-headers-2.6.12-10-686 (2.6.12-10.25) to 2.6.12-10.30
linux-image-2.6.12-10-386 (2.6.12-10.24) to 2.6.12-10.30
linux-image-2.6.12-10-686 (2.6.12-10.25) to 2.6.12-10.30

Any hints?

Thanks in advance,

spier

---

