---
title: "Cannot enable interface (wireless network device) with kcontrol"
date: 2005-12-23
forum: Networking &amp; Wireless
---

### Post by Grugs on 2005-12-23
Newbie to kubuntu and wireless networking.

Opened kcontrol with kdesu kcontrol command.  Selected Internet & Network > Network Settings.  On the Network Interfaces tabs, two interfaces are listed (I have two PCMCIA NICs plugged in, one wired, one wireless).  The wired one is enabled.  Great.  The wireless one is not.   Hmmmm.

I select the wireless interface and click on Enable Interface: it momentarily says it is enabled, then flips back to being disabled.

I disable the wired interface, then select the wireless interface, click on Enable Interface.  Same phenomenon.

How can I enable the wireless card?

Here my specs and configurations:

Card: Intel Wireless PRO/Wirelss 2011 Lan PC Card, model WPC2011NA.

grugs@ubuntu:~$ cat /etc/network/interfaces 
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth1

grugs@ubuntu:~$ iwconfig eth0
eth0      IEEE 802.11-DS  ESSID:""  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:16   RTS thr:off   Fragment thr=0 B   
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have noticed that the ESSID value is "".  I have tried to change this to "any" with the following command: 

sudo iwconfig eth0 essid any

But when I then re-execute the iwconfig eth0 command, the ESSID value remains "".

In kcontrol, I can configure the wireless card and therein set the ESSID to any, but that makes no difference - I still cannot enable it.


ifdown and ifup ?  No.

grugs@ubuntu:~$ sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 6607
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:02:b3:04:5d:d5
Sending on   LPF/eth0/00:02:b3:04:5d:d5
Sending on   Socket/fallback


grugs@ubuntu:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:02:b3:04:5d:d5
Sending on   LPF/eth0/00:02:b3:04:5d:d5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Working leases?  Persistent database - sleeping ?  (Wake up!)

Can a wireless card be enabled from kcontrol only if a network can be found (or DHCPOFFERS are received)?  I would think that I should be able to enable the card regardless of the presence of a wireless network.  (Even so, my windows xp machine is able to find three networks from the same physical location.)

Driver installed?

I have considered that perhaps an appropriate driver is not installed.  But my 4-day-old kubunto 5.10 installation includes a file at /usr/share/doc/pcmcia-cs/SUPPORTED.CARDS.gz which lists "Intel PRO/Wireless 2011" so I assume the driver is installed.  (I have also read that the WPC2011 card is supported by the wavelan (or orinoco or orinoko or pcmcia-cs) driver (or package) and not by ndiswrapper.

acpi?  Removed.

I read in another ubuntu forum that the case of the only-for-a-moment enabled interface in kcontrol is due to the presence of acpi power management, and the problem can be resolved by disabling this with acpi=off in the lilo.conf file -- but my kubuntu installation doesn't even have a lilo.conf file (because I have no other OS installed on this machine, I guess).  I did find, though, that acpi is included with the klaptop package and so, in order to ensure acpi was disabled, I removed the klaptop package completely.  But still the wireless card cannot be enabled.

I have read the [https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto) but it seems to be directed to the gnome ubuntu, not the kde kunbuntu, hence my post here.

wireless-tools package installed?  Yes, it is.

How can I enable this wireless network interface card device thing ?

---

### Post by gurlyburlyman on 2006-04-03
I was having a similar problem and the posting on this site: [http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=14487&start=10]("http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=14487&start=10")
worked for me.

Here's what I did:

   sudo ifconfig wlan0 up
   sudo ifup wlan0

This enabled the interface, but for some reason I still couldn't connect. So the next suggestion on the link above is:

   sudo ifdown wlan0
   sudo ifconfig wlan0 up
   sudo ifup wlan0
   sudo pump -i wlan0

The 'pump' command isn't on my computer, but the first three commands apparently did the trick. After rebooting I can just use the "sudo ifup wlan0" and that seems to do the trick.

---

