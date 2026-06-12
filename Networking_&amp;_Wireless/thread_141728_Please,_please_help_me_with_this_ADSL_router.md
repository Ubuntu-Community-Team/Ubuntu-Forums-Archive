---
title: "Please, please help me with this ADSL router"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by janhenderson on 2006-03-08
Hi. I've been trying to search these forums and read about setting up ubuntu to work with my new ADSL router without success. Windows XP works perfectly with it, and so does SLAX livecd (SLAX just detected everything automatically without any intervention from me and I can browse the net and all, just not ubuntu). I'm becoming frustrated. I'd much appreciate any help I can get, just please don't point me to material I may have already tried. I would be very grateful if someone could just go through it with me step by step. 

My ISP is AOL UK. The new ADSL router is this one [http://safecom.cn/code/sub/category.asp?prdid=184&subcatid=1](http://safecom.cn/code/sub/category.asp?prdid=184&subcatid=1) and I've updated the firmware to the latest on the site. 

When I do ipconfig /all in windows cmd this is some of the information I get 

Dhcp enabled : yes
autoconfiguration enabled : yes
IP address : 192.168.1.2
subnet mask : 255.255.255.0
default gateway : 192.168.1.1
dhcp server : 192.168.1.1
dns servers : 192.168.1.1


If I go into the LAN configuration in the ADSL router's setup, I find the following 
Use the following Static IP address
  	
	IP Address: 	192.168.1.1
	Netmask: 	255.255.255.0
	Default Gateway: 	81.145.240.1
	Host Name: 	mygateway1
	Domain: 	ar7

Enable DHCP Server
  	
 Start IP: 	192.168.1.2
 End IP: 	192.168.1.254
 Lease Time: 	3600


What should I do in Ubuntu to get it working right? should I tell it to use dhcp or static ip? will the host be mygateway1 as above or will it be the host name I gave to the computer when I installed ubuntu? should there be an address at the DNS tab or should I leave it blank? I can ping the router, but I can't ping the internet neither by number or name. 

Many, many thanks, and please help.

---

### Post by patsissons on 2006-03-09
from the data you have from ipconfig, it looks like you should tell it to use dhcp.  your hostname should be whatever you called your computer when you installed ubuntu, it should not have any effect on your internet settings.  dhcp should take care of your dns entries.    dhcp "should" do everything for you, however, you can always try and set up a static entry if you cannot get dhcp to work.

static setup:
ip: 192.168.1.X  X is any number from 2 to 254
netmask: 255.255.255.0
default gateway: 192.168.1.1
broadcast address: 192.168.1.255 (i don't think you need this, but in case you do, this is the correct number)
dns: 192.168.1.1

I am weary of your router's setup, your ip address should most likely be something like 81.145.240.X (again, where X is between 2 and 254).  Your router's address should not be a 192.x.x.x type entry, you would use 192.168.1.1 to ping your router, but its actual ip should be something else.  If you are unsure of what this ip should be, I recommend contacting your isp and asking them about it.

---

### Post by mips on 2006-03-09
[QUOTE=patsissons]I am weary of your router's setup, your ip address should most likely be something like 81.145.240.X (again, where X is between 2 and 254).  Your router's address should not be a 192.x.x.x type entry, you would use 192.168.1.1 to ping your router, but its actual ip should be something else.  If you are unsure of what this ip should be, I recommend contacting your isp and asking them about it.[/QUOTE]

There is nothing wrong with the router config. 81.145.240.1 refers to the WAN(adsl) side and the 192.168.1.1 is the IP address configured on the routers LAN port.

---

### Post by janhenderson on 2006-03-10
Thanks to those who replied. It's still not working. I put it on DHCP and it's still not going online. I really, really wish I could get Ubuntu to work (Slax did), but this is becoming frustrating. Does anyone know what other distro I can try that has as good a repository as ubuntu and as easy an installation? Thanks.

---

### Post by mips on 2006-03-10
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

At what point in the above guide do you get stuck ???

---

### Post by janhenderson on 2006-03-10
I can ping the router, but I can't ping the internet, neither number or name. 

Could it be an MTU problem? I'm on AOL and on windows it needed to be MTU 1400 to work correctly. I'm considering doing this [http://www.ubuntuforums.org/archive/index.php/t-82093.html](http://www.ubuntuforums.org/archive/index.php/t-82093.html)

But then why did Slax manage to connect automatically with no problem?

---

### Post by manicka on 2006-03-10
My suggestion would be to manually setup your machine and not use dhcp. The dns address should be changed from 192.168.0.1 to that of your providers dns server as your router may not be handling dns properly. This is what I have to do with my d-link router.

---

### Post by mips on 2006-03-11
1. Please disable IPv6 and reboot:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```
2. Please post output of **ifconfig eth1**
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**
7. Please copy **entire** output of windows **ipconfig /all** command here

I suspect you lack a default route and need to configure your DNS settings manually.

---

### Post by janhenderson on 2006-03-12
Hi there, mips and others. The command you told me to use to disable IPv6 seems to have done the trick, I couldn't get online before I applied it, once I did and rebooted I could. I have also added an mtu 1400 to /etc/network/interfaces, and added the AOL DNS server to the GUI of networking.  I'm now connected and typing this from ubuntu. There remains one problem though. I can't get "sudo apt-get update" to work, and also, this may be related, when booting the synchronising to ntp.ubuntulinux.org fails. I have added repositories as per this page [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic). How can I fix this? Many, many thanks and regards. 

Here are what you asked me to do from ubuntu, and also the errors I get from "sudo apt-get update" 

sans@newmilk:~$ ifconfig eth1
eth1: error fetching interface information: Device not found

sans@newmilk:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:7F:40:1D
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4033135 (3.8 MiB)  TX bytes:1089327 (1.0 MiB)
          Interrupt:17

sans@newmilk:~$ lspci | grep Eth
0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
sans@newmilk:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

sans@newmilk:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 205.188.146.145

sans@newmilk:~$ cat /etc/network/interfaces
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
iface eth0 inet dhcp
        mtu 1400

auto eth0
sans@newmilk:~$




Windows IP Configuration





        Host Name . . . . . . . . . . . . : MAINLAND


        Primary Dns Suffix  . . . . . . . : 


        Node Type . . . . . . . . . . . . : Mixed


        IP Routing Enabled. . . . . . . . : No


        WINS Proxy Enabled. . . . . . . . : No





Ethernet adapter Bluetooth Network:





        Media State . . . . . . . . . . . : Media disconnected


        Description . . . . . . . . . . . : Bluetooth LAN Access Server Driver


        Physical Address. . . . . . . . . : 00-0A-3A-51-59-30





Ethernet adapter Local Area Connection:





        Connection-specific DNS Suffix  . : 


        Description . . . . . . . . . . . : Marvell Yukon Gigabit Ethernet 10/100/1000Base-T Adapter, Copper RJ-45


        Physical Address. . . . . . . . . : 00-0E-A6-7F-40-1D


        Dhcp Enabled. . . . . . . . . . . : Yes


        Autoconfiguration Enabled . . . . : Yes


        IP Address. . . . . . . . . . . . : 192.168.1.2


        Subnet Mask . . . . . . . . . . . : 255.255.255.0


        Default Gateway . . . . . . . . . : 192.168.1.1


        DHCP Server . . . . . . . . . . . : 192.168.1.1


        DNS Servers . . . . . . . . . . . : 205.188.146.145


                                            192.168.1.1


        Lease Obtained. . . . . . . . . . : 12 March 2006 21:58:33


        Lease Expires . . . . . . . . . . : 12 March 2006 22:58:33



Here's what happens when I try to update: 

sans@newmilk:~$ cat /etc/apt/sources.list
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

 sans@newmilk:~$ sudo apt-get update
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://uk.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outReading package lists... Done
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mips on 2006-03-13
Could I suggest you swap the order of DNS servers around. Your ISP should also have more than one DNS server which I recommend you add.

You can manually edit your sources list with
```
sudo gedit /etc/apt/sources.list
```
If you have kubuntu use 'kate' instead of 'gedit'

I have seen your problem with the sources list before, just cannot remember the solution. Will have a look into it but hopefully someone else here remembers it and points you in the right direction in the meantime.

---

### Post by manicka on 2006-03-13
Try taking the uk bit off from each the repos and just use the main repos e.g. archive.ubuntu.com

---

### Post by elithrar on 2006-03-13
Make sure Ubuntu recognises the correct DNS server; sometimes you'll find it using the loopback address (or some other random address) as the DNS server. Which means you can ping your router, but can't connect to the Internet through it. Grab your ISP's DNS address from Windows or from the modems' interface itself, and...

```

sudo gedit /etc/dhcp3/dhclient.conf

```

Head there, scroll down to:
```

prepend domain-name-servers

```

and change the DNS address to match the correct one.

hth.

---

### Post by bakert on 2006-04-02
Yes, yes, yes!!!  elithrar thank you SO much.  I have been trying to fix this problem for two weeks!

---

