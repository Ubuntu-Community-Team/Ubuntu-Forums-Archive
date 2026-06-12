---
title: "No Idea. Internet just won't work"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by TinKanSinar on 2011-09-14
I have built my first computer. It took a while but it works. Then I installed Ubuntu 11.04 over the entire hard drive. I keep getting the message "Disconnected-You are now offline." I have a brond new motorola sb5101 surfboard modem. The wires are all hooked up and brand new. My ethernet connection is on my intel d945gnt motherboard. My modem says I am online, but I just can't get internet. I have tried resetting, adding a static ip. I just don't know what to do. I can't even ping google.

---

### Post by papibe on 2011-09-14
Could you post the result of these commands?
```
$ lspci -nn | grep -i eth

$ sudo lshw -C network

$ ifconfig -a

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Please use the # tags (code tags).

Regards.

---

### Post by TinKanSinar on 2011-09-15
lspci -nn | grep -i eth:
```
 
01:00.0 Ethernet controller [0200]: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) [8086:108b] (rev 03)

```
 
sudo lshw -C network:
```

*-network
    description: Ethernet interface
    product: 82573V Gigabit Ethernet Controller (Copper)
    vendor: Intel Corporation
    physical id:0
    bus info: pci@0000:01:00.0
    logical name: eth0
    version: 03
    serial: 00:16:76:c0:02:6e
    size: 100Mbit/s
    capacity: 1Gbit/s
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=1.0-5 ip=10.0.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
    resources: irq:45 memory:90100000-9011ffff ioport:1000(size=32)

```
 
ifconfig -a:
```

eth0     Link encap:Ethernet HWaddr 00:16:76:c0:02:6e
          inet addr:10.0.0.100 Bcast:10.0.0.255 Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fec0:26e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
          RX packets:3766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:225960 (225.9 KB) TX bytes:6291 (6.9 KB)
          Interrupt:16 Memory:90100000-90120000
 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          int6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436 Metric:1
          RX packets:4156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:332216 (332.2 KB) TX bytes:332216 (332.2 KB)

```
 
route -n:
```

Kernel IP routing table
Destination    Gateway     Genmask          Flags  Metric  Ref   Use  Iface
10.0.0.0       0.0.0.0     255.255.255.0    U      0       0      0     eth0
169.254.0.0    0.0.0.0     255.255.0.0      U      1000    0      0     eth0
0.0.0.0        10.0.0.1    0.0.0.0          UG     100     0      0     eth0

```
 
nslookup ubuntu.com:
```

;; connection timed out; no servers could be reached

```
 
dig ubuntu.com:
```

; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```

---

### Post by papibe on 2011-09-15
It looks like you have a DNS problem (the service that translate the sites names into workable IPs).

The IP addresses for the machines that provides the service are located in this file:
```
/etc/resolv.conf
```
My guess is that file is empty. In order to permanently solve your problem (so it works every time you boot) we need more work... BUT, this is quick-on-the-fly fix:
[INDENT]In a terminal run this to edit the file:
```
$ gksudo /etc/resolv.conf
```
Write the following, and save the file:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
**[COLOR="Red"]WARNING:[/COLOR]** those addresses are for "Google Public DNS" (read [here]("http://code.google.com/speed/public-dns/")), and are safe (in terms of security), but the use of unknown addresses here could imply serious security problems. Always double check what you put in there.[/INDENT]

After that try the last 2 command that I gave you (nslookup and dig). If you have a result now, i.e. a translation to an IP, go and try accessing the Internet with your browser (it may need restart the browser).

Now, to solve your problem permanently we need to find why the DNS servers are not set.

A few questions:
[LIST]
[*]Are you using the desktop version or the server version?
[*]Have you uninstall the network manager? (If you are using every thing as was installed the you are using it).
[/LIST]

Tell us how it goes,
Regards.

---

### Post by TinKanSinar on 2011-09-15
I put in the nameservers for the resolv.conf file. My connection still will not work. Nslookup and dig will not produce anything. 
 
As for the questions I am running Desktop Ubuntu, and I am using the network manager so, yes it is installed.

---

### Post by papibe on 2011-09-15
OK.

Could you post a screenshot of this:
[INDENT]Open 'Network Connections'.
Select eth0, and press Edit.
Select the tab called 'IPv4 Settings'
Take a screenshot of that windows (Alt+PrtScn)[/INDENT]

Regards.

---

### Post by TinKanSinar on 2011-09-15
My eth0 is called ifupdown(eth0). It won't let me click on edit.

---

### Post by papibe on 2011-09-15
> **TinKanSinar said:**
> My eth0 is called ifupdown(eth0). It won't let me click on edit.

Interesting, I think we are getting something. It looks that a conflict has been created by editing the files manually.

Here's a [post]("http://ubuntuforums.org/showpost.php?p=8275776&postcount=6") explaining how to get back 100% to admin your connections using the GUI 'Network Connections' (using NetworkManager underneath).

Tell if it helps you.
Regards.

---

### Post by TinKanSinar on 2011-09-15
I'm back to network manager but I'm missing eth0. What now?
 
(I'm on the second page now.)

---

### Post by papibe on 2011-09-15
Did you restart you computer?

---

### Post by TinKanSinar on 2011-09-15
Yes. Twice now.

---

### Post by papibe on 2011-09-16
Could you post this files:
```
/etc/hosts
/etc/network/interfaces
/etc/dhcp3/dhclient.conf
```
Regards.

---

### Post by TinKanSinar on 2011-09-17
/etc/hosts:
```

