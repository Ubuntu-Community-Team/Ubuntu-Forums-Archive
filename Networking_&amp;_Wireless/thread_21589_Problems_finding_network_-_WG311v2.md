---
title: "Problems finding network - WG311v2"
date: 2005-03-23
forum: Networking &amp; Wireless
---

### Post by rt702 on 2005-03-23
Hi,

First off, I'm new to Ubuntu and linux in general, so bear with me on this.  I just installed Hoary Preview Release and while most everything went smoothly, my wireless adapter (Netgear WG311v2) is seemingly not able to get a connection.  DHCP fails and when running iwconfig, my access point comes up 00:00:00:00:00:00.  I am able to get an ip via DHCP and connect to the web with my wired net adapter, so it doesn't appear to be a DHCP problem.  

In System->Administration->Networking, I see a Wireless Connection - The interface wlan0 is active along with my active ethernet connection....the details under properties are jut the essid i last tried and configuration set to dhcp.....I have all wireless security turned off on the router and am able to successfully connect via my powerbook.  During the installation period, I breifly saw the MAC address appear on my clients list, but not once since then.  The card works perfectly in my WinXP box on the same network.  

I'm not really sure what other information you guys/gals need for a better diagnosis, so just let me know. 

iwconfig results (note i have the ssid set to 'test' currently on my router...my old ssid had a space in it, and I was worried that was the problem...no dice on that, though)

wlan0     IEEE 802.11g/b+  ESSID:"test"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:44/100  Signal level:21/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Router is a linksys...set to mix (b/g), channel 6, ssid='test', broadcast ssid

Thanks in advance,

Ryan

---

