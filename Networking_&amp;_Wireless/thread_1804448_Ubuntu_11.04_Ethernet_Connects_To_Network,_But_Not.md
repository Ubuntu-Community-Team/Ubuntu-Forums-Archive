---
title: "Ubuntu 11.04 Ethernet Connects To Network, But Not To Internet"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by StephenP55M-UD2 on 2011-07-14
Alright well, I didn't want it to come down to this but i'm seriously stumped.....I am not really an Ubuntu user.  Had 9.10 on my old Compaq and tried on my Toshiba (Not supported :( ).  So guys my computer (Custom built, Specs listed below) will connect to my ethernet through my laptop, but it will not connect straight to the internet to browse.  Had a wireless card but older motherboard wouldn't support it so I trashed it (STUPID MISTAKE :( ) and now I cannot access the internet.  I've tried every Ubuntu I have in collection.  Kubuntu 9.10, Ubuntu 9.10, Ubuntu 10.04.2 LTS, Ubuntu 10.10, and now Ubuntu 11.04.  

I've disabled IPv6 with no avail.  The first time I installed Ubuntu 11.04 everything was fine.  No problems from the get go at all.  Internet worked, heck I downloaded maybe 50 brushes for gimp and the same/if not more text files.  I go to bed and wake up to find my computer on Windows 7.  Apparently updates were installed.....I get back into Ubuntu and thats where my problem comes in to play....Thanks for atleast looking/trying to solve my problem.  

Computer specs:
Gigabyte P55M-UD2
Intel Core i3-530 2.93ghz (Overclocked to 4.00ghz)
4gb OCZ DDR3 10700 RAM
Sony? DVD-Drive (Not to sure, don't think it matters anyway)
WD 500GB HDD

If you guys need anymore information feel free to ask!  Thank you!

**!!!EDIT!!!**

I think I may have a potential problem here.  I tried the command sudo lspci -v.  Now theres one interesting thing I have found here.  It detects my motherboard as a GA-EP45-DS5.  Judging by the "EP45" it is an older Intel socket.  A quick google search finds it to be the old 775 socket.  And my i3 is just detected as a "Intel Corporation Core Processor".  So I think this may be affecting my onboard LAN since they do not use the same chipset.  Gigabyte has no drivers for this motherboard for Ubuntu :(.  So I am completely clueless as what to do now.  I'm not worried performance-wise cause even without the correct drivers my CPU is more than capable enough to handle anything I throw at it.  But now I wonder if my ethernet will ever work again on Ubuntu??

**UPDATE**

Well, I am sorry I keep changing these things but schools out and searching myself for hours on end is how I always solved problems so I am uneasy resorting to this but I greatly appreciate it since I am completely lost....So I tried to install Ubuntu 10.04 LTS again (64-bit BTW) with no avail.  I have no clue if internet works on their because its always black when I boot into the installer, Live, or after I install it using wubi.  I reinstalled Ubuntu 11.04...now  I am back to where I was the first time.  The wired connection is connected everythings "looks" fine.  Motherboards still not detected right along with the card, and processor but oh well, I can deal.  I still cannot connect to the internet whatsoever AT ALL.  Its the 2 arrows left one is up, right one is down.  They are white.  Before it just looked like an ethernet port with a blue cable hooked into it.  Mann, I wish I could switch to 10.04 but I can't even boot into it to see anything so oh well......Thanks again.

---

### Post by StephenP55M-UD2 on 2011-07-14
Oh and btw, my Windows 7 partition has absolutely no problems at all with internet.  Just Ubuntu.....The laptop I am connecting through is a Toshiba (The one I couldn't get Ubuntu to work right on).  I switch the cable to my Xbox whenever I use it.  Any help will be appreciated....

---

### Post by papibe on 2011-07-14
Could you post the result of the following commands:
```
$ ifconfig
```
```
$ route -n
```
```
$ nslookup google.com
```
Regards.

---

### Post by StephenP55M-UD2 on 2011-07-14
Alright, Thanks for your reply.

Here are the results:


stephen@stephen-P55M-UD2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:d3:2e:d0  
          inet6 addr: fe80::224:1dff:fed3:2ed0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22584 (22.5 KB)  TX bytes:4934 (4.9 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9024 (9.0 KB)  TX bytes:9024 (9.0 KB)

stephen@stephen-P55M-UD2:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

stephen@stephen-P55M-UD2:~$ nslookup google.com
;; connection timed out; no servers could be reached

Now it seems for some reason after it went in to sleep, now it can't even connect to the network at all.  Problem seems to just keep getting worse? :confused:

**UPDATE**

After reinstalling I went ahead an entered those commands you asked for again, don't want you wasting your time with commands if we can fix the issue a different way.  Thanks again for all your help....Much appreciated!

**ifconfig command**

Results
> eth0      Link encap:Ethernet  HWaddr 00:24:1d:d3:2e:d0  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fed3:2ed0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:464202 (464.2 KB)  TX bytes:107617 (107.6 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)



**Results for route -n**
> 


Kernel IP routing table
Destination     Gateway         Genmask         Flags  Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U      0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U      1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG     100    0        0 eth0

BOTH of those changed I am sure of.  Atleast it shows 2 IP addresses now.  Guess its a start eh?  The google lookup was the exact same so no connection to the internet but I am connected to the network as of now.

---

### Post by papibe on 2011-07-14
Yes, no network at all. Let's take a look to some network config files. Could you post this files:
```
/etc/network/interfaces

/etc/dhcp3/dhclient.conf

/etc/nsswitch.conf

```
Regards.

---

### Post by StephenP55M-UD2 on 2011-07-15
Thank you, heres the results:

**etc/network/interfaces**
auto lo
iface lo inet loopback


**Now in dchp3 I have no config file..in dhcp I do**
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


**etc/nsswitch.conf**
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by papibe on 2011-07-15
Both '/etc/dhcp3/dhclient.conf' and '/etc/nsswitch.conf' look OK.

However the process of asking for an address (DHCP) it is not initiated on interfaces. Add the necessary lines to '/etc/network/interfaces' so it looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
Then restart the network like this:
```
$ sudo service networking restart
```
Then check if you got an LAN IP address by running:
> ```
$ ipconfig
```
EDIT: oops, I meant this:
```
$ ifconfig
```

Regards.

---

### Post by StephenP55M-UD2 on 2011-07-15
Thanks for all the help btw.

So I changed interfaces to exactly what you posted.

I then went to terminal and tried the command **sudo service networking restart**
I get "restart: Unkown instance:"

I then typed in **ipconfig**
I get "No command 'ipconfig' found, did you mean:
Command 'tpconfig' from package 'tpconfig' (universe)
Command 'iwconfig' from package 'wireless-tools' (main)
Command 'ifconfig' rom package 'net-tools' (main)
ipconfig: command not found"

Hmm....I've never had a hassle-free internet setup with Ubuntu :-|

---

### Post by papibe on 2011-07-15
Try this to restart your network instead:
```
$ sudo /etc/init.d/networking restart
```
and, oops, the command to check is the following (just like post #3):
```
$ ifconfig
```
Regards.

---

### Post by StephenP55M-UD2 on 2011-07-15
**stephen@stephen-P55M-UD2:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:24:1d:d3:2e:d0  
          inet6 addr: fe80::224:1dff:fed3:2ed0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109862 (109.8 KB)  TX bytes:17612 (17.6 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10708 (10.7 KB)  TX bytes:10708 (10.7 KB)

Whoopssss, typed in wrong command. 
**stephen@stephen-P55M-UD2:~$ sudo /etc/init.d/networking restart**
[sudo] password for stephen:
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces...                                   [ OK ]

Man I have alot of typos...

---

### Post by StephenP55M-UD2 on 2011-07-15
Alright, now something else has changed.  This is starting to get to me ](*,)  Alright, so I went into Windows to look at Device Manager to look at who makes the onboard LAN for my motherboard.  Its a Realtek PCIe controller but it didn't tell me the exact model.  Probably the exact same on all P55 boards.  I just wanted to google to see if anyone else has problems with Ubuntu and these cards.  Doesn't seem to be....well now I boot back into Ubuntu.  Click on that icon in the top right (The 2 Computer monitors or w/e) and it now tells me my Device is unmanaged.  This problem just seems to keep getting worse in Ubuntu but no change at all in Windows......Appreciate any help!

---

### Post by StephenP55M-UD2 on 2011-07-15
Sorry, I don't really mean to bump my thread but seeing as it is 3 pages behind idk how many people are going to look at it....

Please look at the updates.

Thank you all.

---

