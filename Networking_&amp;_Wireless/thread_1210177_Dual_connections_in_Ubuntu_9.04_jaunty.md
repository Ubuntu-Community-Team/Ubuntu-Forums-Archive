---
title: "Dual connections in Ubuntu 9.04 jaunty"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by Paulos-The-Great on 2009-07-11
Hello Linux Lovers! This is my first post EVER so bear with me and my noob questions,

Dual connections in Ubuntu 9.04 jaunty

Ok here we go...

I want to connect my jaunty desktop to my isp via Ethernet AND wirelessly connect to my Windows Home Server on a separate network. Is it possible to have simultaneous connections?

In case thats not clear i want to connect to 2 routers at the same time. 1 for internet and 1 for storage.

Any help would be appreciated :p

Really want to move away from windows as much as possible.

Thanks in advance.

Paulos-The-Great

---

### Post by superprash2003 on 2009-07-11
yes that is possible , it should work by default

---

### Post by Iowan on 2009-07-12
Network Manager may balk, but you *should *be able to set it up via */etc/network/interfaces*.

---

### Post by Paulos-The-Great on 2009-07-15
Thanks for replying people,

How would i go about configuring  [I]/etc/network/interfaces to suit my needs?

Also network-manager only seems to connect to ONE network at a time. How do i configure something ie, (Please Specify in your opinion the best network app) to connect to both at the same time?

Thanks again


Paulos-The-Great
[/I]

---

### Post by martinbaselier on 2009-07-15
For /etc/network/interfaces to work, it's best to disable or remove network-manager. 
I presume your wired network is on eth0.
You can check the available cards and their setup with **ifconfig** and **iwconfig** for wireless networks.

Open a terminal.
To paste into the commandline, use ctrl+shift+v.
Or triple click to select the line you want to copy/paste and use the middle mouse button (middle mouse button pastes selected text)

enter the following command:
**sudo gedit /etc/network/interfaces**
enter your password

Past the following lines into it.
```

auto lo eth0
iface eth0 inet dhcp
iface lo inet loopback

```
That should be enough to get online. 


Then you kill the network manager, to see if it will work:
**sudo killall -KILL networkmanager**

I hope networkmanager is the correct name, since I don't have it installed. Otherwise use:
**ps -e | grep net**
This will show you the correct name.

Use **sudo ifdown eth0** and **sudo ifup eth0**, to respectively turn the network off and on. (for eth0 of course)

If this is working, you can setup the wireless network. 

I presume wireless is on wlan0
add wlan0 to the auto line (for automatic connections)
and create a setup.

I will presume the wireless network will be static in the 192.168.1.xxx range.(for an educational purpoase) and your gateway has the address 192.168.1.1 and you use WEP encryption.
```

iface wlan0 inet static
address 192.168.1.2
broadcast 192.168.1.255
netmask 255.0.0.0
gateway 192.168.1.1
wireless-essid SSID
wireless-key s:WEPKEY

```
Change SSID to the SSID of your home network.
And WEPKEY to your WEP key (in ascii)
If you don't use a wepkey, just don't use the line.
for WPA you would need the wpa_supplicant daemon.

For more information type 
[B]man interfaces
man iwconfig
man ifconfig
man wpa_supplicant[/B]

---

### Post by Paulos-The-Great on 2009-07-23
Hi [martinbaselier]("http://ubuntuforums.org/member.php?u=578534") thanks for replying and being very specific.

My question is where do I enter the wireless code you gave me?:confused: into the network-interfaces file where I configured eth0?

Also the wireless will be WPA and i have the supplicant installed already so what do i code into the network-interfaces file:confused:
Thanks again, the more I play with Linux the more I like it.[IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

Paulos-The  Great

---

