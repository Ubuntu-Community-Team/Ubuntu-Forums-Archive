---
title: "no network connection"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by ghettocounsler on 2009-07-19
[LIST]
[*]Using Kubuntu (Ubuntu 9.04)
[*]attempting wired connection to network I've been attached to before, network uses static IP addresses
[*]no known reasons why worked previously and now not working (although obviously there is some reason)
[*]**cannot paste easily because having to use different computer to connect**
[*]cannot ping gateway host unreachable
[*]cable is not bad and network otherwise working as expected
[/LIST]
Appreciate any assistance at debugging this issue.

---

### Post by dlmarti on 2009-07-19
you haven't given any information to start debugging the issue.

Please start with copying the output of "ifconfig".

---

### Post by ghettocounsler on 2009-07-19
some output:

> 
root@mark-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1a:4d:66:9b:28
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4032 (4.0 KB)  TX bytes:4032 (4.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:77:e2:0d
          inet addr:192.168.2.112  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fe77:e20d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8213 (8.2 KB)  TX bytes:5437 (5.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-77-E2-0D-32-30-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@mark-desktop:~$

> root@mark-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HB (ICH8) 4 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)

> root@mark-desktop:~$ lshw -class network
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 12
       serial: 00:1a:4d:66:9b:28
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.2.112 latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:77:e2:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.112 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:69:92:7e:33:d4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@mark-desktop:~$

---

### Post by dlmarti on 2009-07-19
which interface are your trying to configure, the wireless or wired connection?

---

### Post by ghettocounsler on 2009-07-19
at this point the wired, wireless would be icing on the cake but I've only got a netgear MS compatible usb stick so thought I'd get wired going first then look at the wireless later as I might need some packages. 

I'd made an attempt at the wireless 1st by editing /etc/network/interfaces but no luck, here is the file currently
> 
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.112
gateway 192.168.2.1
dns-nameservers 192.168.2.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid JKLnet
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk ab7afcb8f39cca1f42320f3b81469ca00f799265d573f570e62540c7cae9ed95

---

### Post by dlmarti on 2009-07-19
you should be able to setup the network from system->Preferences->Network Connections

Or if you want to try this:
just type ifconfig eth0 192.168.2.75
or any valid ipaddress for your network

Then try to ping the gateway at 192.168.2.1

If that works, then this is just a simple setup issue.

---

### Post by ghettocounsler on 2009-07-19
Ok that did work although I used eth1 (no eth0 available).

---

### Post by dlmarti on 2009-07-19
Then you should be able to use this:
system->Preferences->Network Connections

To setup your network, or are you saying that didn't work?

---

### Post by ghettocounsler on 2009-07-19
I was saying that the ping of the gateway was successful after following your instructions. 

I have no system -> preferences->Network Connections

Kubuntu:
I do have system settings -> network settings -> network management 
Under wired the various bits are (with what I set them too):
= Ethernet tab =
- ethernet MAC address
- MUT (options)
* Automatic
* various bytes settings
= IP Address tab =
- method (options)
* DHCP
* Auto
* manuual (this seems the only one to allow specifying an IP)
* DHCP with Manual DNS
== addresses == 
- address - I used 192.168.2.75
- prefix - ?? i put nothing here ??
- gateway - 192.168.2.1
- DNS servers: 192.168.2.1

I then did a reboot and I can ping the gateway and other computers on the network but not google.com

---

### Post by dlmarti on 2009-07-19
ok, so thats progress.

so it looks like we just need to get your DNS working.

Your prefix, should probably be 192.168.2.0, but thats probably not a big omission.

so, on to your DNS
Right now you have your DNS pointing at your router, unless your router is setup to be a DNS this is wrong.

Lets test your routers DNS capability:
in a console window type "telnet 192.168.2.1 53"

If you get something like: 
[B]"Trying 192.168.2.1...
telnet: Unable to connect to remote host: Connection refused"[/B]
The router doesn't do DNS

If you get something like:
[B]"Trying 192.168.2.1...
Connected to 192.168.2.1.
Escape character is '^]'.[/B]"
Then the router DOES do DNS

My gues is it doesn't and you need to set the proper name server IP addresses into your setup.

---

### Post by ghettocounsler on 2009-07-19
I did get this from the telnet:

[B]"Trying 192.168.2.1...
Connected to 192.168.2.1.
Escape character is '^]'.[/B]"

---

### Post by dlmarti on 2009-07-19
Then we need to try two things.
1. type nslookup and then when the prompt comes up, type [www.google.com](www.google.com) and hit return

This will cause your router to do a lookup for the host, and may return information we can use.

2. What kind of router is this?  Login to the router and find out what IT thinks the nameserver IP's are.  Try to ping these nameservers.

---

### Post by ghettocounsler on 2009-07-20
> root@mark-desktop:~$ nslookup
> [www.google.com](www.google.com)
Server:         192.168.2.1
Address:        192.168.2.1#53

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 72.14.213.103
Name:   [www.l.google.com](www.l.google.com)
Address: 72.14.213.147
Name:   [www.l.google.com](www.l.google.com)
Address: 72.14.213.99
Name:   [www.l.google.com](www.l.google.com)
Address: 72.14.213.105
Name:   [www.l.google.com](www.l.google.com)
Address: 72.14.213.104
Name:   [www.l.google.com](www.l.google.com)
Address: 72.14.213.106
>

This is a cisco router (home use type) and unfortunately I'm not in possession of the pw, my father setup the network in the house and he has passed away.

---

### Post by dlmarti on 2009-07-20
> **ghettocounsler said:**
> This is a cisco router (home use type) and unfortunately I'm not in possession of the pw, my father setup the network in the house and he has passed away.

What does your /etc/resolv.conf file say???

---

### Post by ghettocounsler on 2009-07-20
resolv.conf
I manually added nameserver 192.168.2.1 as without this there is no joy. ashland fiber is the carrier in these parts.
> root@mark-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain pc.ashlandfiber.net
search pc.ashlandfiber.net
nameserver 66.241.64.12
nameserver 66.241.64.11
nameserver 192.168.2.1
root@mark-desktop:~$
(the above step does not need to be redone on restart)

I tracked down some other stuff as well which lead me to execute these items from bash:
> ifconfig eth1 192.168.2.75
route add default gw 192.168.2.1
again without these there is no joy (each restart of the computer these need to be redone)

Note for others having this problem: there is information out there about making edits to gedit /etc/network/interfaces but it seems that this is for naught when NetworkManager is running (some speculation here at present). 

With the above things are working (wired) not withstanding having to run those commands each restart. I'm not sure I like the NetworkManager might rather have conf files manuallly handled.

Oddly however the connection to this machine is unreliable as WinXP computers on the network are not having any of these problems. The network is a cable connection and the problem is that the upload/download are volatile, one minute greate next minute you're pulling your hair out (I've never worked on a cable connection before).

