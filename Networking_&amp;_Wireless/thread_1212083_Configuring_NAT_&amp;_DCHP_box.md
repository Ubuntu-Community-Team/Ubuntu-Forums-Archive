---
title: "Configuring NAT &amp; DCHP box"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by TRex on 2009-07-13
I am trying to configure a combo NAT & DHCP server where eth0 connects to the Internet using DHCP and then shares its Internet connection through eth1.

This is brand new for me (newbie in the 'nix world) so I searched for help.

The directions at [http://www.computechgroup.com/?p=480]("http://www.computechgroup.com/?p=480") appear to cover what I'm doing so I tried them with appropriate mods. But it doesn't work. :-(

ifconfig produces the following
```
eth0  Link encap:Ethernet  HWAddr 00:xx:xx:xx:xx:xx
      inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
      inet6 addr: fe80::2e0:29ff:fe5a:60de/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      ...
      ...
      ...
      ...
      
eth1  Link encap:Ethernet  HWAddr 00:xx:xx:xx:xx:xx
      inet addr:10.10.1.5  Bcast:10.10.1.255  Mask:255.255.255.0
      inet6 addr: fe80::204:76ff:fe72:63b2/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      ...
      ...
      ...
      ...
      
lo    Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      ...
      ...
      ...
      ...

```

(I suspect more than the ifconfig will be needed, but don't know enough to know what that might be.)

The DHCP server is functioning -- giving out addresses with correct gateway but no DNS server. But even a manual config of DNS server on a Windoze box gives no joy to the outside. This unit can get to the Internet as long as the Windoze machine I'm trying to replace is connected and running.

I'd *really* appreciate help.

---

### Post by iponeverything on 2009-07-13
Add the following line to the top of /etc/dhcp3/dhcpd.conf

```
option domain-name-servers 208.67.220.220, 208.67.222.222
```

add the following lines to your /etc/rc.local

```
iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

and reboot

---

### Post by TRex on 2009-07-14
> **iponeverything said:**
> 
add the following lines to your /etc/rc.local

```
iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

Do those lines go before or after the 'exit 0' line (only line not commented out)?

Will those lines work? -- From the shell, when typing either
```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```
or
```
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
```

I get 'Permission denied' which makes me wonder if the command will be denied to the rc.local script.

---

### Post by TRex on 2009-07-14
Additional details
I have a router connected to my cable modem. I'm trying to replace the router because it is a choke point. I'm using it now because the next item is a Win2k server & I don't trust a Windoze box directly on the Internet. The router uses DHCP on the Internet side and 192.168.0.1 with DHCP on the back side.

Next is the Win2k server. It connects to the router with a DHCP NIC (always 192.168.0.2) and connects to my main switch with a NIC set to 10.10.1.1 and running DHCP server. Its gateway and DNS server are set to 192.168.0.1.

The goal is to replace both with a single Linux box.

The Ubuntu 9.04 box has eth0 connecting to the router (either 192.168.0.2 or 192.168.0.3 depending on status of Win2k server) which it gets via DHCP. eth1 is connected to the main switch. It is configured to 10.10.1.5 with both gateway and DNS set to 192.168.0.1. With the Win2k server down, DHCP-enabled boxes are getting IP addresses (so I know the DHCP server is functioning correctly) and can ping 10.10.1.5 but canNOT ping 192.168.0.1 as they can with the Win2k setup. So I figure the Ubuntu box is not forwarding properly.

Ideas?

---

### Post by iponeverything on 2009-07-14
> **TRex said:**
> Additional details
I have a router connected to my cable modem. I'm trying to replace the router because it is a choke point. I'm using it now because the next item is a Win2k server & I don't trust a Windoze box directly on the Internet. The router uses DHCP on the Internet side and 192.168.0.1 with DHCP on the back side.

Next is the Win2k server. It connects to the router with a DHCP NIC (always 192.168.0.2) and connects to my main switch with a NIC set to 10.10.1.1 and running DHCP server. Its gateway and DNS server are set to 192.168.0.1.

The goal is to replace both with a single Linux box.

The Ubuntu 9.04 box has eth0 connecting to the router (either 192.168.0.2 or 192.168.0.3 depending on status of Win2k server) which it gets via DHCP. eth1 is connected to the main switch. It is configured to 10.10.1.5 with both gateway and DNS set to 192.168.0.1. With the Win2k server down, DHCP-enabled boxes are getting IP addresses (so I know the DHCP server is functioning correctly) and can ping 10.10.1.5 but canNOT ping 192.168.0.1 as they can with the Win2k setup. So I figure the Ubuntu box is not forwarding properly.

Ideas?

Its very mechanical, no magic. Try your echo after a ""sudo -i".

Make a little ASCII diagram of your setup. I still don't understand your topology.

---

### Post by TRex on 2009-07-15
Topology
```

PRESENT CONFIGURATION
                              _____________________________          __________________________
                             | FIREWALL/ROUTER APPLICANCE  |        |        WIN2K SERVER      |         ________      VARIOUS PCs
INTERNET --- CABLE MODEM ----| NIC1                  NIC2  |--------| NIC1              NIC2   |--------| SWITCH | --- & PRINTERS
             (serves IP      | DHCP            192.168.0.1 |        | DHCP          10.10.1.1  |         --------       (10.10.1.x)
           addr from ISP)    | (varies)      built-in DHCP |        |(192.168.0.2)  DHCP server|
                              -----------------------------          --------------------------



==========================================================================================================================

HOPED-FOR CONFIGURATION

                              ________________________ 
                             |         UBUNTU         |         ________      VARIOUS PCs
INTERNET --- CABLE MODEM ----| eth0             eth1  |--------| SWITCH | --- & PRINTERS
             (serves IP      | DHCP        10.10.1.5  |         --------       (10.10.1.x)
           addr from ISP)    | (varies)   DHCP server |
                              -------------------------

```
(I hope that makes it clearer)


Being a newbie, I don't know what
> Try your echo after a ""sudo -i".
means or how to do it. Although I understand networking, treat me like I know nothing when it comes to Ubuntu ('cause I don't)! I still don't know where to put those lines in the rc.local file. I don't even know what the 'echo' command does.

---

### Post by iponeverything on 2009-07-15
Thanks for the diagram it does clear things up.

```
sudo -i
```

Gives you in interactive root shell. Using echo to "echo" a value into into a variable on /proc to change the forwarding behaviour, will work. I have no do idea why sudo does not, but that does not matter. When you are trying to get this work, make sure that you have no other firewall rules in place on linux machine by clearing them with

```
iptables -F
```

And yes, the two lines go above the "exit 0" or they will never be seen.  After the reboot you check the forwarding variable with cat like so

```
cat  /proc/sys/net/ipv4/conf/all/forwarding
```

0 in off
1 is on

Sorry for treating you more like a experienced user than a someone that is new to linux, I have generally people respond better to former. When you see an option to command that you recognize, type "man <that command>" and then use "/" to search the man page for that option to see what it does. 

Though I will be first to admit that the man pages often to cryptic to be of any help. Something else you do is use google. One or two extra words to narrow the search, does wonders.

---

### Post by martinbaselier on 2009-07-15
After the > sign you are no longer root, but a normal user. 
**echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward**
would be a correct way to do this within a terminal.

---

### Post by TRex on 2009-07-15
I got things working using Firestarter -- sort of. As long as I manually add the Open DNS servers, everything works fine. But on a purely DHCP config, the Open DNS servers do not appear and a box can't look up addresses.

I think this weird because the /etc/dhcp3 file (which starts with a comment line: 'DHCP configuration generated by Firestarter') includes the Open DNS servers in the 'option domain-name-servers' line. But for whatever reason, those listings are not being transmitted by the DHCP server.

I'm going to try changing the DNS for eth1 (the shared NIC) to one of the Open DNS servers and see if that gets picked up by a unit using DHCP.

iponeverything, I appreciate that most people respond better to being treated as more experienced (you're right), but I know what I don't know (a lot when it comes to Linux) and don't mind being hand-held/spoon-fed! :)

I'll start locking down security with rules added to Filestarter. Thanks for all the help.

---

