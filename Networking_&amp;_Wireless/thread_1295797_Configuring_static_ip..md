---
title: "Configuring static ip."
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by rlarrowe on 2009-10-19
I can't figure out how to set up a static ip.  I have been to many forums and all of the solutions have resulted in no connection.  I want to be sure I have the right information about my connection.  So I need to know the commands to get it, and either the command line way or the gnome gui way to set it up.

Thx

---

### Post by gareththered on 2009-10-20
Are you using wireless or ethernet?

---

### Post by Iowan on 2009-10-20
A couple of options: Network Manager or */etc/network/interfaces*. Does machine currently get address via DHCP? Does the network have a DHCP server whose lease range you must avoid?

---

### Post by rlarrowe on 2009-10-20
ethernet (adsl) U.S. Robotics maxG

I am using DHCP.

---

### Post by rlarrowe on 2009-10-20
Also, I have my internet through at&t.  Don't know about the leased IPs thing.

Here is the current /etc/network/interfaces:

>auto lo
>iface lo inet loopback

---

### Post by DGortze380 on 2009-10-21
> **rlarrowe said:**
> Also, I have my internet through at&t.  Don't know about the leased IPs thing.

Here is the current /etc/network/interfaces:

>auto lo
>iface lo inet loopback

Should look something like this, replace with your appropriate network values. You may have to uninstall Network Manager.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
network 192.168.0.0
broadcast 192.168.0.255


```

---

### Post by cariboo on 2009-10-21
If you are running Jaunty, setting the static ip address using /etc/network/interfaces is not going to work. You can use network-manager to set a static ip address.

---

### Post by gareththered on 2009-10-21
The example posted by DGortze380 will work if you are using Ethernet.  If you are using wireless then you will need additional entries in the same file to configure encryption etc.

cariboo907: Jaunty does work with static IP addresses in the /etc/network/interfaces - I have it that way on three of my machines!

Below is an example 'interfaces' file from one of my machines:-
```
auto wlan0
iface wlan0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless_essid GTR
pre-up wpa_supplicant -Dwext -B -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```'wlan0' is the name of the wireless network interface on this particular machine and is in the 1st, 2nd and 7th line.  Make sure you change yours accordingly.  The 6th line contains the SSID (or name) of your wireless network, which will also need to be changed.
The 7th line refers to a file '/etc/wpa_supplicant.conf'.  This contains the encryption and pass key for the connection.  Mine is as follows:-```
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="GTR"
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk=<very long hex string>
}

```The psk's <very long hex string> is generated from your SSID (network name) and passphrase.   For example, for my 'GTR' network and a passphrase of 'password', type ```
wpa_passphrase gtr password
```  You will get ```
network={
        ssid="gtr"
        #psk="password"
        psk=cf981039119bedfc1ddd3bfa2cd991e585f4746d686bbc9570402f1b6e9be0ba
}

```which you can use to create '/etc/wpa_supplicant.conf'.

Good luck!

---

### Post by slakkie on 2009-10-21
> **cariboo907 said:**
> If you are running Jaunty, setting the static ip address using /etc/network/interfaces is not going to work. You can use network-manager to set a static ip address.

Excuse me? Have a look in my signature. You will see it is possible.

---

### Post by rlarrowe on 2009-10-21
Problem solved.  I didn't have the line:

   auto eth0

in my /etc/network/interfaces file.

Thanks for the help

---

### Post by Iowan on 2009-10-22
It's always good to see those [SOLVED] threads. :)
(Hint, hint... under Thread Tools)

---