---

### Post by dlmarti on 2009-07-20
I don't know how kubuntu differs from regular Ubuntu.

In my setup, I just go to system->preferences->network connections, and setup the network.  Its pretty seamless.

Can you ping these two nameservers?
nameserver 66.241.64.12
nameserver 66.241.64.11

---

### Post by ghettocounsler on 2009-07-20
I CAN ping those name servers. 

I think Kubuntu just has different names for the links to get there, in the end seems we get to the same place. Trouble is that in the NetworkManager there is no recognition in the setup that the connection is being used ?? so this seems a bit of a disconnect in the GUi

---

### Post by dlmarti on 2009-07-20
what does it show as your setup now?
Did you delete the auto configs, and create a new static config?

---

### Post by ghettocounsler on 2009-07-20
sorry I don't know what you are referring to "your setup now"
Other then the bash commands:
ifconfig eth1 192.168.2.75
route add default gw 192.168.2.1 			 		
and previously mention edit to /etc/resolv.conf (adding  nameserver 192.168.2.1) I have done nothing not noted in this thread. Other then rebooting the machine and uninstalling the KDE Network Manager (to leave me with the ubuntu NetworkManager (I believe)).

---

### Post by dlmarti on 2009-07-20
I was referring to the config you entered into the network connections application.
I'm very experience with Linux, a little bit with Ubuntu/Gnome, none with KDE.
I don't know what the proper application to use with KDE is.