127.0.0.1  localhost
127.0.1.1  random

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

```

My dhclient.conf file is in /etc/dhcp not /etc/dhcp3.
/etc/dhcp/dhclient.conf:
```

(A bunch of sayings about what the file does and how not to touch it or else.)

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classles-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0-link1-link2", "link0 link1";
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

```

---

### Post by papibe on 2011-09-17
Nothing wrong there.

Since we change the configuration on post #9. Could you post again the commands on post #2?

Regards.

---

### Post by TinKanSinar on 2011-09-17
lspci -nn | grep -i eth:
```
 
01:00.0 Ethernet controller [0200]: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) [8086:108b] (rev 03)

```
 
sudo lshw -C network:
```

*-network
    description: Ethernet interface
    product: 82573V Gigabit Ethernet Controller (Copper)
    vendor: Intel Corporation
    physical id:0
    bus info: pci@0000:01:00.0
    logical name: eth0
    version: 03
    serial: 00:16:76:c0:02:6e
    size: 100Mbit/s
    capacity: 1Gbit/s
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=1.0-5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
    resources: irq:45 memory:90100000-9011ffff ioport:1000(size=32)

```
 
ifconfig -a:
```

eth0     Link encap:Ethernet HWaddr 00:16:76:c0:02:6e
          inet6 addr: fe80::216:76ff:fec0:26e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
          RX packets:51796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3107760 (3.1 MB) TX bytes:5587 (5.5 KB)
          Interrupt:16 Memory:90100000-90120000
 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          int6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436 Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)

```
 
route -n:
```

Kernel IP routing table
Destination    Gateway     Genmask          Flags  Metric  Ref   
```
 
nslookup ubuntu.com:
```

;; connection timed out; no servers could be reached

```
 
dig ubuntu.com:
```

; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```

---

### Post by papibe on 2011-09-17
What happens if you do this:
```
$ sudo ifdown eth0

```
and then
```
$ sudo ifup eth0
```
Regards.

---

### Post by TinKanSinar on 2011-09-17
sudo ifdown eth0:
```

ifdown: interface eth0 not configured

```

sudo ifup eth0:
```

Ignoring unknown interface eth0=eth0.

```

---

### Post by papibe on 2011-09-17
Try this:
```
$ sudo dpkg-reconfigure network-manager
```
and then
```
$  sudo service network-manager restart
```
If that won't get us anywhere I'm going to suggest to get rid off network manager and do all the configuration using files.

Regards.

---

### Post by TinKanSinar on 2011-09-17
Unfortunately, I still do not have eth0 showing up.

---

### Post by papibe on 2011-09-17
Ok, let's do a test before get uninstalling NM.

Stop the NM service:
```
$ sudo service network-manager stop
```
Edi your /etc/network/interfaces so it looks like this:
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
No start the traditional networking service:
```
$ sudo service networking start
```
Now try the nslookup and the dig command. If that works try browsing the Internet.

Tell me how it goes.
Regards.

---

### Post by TinKanSinar on 2011-09-17
I'm getting networking stop/waiting.

---

### Post by papibe on 2011-09-17
Maybe this:
```
$ sudo service networking **restart**
```

---

### Post by TinKanSinar on 2011-09-17
```

restart: Unknown instance:

```

---

### Post by papibe on 2011-09-17
I'm running out of ideas :confused: Try this:
```
$ sudo dhclient eth0
```

---

### Post by TinKanSinar on 2011-09-17
It doesn't seem to have done anything, but I think that's because networking is still down. I turned on network-manager to check, but it just gives device not managed.

---

### Post by papibe on 2011-09-17
Is the driver loaded? What's the output of
```
$ lsmod | grep e1000e
```
The output should be something like:
```
e1000e                120432  0 
```
If nothing is displayed, try:
```
$ sudo modprobe e1000e
```
Tell me how it goes.
Regards.

---

### Post by TinKanSinar on 2011-09-17
```

e1000e   138627 0

```

---

### Post by TinKanSinar on 2011-09-18
I rebooted my computer and I got the eth0 to ifup and ifdown. The problem now is that networking is stuck on stop/waiting. I did: 
```

initctl list | grep network

```
and I got:
```

network-manager stop/waiting
network-interface (lo) start/running
network-interface (eth0) start/running
network-interface-security (network-manager) start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (networking) start/running
networking stop/waiting

```

I also did:
```

sudo /etc/init.d/networking restart

```
and it gives me:
```

 * Reconfiguring network interfaces...      [ OK ]

```

But "initctl list | grep network" still gives me the same response. Apparently networking itself will not turn on, even with network manager on. What can I do to fix that?

---

### Post by TinKanSinar on 2011-09-18
I've looked around a bit, and I've found that it seems to be a bug that has affected several people. Thankfully that means it's not my fault or my new computers, but I might have to redo the install with brand new files.

---

### Post by wkatastrof on 2012-04-24
> **TinKanSinar said:**
> I've looked around a bit, and I've found that it seems to be a bug that has affected several people. Thankfully that means it's not my fault or my new computers, but I might have to redo the install with brand new files.


What bug is this? I am also affected by it where networking is stuck at 'networking stop/waiting'. I can't believe that I would have to reinstall from scratch to get this working again.

---

