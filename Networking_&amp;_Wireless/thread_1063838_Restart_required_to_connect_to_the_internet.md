---
title: "Restart required to connect to the internet"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by EcoNico on 2009-02-08
Dear all,

For some reasons, ubuntu 8.04 2.6.24-23-generic does not allow me to directly connect to the internet after I start my computer.
I am always obliged to restart my PC to obtain the connection.

Here is what ifconfig returns when the connection is unavailable:

--------------------------------

eth0      Link encap:Ethernet  HWaddr 00:00:6c:ad:b4:f1  
          adr inet6: fe80::200:6cff:fead:b4f1/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:23195 (22.6 KB)
          Interruption:220 Adresse de base:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:00:6c:ad:b4:f1  
          inet adr:169.254.10.101  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:220 Adresse de base:0x8000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1774 erreurs:0 :0 overruns:0 frame:0
          TX packets:1774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:88976 (86.8 KB) Octets transmis:88976 (86.8 KB)


--------------------------------




And here is what I get when the connection is back on, after a restart:


--------------------------------

eth0      Link encap:Ethernet  HWaddr 00:00:6c:c6:f7:e5  
          inet adr:192.168.1.24  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::200:6cff:fec6:f7e5/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:7918 erreurs:0 :0 overruns:0 frame:0
          TX packets:6594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:9388092 (8.9 MB) Octets transmis:958609 (936.1 KB)
          Interruption:220 Adresse de base:0x8000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1624 erreurs:0 :0 overruns:0 frame:0
          TX packets:1624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:81200 (79.2 KB) Octets transmis:81200 (79.2 KB)

--------------------------------



I verified the "interfaces" file as well as the "70-persistent-net.rules" Everything looks normal to me.

Could someone give me a hint?
I would greatly appreciate it.
thanks

---

### Post by FishRCynic on 2009-02-08
network manager running?
if so
before rebooting does disabling and re-enabling the 
wired network get you linked to the network.
(dhcp does not seem to be activated 1st time round)

---

### Post by EcoNico on 2009-02-08
yes, Network manager was running. Disabling and re-enabling it does not work.

**One thing I had not mentioned: this only happens when I unplugged the PC power cord from the power outlet, and therefore cut some kind of stanby link between the PC Ethernet port and the Modem/router..**

---

### Post by FishRCynic on 2009-02-08
what happens when you unplug the ethernet cable (before rebooting) from the pc and then plug it back in?

---

### Post by EcoNico on 2009-02-08
Steps detailed:

1) with the internet working, I unplugged the Ethernet cable from the Modem/Router

2) I rebooted

3) After logging in, I plugged the Ethernet cable back to the Modem/Router

4) I checked --> NO internet connection ; ifconfig does not display any inet address looking like 192.168....

---

### Post by superprash2003 on 2009-02-08
how about typing **sudo dhclient eth0** in the terminal

---

### Post by EcoNico on 2009-02-08
**sudo dhclient eth0** does work when only the Ethernet cable is unplugged and plugged back after reboot as describd in post #5, **HOWEVER**it does **NOT**work when I switch the computer OFF, unplugged the power cord from the power outlet, wait a bit and eventually re-plugg and re-start everything. :-(

---

### Post by FishRCynic on 2009-02-08
ok try

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

after startup

---

### Post by EcoNico on 2009-02-08
Here is what I got:


**_1) NETWORKING STOP_**

nicole@nicole-desktop:~$ sudo /etc/init.d/networking stop

* Deconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
   ...done.
 * Starting the Firestarter firewall...
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
There is already a pid file /var/run/dhclient.eth0.pid with pid 5959
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:00:6c:6f:51:df
Sending on   LPF/eth0/00:00:6c:6f:51:df
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
                                                                         [ OK ]


**_2) NETWORKING START_**

nicole@nicole-desktop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:00:6c:6f:51:df
Sending on   LPF/eth0/00:00:6c:6f:51:df
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Stopping the Firestarter firewall...
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
   ...done.
 * Starting the Firestarter firewall...
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
eth15: error fetching interface information: Device not found
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2

