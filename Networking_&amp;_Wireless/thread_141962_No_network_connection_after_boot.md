---
title: "No network connection after boot"
date: 2006-03-09
forum: Networking &amp; Wireless
---

### Post by sharingan on 2006-03-09
hi all

i have configured my wireless pcmcia card with **ndiswrapper **as suggested in the ubuntu [wiki]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto").

so far so good. i could start and stop both eth0 and wlan0 interfaces, but when i reboot my laptop no connecction comes up.

with the following [FONT="Courier New"]**/etc/network/interfaces**[/FONT] file what i got after running ifconfig is the lo and wlan0 up, but the wlan0 is without any configuration provided in the interfaces file.
with such configuration... it should boot with the eth0 interface up!!

running sudo [FONT="Courier New"]/etc/init.d/networking[/FONT] restart makes the rigth interfaces to appear, but i would like to start up nicely.

what can be wrong? could there be a service that is not starting correctly?

thnx for any help

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#        script grep
#        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.1.21
        netmask 255.255.255.0
        gateway 192.168.1.1

iface wlan0 inet static
#       name 3Com Wireless
        address 192.168.1.21
        netmask 255.255.255.0
        gateway 192.168.1.1
#       network 192.168.1.0
#       broadcast 192.168.1.255
        wireless_essid USRHOME
        wireless_mode Managed
        wireless_channel 11
        wireless_key1 xxxx
        wireless_defaultkey 1
#       wireless_keymode restricted
#       wireless_rate auto

#auto wlan0
auto eth0
```

---

### Post by prizrak on 2006-03-09
Umm, this is just a guess. But go into the network manager, and make sure that your eth0 is not configured (not just deactivated) and make sure that your wlan0 is both configured and activated. The issue could be that because you are doing it the CLI way, when you start it next time it uses settings setup with GUI. Like I said that's my best guess (sounds similar to my issue at least)

---

### Post by prizrak on 2006-03-09
Oh actually another thing. I'm not sure how ndiswrapper works since I got Atheros (fully supported) it's possible you have to get it started before networking loads just like you would with wpasupplicant.

---

### Post by sharingan on 2006-03-10
hi prizrak

[QUOTE=prizrak]go into the network manager, and make sure that your eth0 is not configured (not just deactivated) and make sure that your wlan0 is both configured and activated. [/QUOTE]
i checked the GUI configuration and it's the same as the given in the /etc/network/interfaces file. (see attachments) :neutral: 

wlan0 should be activated when the computer starts.

[QUOTE=prizrak]it's possible you have to get it started before networking loads just like you would with wpasupplicant.[/QUOTE]
how do i check that **ndiswrapper** is started before networking?

thnx

---