### Post by bobmitch on 2005-03-23
I have the same pci wireless nic - but haven`t had a problem with it at all since hoary array 4.

Did you select your wireless as the primary network point during the hoary install?
I did this and used dhcp - no problems at all.  Please note that I do not use and hence have not configured my on-board ethernet  - so I think that your wired nic may have something to do with the problem.

Is your default gateway set to 192.168.0.1?
Can you ping this ip address (without using cat5)?

---

### Post by rt702 on 2005-03-23
With the ethernet cable disconnected (and with the the ethernet device showing as not enabled), I can not ping.  I get an error connceting message.  It just seems like I can't get connected to the wireless signal for whatever reason.

---

### Post by bobmitch on 2005-03-23
Would I be correct in assuming you have had this working before in Windows?

---

### Post by rt702 on 2005-03-23
Yes, it worked great.  When I get home from work, I'm going to pull it and try it once more in the windows box to confirm it didn't get damaged along the way.

---

### Post by big-jimmy on 2005-05-08
Hello mate, have you found any solution to this?

I've exactly the same problem wg311v2 with texas chipset, scanning for wireless networks finds my router (netgear wg834g), the router sees the MAC address and I've added it to the access list. 

But bringing up  wlan0 gives:

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:09:5b:bf:24:25
Sending on   LPF/wlan0/00:09:5b:bf:24:25
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
...

have tried disabling WEP with no luck .. also tried static ip but still no luck .. I'm using ndiswrapper - is there any other drivers to try? All works under winXP fine .. 

many thanks in advance for any help.

---

### Post by bobmitch on 2005-05-09
[QUOTE=big-jimmy]


have tried disabling WEP with no luck .. also tried static ip but still no luck .. I'm using ndiswrapper - is there any other drivers to try? All works under winXP fine .. 

many thanks in advance for any help.[/QUOTE]

If you haven`t already, upgrade to Hoary - you shouldn`t need ndiswrapper for wireless to work, as the (not quite perfect, but better than ndiswrapper) texas instruments wireless chipset drivers are already in a kernel module.

---

### Post by big-jimmy on 2005-05-09
Thanks ... I'm already using Hoary .. does the kernel module get loaded by default, if not how do I go about loading it? 

I've found installing driverloader with the winxp drivers works, but I'm guessing isn't quite stable as linux completely froze a few hours after install, which has never happened to me before.

---

### Post by bobmitch on 2005-05-10
[QUOTE=big-jimmy]Thanks ... I'm already using Hoary .. does the kernel module get loaded by default, if not how do I go about loading it? 

I've found installing driverloader with the winxp drivers works, but I'm guessing isn't quite stable as linux completely froze a few hours after install, which has never happened to me before.[/QUOTE]

If it detects the hardware, the driver will be loaded.  Never had to change config or anything myself - it just works.

Am I correct in assuming you have the pci version, not the usb?

---

### Post by stevenyu on 2005-05-19
Ok here I go, here are the procedure I took for my TI based Netgear WG311v2 NIC with ndiswrapper
 
 0 - **What you need?**
 
 The latest windows driver for your wifi card (for my Netgear WG311v2, I didn't use the latest as the new one have a 3rd party software based wpa driver, so i used - [WG311v2 Beta Software Version 1.2]("http://http//kbserver.netgear.com/support_details.asp?dnldID=848") )
 
 The latest source of Ndiswrapper - [NDISWRAPPER]("http://ndiswrapper.sourceforge.net/") 
 You can use the source that came with Hoary, but I prefer getting the latest source myself.
 
 1 - **Install Ubuntu Hoary**
 
 2 - **Install the GNU C Compiler**
 
 Once you got in to the X-Window, fire up the Synaptic and install the following programs:
 
 **gcc**
 **g++**
 **Kernal Header** (use uname -a to find out which kernal you are running)
 **ndiswrapper source** (or you can use the one you downloaded from sourceforge, I prefer this method, )
 
 3 - **Remove the god damn ACX Driver**
 
 go to */lib/modules/**kernelversion**/kernel/drivers/net/wireless*
 
 and *mv acx /root/* follow by *depmod -a*
 
 NOTE: ***kernelversion*** will be difference as kernel version are different for everyone, depend on your CPU type.
 
 4 - **Unpack the source and driver man**
 
 Just right click on the files and extract to where you want it to, for me I just do extract to my home folder.
 
 5 - **Installing ndiswrapper**
 
 goto the directory holding your ndiswrapper, and
 
 *sudo make install*
 
 then goto the directory holidng your WiFi NIC driver, and
 
 *sudo ndiswrapper -i YOURWIFI.INF*
 
 and check the installation by *sudo ndiswrapper -l* ,and you should see something similar to this:
 
 > Installed ndis drivers:
 wg311v2 driver present, hardware present
 
 6 - **Auto load Ndiswrapper when reboot**
 
 *sudo ndiwrapper -m*
 
 7 - **Edit the network interface file**
 
 the file is located in */etc/network* and here is my configuration for static IP.
 
 > # This file describes the network interfaces available on your system
 # and how to activate them. For more information, see interfaces(5).
 
 # The loopback network interface
 auto lo
 iface lo inet loopback
 
 # This is a list of hotpluggable network interfaces.
 # They will be activated automatically by the hotplug subsystem.
 mapping hotplug
     script grep
     map wlan0
 
 # The primary network interface
 iface wlan0 inet static
     # wireless-* options are implemented by the wireless-tools package
     wireless_keymode open
     wireless_key REPLACE WITH YOUR WEP KEY
     wireless_mode managed
     wireless_essid REPLACE WITH YOUR ESSID
     wireless_nick REPLACE WITH YOUR HOST NAME
     address 192.168.1.3
     netmask 255.255.255.0
     network 192.168.1.0
     broadcast 192.168.1.255
     gateway 192.168.1.254
     # dns-* options are implemented by the resolvconf package, if installed
     dns-nameservers 192.168.1.254
 
 auto wlan0
 
 
 8 - **That all**  \\:D/

---

### Post by ssck on 2005-05-20
[QUOTE=stevenyu]Ok here I go, here are the procedure I took for my TI based Netgear WG311v2 NIC with ndiswrapper
 
 0 - **What you need?**
 
 The latest windows driver for your wifi card (for my Netgear WG311v2, I didn't use the latest as the new one have a 3rd party software based wpa driver, so i used - [WG311v2 Beta Software Version 1.2]("http://http//kbserver.netgear.com/support_details.asp?dnldID=848") )
 
 The latest source of Ndiswrapper - [NDISWRAPPER]("http://ndiswrapper.sourceforge.net/") 
 You can use the source that came with Hoary, but I prefer getting the latest source myself.
 
 1 - **Install Ubuntu Hoary**
 
 2 - **Install the GNU C Compiler**
 
 Once you got in to the X-Window, fire up the Synaptic and install the following programs:
 
 **gcc**
 **g++**
 **Kernal Header** (use uname -a to find out which kernal you are running)
 **ndiswrapper source** (or you can use the one you downloaded from sourceforge, I prefer this method, )
 
 3 - **Remove the god damn ACX Driver**
 
 go to */lib/modules/**kernelversion**/kernel/drivers/net/wireless*
 
 and *mv acx /root/* follow by *depmod -a*
 
 NOTE: ***kernelversion*** will be difference as kernel version are different for everyone, depend on your CPU type.
 
 4 - **Unpack the source and driver man**
 
 Just right click on the files and extract to where you want it to, for me I just do extract to my home folder.
 
 5 - **Installing ndiswrapper**
 
 goto the directory holding your ndiswrapper, and
 
 *sudo make install*
 
 then goto the directory holidng your WiFi NIC driver, and
 
 *sudo ndiswrapper -i YOURWIFI.INF*
 
 and check the installation by *sudo ndiswrapper -l* ,and you should see something similar to this:
 
 
 
 6 - **Auto load Ndiswrapper when reboot**
 
 *sudo ndiwrapper -m*
 
 7 - **Edit the network interface file**
 
 the file is located in */etc/network* and here is my configuration for static IP.
 
 
 
 8 - **That all**  \\:D/[/QUOTE]

sorry for barging in .... i really need help

no matter what i have tried, i just don't seem to be able to get the essid when i type iwconfig

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

just how do i get this information in ? 

even when i put in the ip address, and gateway, i am not able to ping the gateway.

in ifconfig,

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:9B:C5:13
          inet addr:192.168.2.239  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe9b:c513/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:e0203000-e02037ff

how do i solve it so that it is able to get thru ?

---

### Post by stevenyu on 2005-05-20
just how do i get this information in ? 

double check you **interface** file under /etc/network

I found out that WG311v2 doesn't like any essid if you haven't put in the keymode as open, and the key in before you assign the essid to the card.

also make sure the acx driver is move to somewhere else, otherwise you can't get it working too

---

### Post by ssck on 2005-05-21
[QUOTE=stevenyu]just how do i get this information in ? 

double check you **interface** file under /etc/network

I found out that WG311v2 doesn't like any essid if you haven't put in the keymode as open, and the key in before you assign the essid to the card.

also make sure the acx driver is move to somewhere else, otherwise you can't get it working too[/QUOTE]


hi thanks for helping.

these are my settings in the interfaces file :

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

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
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1


iface wlan0 inet static
wireless_keymode open
wireless_mode managed
#wireless_nick REPLACE WITH YOUR HOST NAME
address 192.168.2.239
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 202.188.0.133
wireless-essid Hex3
wireless-key open

auto wlan0


auto eth0

the problem is in the iwconfig file, the essid is not updated.when i try to update it manually, it doesn't work.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

in the ifconfig file, these are my settings :

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:81:A4:4F
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe81:a44f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1157316 (1.1 MiB)  TX bytes:205930 (201.1 KiB)
          Interrupt:6

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1117546 (1.0 MiB)  TX bytes:1117546 (1.0 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:9B:C5:13
          inet addr:192.168.2.239  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe9b:c513/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:e0203000-e02037ff


i am really not sure what is the problem.the card and router definitely works in win xp.what else can i do ? 

appreciate all the help i can get.

---

### Post by ssck on 2005-05-21
tried updating the essid into the iwconfig using the iwconfig command.it doesn't get updated.

how can i get it updated ?

---

### Post by stevenyu on 2005-05-21
ok, give this one a try:

 >  # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

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
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1
 auto eth0

iface wlan0 inet static
wireless_keymode open
wireless_key open
wireless_mode managed
wireless_essid Hex3
address 192.168.2.239
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 202.188.0.133

auto wlan0 

Make sure you type in the right essid and the WEP key!!!

and Make sure the ACX driver have been removed

---

### Post by ssck on 2005-05-21
hi stevenyu,

thanks for your help.i put in th suggestions for the interfaces file and disabled the wired lan (eth0) and enabled the wireless (wlan0).i rebooted the laptop and now it is running OK.

appreciate your help.

regards.

---

### Post by Joe on 2005-05-21
Thanks Stevenyu for the great post.  I've been trying to figure out how to get my card to pick up an ip address for the past month with ndiswrapper.  I guess I should have tried deleting the acx driver before.

---

