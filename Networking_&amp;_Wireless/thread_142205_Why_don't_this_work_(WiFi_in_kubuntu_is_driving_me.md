---
title: "Why don't this work??? (WiFi in kubuntu is driving me crazy!!!!)"
date: 2006-03-09
forum: Networking &amp; Wireless
---

### Post by mexlinux on 2006-03-09
I can not get kubuntu to properly connect to wifi networks, some times it connects, some times it does not, some times, everything seems to be correct, but it simply does not work.
Here I want to show an exmple of AFAIK a right configuration, bt it simply does not work....WHY????
I'm tired  start and stop services reboot the pc, it's simply not consistent...WHY????

Can someone please review this and tell me in this example (real example) what is wrong?

These are my files:
/etc/network/interfaces
```

auto lo
iface lo inet loopback
       address 127.0.0.1
       netmask 255.0.0.0

mapping hotplug
        script grep
        map eth1

iface eth1 inet static
        wireless-mode managed
        wireless-essid 2WIRE828
        address 192.168.0.66
        netmask 255.255.255.0
        gateway 192.168.0.1
iface eth0 inet dhcp              

```

/etc/resolv.conf
```

nameserver 192.168.0.1

```

I get this output from the commands:

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:16:6F:17:40:74
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe17:4074/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:323 errors:0 dropped:1 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36554 (35.6 KiB)  TX bytes:13509 (13.1 KiB)
          Interrupt:17 Base address:0xc000 Memory:dfbfd000-dfbfdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4808 (4.6 KiB)  TX bytes:4808 (4.6 KiB)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"2WIRE828"  Nickname:"2WIRE828"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:72:E1:3D:C9
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-59 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:10


```

route -n
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

```

But Ping gto the gateway gives: Destination Host Unreachable
and network of of course is not browsable.....

everytime I switch networks the only way I can enssure it will work is to modify the /etc/network/interfaces and reboot the machine (wifi-radar some times works, some times does not..) it's not working and suddenly works............. sad

---

### Post by roachk71 on 2006-03-10
[LEFT]As far as I'm aware, it's usually unnecessary for the loopback interface (lo) to have an address and netmask, since this refers to localhost (the computer itself.)

All of the other settings look fine.

And since the interface used is eth1, extra drivers apparently don't need to be loaded at boot time.

What wireless card are you using? If it's not a Prism-based card this could be an incorrect assignment.

The only setting I can see wrong here, since you're using a static IP address, is the wrong DNS server address. 192.168.0.1 is normally used by the router only when using DHCP; you may want to set this to one of your ISP's domain name server addresses (there can be more than one; they're usually separated by a space.)

```

iface lo inet loopback
        address 127.0.0.1  (this line and the next can be removed; they're unnecessary.)
        netmask 255.0.0.0

``` 
Another problem is that you have two interfaces in use; they usually conflict. So when you want to use only the wireless, comment out or remove this line:

```

iface eth0 inet dhcp

``` 

By the way, you don't really have to restart every time; before you modify the eth0 code, type
```

sudo ifdown eth0

``` in the terminal window.

A special note: As yet (and this is why I chose Ubuntu over Kubuntu,) KDE's wireless utilities don't work as advertised. You really do have to use commands in the terminal to make the cards work correctly. This isn't a Kubuntu bug, rather a KDE one. The KDE developers already know about this and are working on a solution for KDE 4.
[/LEFT]

---

### Post by mexlinux on 2006-03-10
Thanks for your answer
> it's usually unnecessary for the loopback interface (lo) to have an address and netmask, since this refers to localhost (the computer itself.)

It wasn't me, that came with kubuntu, or some package (?), OK I will remove it.
> 
What wireless card are you using? If it's not a Prism-based card this could be an incorrect assignment.

Intel Pro/wirless 2200bg

> 
The only setting I can see wrong here, since you're using a static IP address, is the wrong DNS server address. 192.168.0.1 is normally used by the router only when using DHCP; 

I will change it, but always worked with my previous distro (mandriva), and works with all the windows pc's in my office.

> 
Another problem is that you have two interfaces in use; they usually conflict. So when you want to use only the wireless, comment out or remove this line:

```

iface eth0 inet dhcp

``` 

I liked that one, I will comment that line.

> 
sudo ifdown eth0

Good to know!
.... well, I already have a script that does:
sudo ifconfg eth1 down
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
Is that the same?

> 
KDE's wireless utilities don't work as advertised. You really do have to use commands in the terminal to make the cards work correctly.

I can see!
Is it a good Idea to use wifi-radar or network-manager in kubuntu??
I have already wifi-radar, but it also works just some times...

Thanks,
Miguel

---