---

### Post by FishRCynic on 2009-02-08
open port 67 on your firewall and see what happens

allow dhcp service in firewall should work too

---

### Post by EcoNico on 2009-02-08
Well, it was not obvious to set up my firewall to have port 67 opened, I therefore decided to uninstall the firewall for now...
Unfortunately, nothing new, I still cannot access the net without rebooting..

---

### Post by FishRCynic on 2009-02-08
can you post your /etc/network/interfaces?

---

### Post by EcoNico on 2009-02-09
**_From gedit /etc/network/interfaces_**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

---

### Post by FishRCynic on 2009-02-09
> **EcoNico said:**
> **_From gedit /etc/network/interfaces_**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp



-----------------------------------------------------


using intrepid / hardy ?

comment out

#iface eth0 inet dhcp

or delete it

and reboot 

avahi is supposed to figure this all out without help

(at least so far it does here)

---

### Post by EcoNico on 2009-02-10
I am using:

**cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"


I tried but same thing..I ended up reinstalling the OS, thinking something had gone wrong during the first install, but still the same..


Here is some more **ifconfig** info completed with the result of **netstat -rn**
_*Note *_that I uninstall avahi-autoipd and made sure /etc/network/interfaces was taking into account the dhcp server



**_WHEN IT WORKS _**


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:6c:40:87:66  
          inet adr:192.168.1.27  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::200:6cff:fe40:8766/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2773 erreurs:0 :0 overruns:0 frame:0
          TX packets:3199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2209995 (2.1 MB) Octets transmis:655552 (640.1 KB)
          Interruption:220 Adresse de base:0x6000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1942 erreurs:0 :0 overruns:0 frame:0
          TX packets:1942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:97100 (94.8 KB) Octets transmis:97100 (94.8 KB)

nicole@nicole-desktop:~$ netstat -rn
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic   MSS Fenêtre irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0



[B][U]
AFTER COMPUTER SWITCHED OFF AND POWER CORD UNPLUGGED ---- THEN COMPUTER POWER CORD PLUGGED BACK AND COMPUTER RESTARTED[/U][/B]


ifconfig
eth1      Link encap:Ethernet  HWaddr 00:00:6c:4c:ad:08  
          adr inet6: fe80::200:6cff:fe4c:ad08/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:2222 (2.1 KB)
          Interruption:220 Adresse de base:0x8000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1602 erreurs:0 :0 overruns:0 frame:0
          TX packets:1602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:80100 (78.2 KB) Octets transmis:80100 (78.2 KB)

nicole@nicole-desktop:~$ netstat -rn
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic   MSS Fenêtre irtt Iface




Note that when I restart the computer, the LEDs of the router/modem turn ON, which should mean the Ethernet card from the mother board and the router somehow speak together, right ??
If it is the case, knowing there is no firewall, and that I have not messed around with the ports (yet), what is stopping the router / Ethernet card to continue communicating after a very first start?

---

### Post by superprash2003 on 2009-02-10
@econico
 why not it should work?? dhclient requests the router for an ip..

---

### Post by EcoNico on 2009-02-10
using **sudo dhclient eth0** indeed works, but only when I cut the network connection by unplugging the cable from the router and then plugging back in.

_The problem occurs when I stop the computer and unplugg the power cable from the power outlet._

On the other hand, whenever I use the computer with the internet connection OK and I switch it off _without_ unplugging the power cord from the power outlet, I can see the LEDs of the router close to the Ethernet cable still being lit; in that case, I can start ubuntu and get internet directly.. 

Could you please tell me if there is an Ethernet card driver I need?
Is there an extra port I need to force open at start up?

---

### Post by FishRCynic on 2009-02-10
/what is the network card name/version &/or chipset

when you first boot does it show up in lspci?

---

### Post by EcoNico on 2009-02-11
Here is the info I get for the network controller integrated on the mother board, after a **lspci -v**