Basically what we need in an application or set of scripts configured to setup your network on boot-up.  Under Ubuntu/Gnome, this is System->Preferences->network connections.
Not sure what it is under KDE.

---

### Post by ghettocounsler on 2009-07-20
I currently have NO configurations in the network management tool meaning in the GUi link of the widget on the toolbar when I open it to 'manage connections' there is nothing in there. It does however show I'm connected via 'eth1'

/etc/network/interfaces still only shows this config
> 
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.112
gateway 192.168.2.1
dns-nameservers 192.168.2.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid JKLnet
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk ab7afcb8f39cca1f42320f3b81469ca00f799265d573f570e62540c7cae9ed95
wpa-key-mgmt WPA-PSK
wpa-psk ab7afcb8f39cca1f42320f3b81469ca00f799265d573f570e62540c7cae9ed95

eth1 in ifconfig looks as expected:
> 
eth1   Link encap:Ethernet  HWaddr 00:1a:4d:66:9b:28
          inet addr:192.168.2.75  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe66:9b28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:972005 (972.0 KB)  TX bytes:696232 (696.2 KB)
          Interrupt:16

so it all does make you wonder if the network manager is botched up as it appears to not permit management of the eth1 connection and (unless I'm botching something up in the setup) when I do setup something 'it don't work'. 

Question: possibly a pathway is to un-install the network manager and simply edit the conf files for this functionality in the console. Of course I'm assuming there are a set of conf files with are behind the functionality of the NetworkManager.

---

### Post by dlmarti on 2009-07-20
can you open the network manager, and create a profile (add) with the settings we used here?

---

### Post by martinbaselier on 2009-07-20
The networkmanager does not use /etc/network/interfaces ( since ubuntu 8.10 I believe ). So you could uninstall it and use these settings instead.

---

### Post by ghettocounsler on 2009-07-20
I have tried to create a 'profile' for a wired connection with these attributes:
> 
address - i used 192.168.2.75
prefix - I don't know what to put in there so I left it blank
gateway - I used 192.168.2.1
DNS servers: I used 192.168.2.1 again but not sure this is correct although in the /etc/resolv.conf if this IP is not noted as a nameserver nothing works so perhaps this is correct.
 
and did a /etc/init.d/network restart as well but no luck

The biggest problem I'm noting is that using the Network Manager it seems difficult (I'd say impossible if I did not question my level of experience) to 'tell' if what is noted in the GUi is actually getting into a .conf somewhere.

---

### Post by dlmarti on 2009-07-20
What did ifconfig say, once you did the restart?
The prefix is probably going to be either "24" or 192.168.2.0 depending on the context (still not sure which tool your using).

---

### Post by dlmarti on 2009-07-20
If you just want to skip the graphical network setup check out this: [http://kubuntuforums.net/forums/index.php?topic=3100052.0](http://kubuntuforums.net/forums/index.php?topic=3100052.0)

Sorry, I'm not more familiar with KDE or I would be of more help.

---

### Post by ghettocounsler on 2009-07-21
ok, creating a profile in the Network Manager with noted attributes and prefix of '24' and this now does work, e.g. this newly configured connection does work from network manager GUi.

---

### Post by dlmarti on 2009-07-21
> **ghettocounsler said:**
> ok, creating a profile in the Network Manager with noted attributes and prefix of '24' and this now does work, e.g. this newly configured connection does work from network manager GUi.

sweet!, so all is good?

---

### Post by ghettocounsler on 2009-07-22
Yep, at the moment this is good, thanks heaps for all your help!

I still may go the route of removing all the GUi garb and go for config files only as at least then I know what is and is not working. (personal preference really)

---

### Post by dlmarti on 2009-07-22
> **ghettocounsler said:**
> Yep, at the moment this is good, thanks heaps for all your help!

I still may go the route of removing all the GUi garb and go for config files only as at least then I know what is and is not working. (personal preference really)

I'm the same.

---

