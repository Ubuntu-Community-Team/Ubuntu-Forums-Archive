---
title: "Gain a IP address at Machine Boot"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by Living2007 on 2010-03-09
I am running Ubuntu 8.04, and I am able to access my machine via SSH, but I only want the log in screen visible on the machine itself, yet still able to work with the SSH.

But to do this, I have to log in, get the IP address, log off, then log in via SSH. How do I make the machine receive an IP address during the boot-up!

---

### Post by chili555 on 2010-03-09
You can remove Network Manager and set up your details in */etc/network/interfaces*. If you need to SSH into the machine, it would also seem handy to use a static IP address. Here is a brief tutorial: [http://ubuntuforums.org/showpost.php?p=8811744&postcount=5](http://ubuntuforums.org/showpost.php?p=8811744&postcount=5)

Make sure, if you use a static IP address, to select an address outside the range of the DHCP server in the router or switch. Also, you must set up */etc/resolv.conf*. The address of the gateway works perfectly well:```
nameserver 192.168.what.ever
```

---

### Post by Living2007 on 2010-03-10
OK, I have entered some information into /etc/network/interfaces and it's failing to connect.
I noticed that Manual Configuration has shown up on the NM applet, and somethings are right. SSID has turned into ESSID and the WEP is set to 64/128-bit Hex, it should be 64/128-ASCII. What needs to be fixed in /etc/networks/interfaces ?

---

### Post by Iowan on 2010-03-10
What information did you enter into */etc/network/interfaces*? Did you restart afterwards? What shows up if you enter (in a terminal):```
ifconfig -a
```

---

### Post by chili555 on 2010-03-10
> SSID has turned into ESSIDThey are the same.> WEP is set to 64/128-bit Hex, it should be 64/128-ASCII.Change the wireless-key part to include [COLOR="Red"]s:[/COLOR]```
wireless-key s:<your_ascii_key>
```

---

### Post by Living2007 on 2010-03-10
> **Iowan said:**
> What information did you enter into */etc/network/interfaces*? Did you restart afterwards? What shows up if you enter (in a terminal):```
ifconfig -a
```

here is what /etc/network/interfaces says:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.o
gateway 192.168.1.1
wireless-essid wireless
wireless-key 3uvaxxxxxxxpe

#auto eth0
iface eth0 inet dhcp
```

My ubuntu can't connect to the internet so I can't post the ifconfig, but it follows these settings...

---

### Post by chili555 on 2010-03-10
Your wireless key appears to be ASCII; it's 13 characters. Please add s: as I indicated above:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.10
netmask 255.255.255.[COLOR="Red"]0[/COLOR]
gateway 192.168.1.1
wireless-essid wireless
wireless-key [COLOR="Red"]s:[/COLOR]3uvaxxxxxxxpe

#auto eth0
iface eth0 inet dhcp
```Restart networking:```
sudo /etc/init.d/networking restart
ping -c3 www.google.com
```Did you amend */etc/resolv.conf*?

---

### Post by Living2007 on 2010-03-11
Thanks, i didn;t see the 5th post, but that is now up to date. I can now ping. Thanks

resolv.conf has not been edited. It already has the following:

### BEGIN INFO
#
# Modified_by: NetworkManager
# Process:       /usr/bin/NetworkManager
# Process_id:   4704
#
### END INFO

search home


nameserver 192.168.1.1

EDIT: I am now able to do SSH! Thanks to those to have helped :)

---

