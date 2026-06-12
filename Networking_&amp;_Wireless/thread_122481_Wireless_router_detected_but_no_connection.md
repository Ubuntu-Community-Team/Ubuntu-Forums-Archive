---
title: "Wireless router detected but no connection?"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by kix on 2006-01-27
I've read a lot through the wireless problems on the forums, but can't find anything related to what I have here.

My hardware is Acer Travelmate 8003LMi, with the Intel Centrino 2200 chipset.

Problem I have is only slightly annoying and probably easy to fix, Ubuntu (live 5.10) detects my wireless network and I select the network from the network config menu, enter the WEP key and enable the eth1 nic, but still no connection.

So, the network is there, listed, but not enabled, and will not enable.

Not sure if anyone is familiar with the Acer laptops, there is a wireless LED and button at the front of the mouse pad, this is normaly lit during wireless use in WXP, but never lights when running Ubuntu (or any other Live CD).  It is used to switch wireless on and off.

Any pointers to how to get Ubuntu and my wireless router talking?  Is it a driver or config issue?

Thanks

---

### Post by Lambert on 2006-01-28
From the terminal, 
Post the outpug of [I]iwconfig

[/I]and try to scan to see what you get

sudo iwlist eth1 scan

Didn't see an answer here but this might be a good link for you in general.

[http://nek0.net/linuxacer8000/](http://nek0.net/linuxacer8000/)

---

### Post by kix on 2006-01-28
Lambert, many thanks for the reply, and a very helpful link.

The results from your suggestions:

Network not configured
```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
Then with the wireless activated from the control panel, and eth1 set as default gateway.
```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Red"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:E2:67:4A:C1
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=77/100  Signal level=-52 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3

sit0      no wireless extensions.
```

And finally:

```
ubuntu@ubuntu:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:04:E2:67:4A:C1
                    ESSID:"Red"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rate:22 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 22
                    Quality=75/100  Signal level=-54 dBm
                    Extra: Last beacon: 2201ms ago
```

Are you able to point me to anything with those results?

Cheers

---

### Post by Lambert on 2006-01-28
Your device and driver look to be working ok because you can

1. scan and get results
2. get association with the router.

so some more info needed.

post output of command *ifconfig *and *arp -a*
also 
sudo lshw -C network
cat /etc/network/interfaces

You can xxx out all personal data
What kind of encryption are you using?

have you tried the command

sudo dhclient eth1

---

### Post by kix on 2006-01-28
Lambert, tried your suggestions, FYI I'm using 64 bit WEP encryption.
```

ubuntu@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:4A:71:AB
          inet6 addr: fe80::20e:35ff:fe4a:71ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:4296 (4.1 KiB)
          Interrupt:10 Base address:0xe000 Memory:d0214000-d0214fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1952 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:173616 (169.5 KiB)  TX bytes:173616 (169.5 KiB)

```
```

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5705 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:4b:58:ed
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.31 duplex=half link=no multicast=yes port=twisted pair
       resources: iomemory:d0200000-d020ffff irq:6
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:4a:71:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.0.6 firmware=ABG:9.0.1.5 (Oct 15 2004) link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:d0214000-d0214fff irq:10
```

```
ubuntu@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

iface eth1 inet dhcp
wireless-essid Red
wireless-key s:##########

auto eth1

```
```

ubuntu@ubuntu:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 23643
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:4a:71:ab
Sending on   LPF/eth1/00:0e:35:4a:71:ab
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

And, *arp -a* returns nothing.

Thanks again for your time.

---

### Post by Lambert on 2006-01-28
Ok, your dhcp server(router) is not accepting your request for a dhcp packet. Probably  because of a missing setting in your wep configuration so it can't authenticate your request.

For now I can say try this or maybe somebody else who uses ipw2200 will see this and know

in your /etc/network/interfaces file change the wireless key line to look like this

wireless-key restricted s:xxxxxx


add this line

wireless-mode managed

and not sure if this will hep but if after the above doesn't work try putting a - every 4 characters in your key.

wireless-key restricted s:xxxx-xxxx-xx

---

### Post by kix on 2006-01-30
Lambert, thanks again.  Tried your suggestions, even went the whole hog and installed Ubuntu.  Problem is still the same, DHCP does not seem to work over wireless, wired is fine.

Checked and then changed the WEP key, no joy, works XP and not on Ubuntu.

Any hope on getting this wireless going?

Thanks once more for your time and effort.

Stuck.

---

### Post by Lambert on 2006-01-30
Two more suggestions.

1. I gave you restricted. try changing the interfaces file to this.

wireless-key open s:xxxxx

If that doesn't work then 

2. try using a hexadecimal key instead of a passphrase.

---

### Post by mannu on 2006-01-31
Hi,

Try looking at this I had exactly the same problem and it is to do woth web encryption. For some reason I have to manually activate this from etc/network/interphase which isn;t a big deal but it does work (for me anyway),

i edited etc/network/interface file so it looks like this

This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
# auto eth0
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0


auto ra0

iface ra0 inet dhcp
wireless-essid <your ssid>
wireless-mode managed
wireless-key1 <your key don;t space them>
wireless-defaultkey1
wireless-keymode restricted
wireless-enc on
wireless-channel <your channel>
post-up iwconfig ra0 enc on


You will notice the importance the script places on identifying the key which you can obtain from your router (ispecifcially placed the encytion in key 1 rathert han passphrase),

Paul Mannu

---

### Post by kix on 2006-02-07
Lambert and mannu, many thanks for your time and effort.  Unfortunately, after trying to crack this problem for a long time, I never got anywhere.

This install was for the laptop only, as the missus likes the feel of Ubuntu and the freedom of wifi.  I've installed PCLinuxOS on the laptop (as I've had it installed on my desktop for nearly a year), and the wireless is working fine, without any configuration. 

:-D 

I'll probably give Ubuntu another try when I buy the missus her own laptop. ;) 

Cheers

kix

---

### Post by kix on 2006-02-13
Ok, so I said I gave up, but I decided to have another go.  Went for a static IP address, and it works.  I'm chuffed to bits.  So, I'll have a bit of a play around and see if I can get the DHCP to work.

:mrgreen:

---