00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASRock Incorporation 939NF6G-VSTA Board
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e480 [size=8]
	Capabilities: <access denied>


_*Note:*_I reinstalled avahi-autoipd

---

### Post by FishRCynic on 2009-02-11
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	I/O ports at c000 [size=256]
	Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

the above is a partial from this laptop as an example from lspci -v


there should be some "network" controller listed like above
containing something of Realtek PHY RTL8201CL

when you first boot do you get an ethernet controller listed similar to above?

when you reboot does it magically appear in lspci -v?

you can try enabling Pci power on in your bios.
(under ADVANCED setting ACPI

---

### Post by EcoNico on 2009-02-12
I only get what I posted in #19, having the internet connection available or not...

I checked what you proposed but it did not do the trick. The mother board network card is working but the communication after a first boot <=> AFTER COMPUTER SWITCHED OFF AND POWER CORD UNPLUGGED ---- THEN COMPUTER POWER CORD PLUGGED BACK AND COMPUTER RESTARTED is still not coming up.


I mentioned  in #17 that my modem was not the cause; well, I am not so sure any more.. I will try to see if something in the modem/router seems wrong..
Oherwise, what about IPv4 or IPv6, do you think there could be something hidden there?

---

### Post by EcoNico on 2009-02-12
I also tried to install **wicd **instead of **network manager** to see => result: no improvements..


_I nevertheless noticed something which I think should not be:_
The **Hardware address** (example from ifconfig: Ethernet HWaddr 00:00:6c:4c:ad:08 )**of the ****Ethernet controller (I suppose) is changing** all the time!!?? I don't think that is normal? Do you know a trick to set it up for good?

---

### Post by FishRCynic on 2009-02-12
it appears it is the mcp61 - and it appears to be a buggy chipset

[http://nixcraft.com/linux-hardware/7815-mcp61-firewall.html](http://nixcraft.com/linux-hardware/7815-mcp61-firewall.html)
doesn't look like he got it fixed
if you dual boot to xp - you might try disabling activearmor 

"To disable ActiveArmor….

Start->All Programs->NVIDIA Corporation->Network Access Manager->Web-based Interface->ActiveArmor->Select Disabled and apply."

if in your bios there is a place to set the mac address for the 
onboard nic set it (i didn't see one in the mb manual though)

you could try noapic or acpi=off on your boot line and see if it helps
or combination of various boot options

*******************
(if you have another pci nic not nvidia - disable the onboard lan and install & use the pci nic)

---

### Post by sleve on 2009-02-12
ive been having the same issue and ive posted in some other threads about this. my drivers are up to date. my windows connects correctly. its only when i Shut Off ( not Restart ) my pc and take the cord out hit the power to clear any power left Replug the power cord to my pc in and restart that i am able to connect. 

i have green lights on my router and when the cord is plugged in and no connection. im assuming this is a bug and will wait for a fix.

---

### Post by EcoNico on 2009-02-13
@sleve:  Sorry I missed your thread..Thanks for the feedback..It is good in a way to know I am not the only one to carry this burden ;-)


@FishRCynic: It is a bummer!  Well, **thanks anyway; I really appreciate your help and time on this issue**. As you suggested, as a quick solution, I will try to get a nic somewhere and use it instead. 
_Meanwhile, do you know where this bug (or annoying behavior) can be listed in order to have Ubuntu developers find a workaround?_

---

### Post by FishRCynic on 2009-02-13
this really isn't a bug but an improper implementation by nvidia on their nic.  However filing a bug may lead to someone giving you a workaround that will render the nic at least usable 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

and in people speak :-0

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

there is possibly a bug report(s) on this already as it has been an issue 
for both windows and linux since the chipset was released.
(i didn't see one specifically for this but i didn't look at all of them)

[https://launchpad.net/](https://launchpad.net/)

---

### Post by EcoNico on 2009-02-14
Thanks for the info!!

-------------------------------

FYI:
I decided to buy a Netgear FA311 Ethernet PCI card.
I just plugged it in, restarted and it worked and has still been working perfectly fine!

---

