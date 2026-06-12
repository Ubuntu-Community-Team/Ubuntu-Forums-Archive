---
title: "cannot browse Internet; can ping, dig, etc"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by nineowls on 2011-07-19
**Summary:**
I virtualized ancient Ubuntu laptop to ESXi server when most recent kernel won't work with display; The ancient laptop "works" using prior kernel. As virtual machine(vm) on ESXi everything "works" including newest kernel.  I then converted ESXi vm to a vmware server 2.0 vm for use on windows 7 64 bit. It "almost\sometimes works"--can ping, dig, but no browsing. I thought I could compare settings and figure this out but have spent 16 or 20 hours without getting a permanent solution. Any help appreciated! :)
**Problem:**
After finding the network broken, tried many things, actually got browsing fixed once but on reboot, all went back to broken.
Today, this is what I've tried:
Removed all the vmware "hardware nics" and rebooted.
Deleted the /etc/udev/rules.d/70-persistent-net.rules file 
Deleted all the connections in network manager applet
Checked that only the two lo lines are in /etc/network/interfaces
Shutdown the vm
Added one(1) NAT nic in the vmware interface, and checked the mac address 00:0c:29:fd:06:72 
I rebooted the vm, auto eth1 is populated as wired network with the "right" mac
/etc/udev/rules.d/70-persistent-net.rules has that mac mapped to eth0; I changed the reference to eth1.
Reboot.
```
ifconfig -a

```
getting address from vmware server 192.168.44.128 

```
ip addr

```
gets lo and eth1

```
cat /etc/resolv.conf

```
domain localdomain
search localdomain
nameserver 192.168.44.2

```
sudo ping -c 3 google.com 

```
64 bytes from vx-in-f104.1e100.net (75.125.115.104): ... 53.5 ms
...
...0% packet loss, time 2003 ms
(this is almost identical to the result on the laptop and pinging ip address works too)


```
dig google.com 

```
; DiG 9.7.0-P1 <<>> [www.google.com](www.google.com)
;; global options: +cmd
...
...status: NOERROR...
...ANSWER SECTION...
(has an extra line in the vm)
[www.google.com](www.google.com)    5    IN    CNAME    [www.l.google.com](www.l.google.com).
(then has basically same results)
[www.l.google.com](www.l.google.com) ... same ips I get on the other two machines

dig is querying the vmware server ip to get these results

tried adding OpenDNS to the eth0 connection in network applet

made sure all three have different names and rebooted (/etc/hosts /etc/hostname)

Now what?

---

### Post by jmoorse on 2011-07-19
Have you removed the ESX vmware tools and installed the vm tools from server?  I seem to recall they are different packages.

---

### Post by nineowls on 2011-07-19
> **jmoorse said:**
> Have you removed the ESX vmware tools and installed the vm tools from server?  
I just successfully uninstalled them, and reinstalled from the VMWare Server, but the configuration failed (kernel headers wrong)

---

### Post by nineowls on 2011-07-19
Then I shutdown.
Turned off the NAT nic (do not connect at startup)
Added a BRIDGED nic (NOTED THE MAC ADDRESS)
Boot
per instructions here:
[http://forums.virtualbox.org/viewtopic.php?t=7749]("http://forums.virtualbox.org/viewtopic.php?t=7749")
I looked at the new network connection name (Auto Ethernet) in NetworkApplet
Opened ```
sudo vim /etc/udev/rules.d/70-persistent-net.rules
```
Changed the reference "eth2" (your reference may be different--choose the line with the mac address you noted when adding the nic) to "Ethernet"
Then I 
```
sudo /etc/init.d/networking restart
```
I can ssh into my servers and get help from ubuntuforums cuz my Internet works
woot.:P

---

### Post by jmoorse on 2011-07-19
Just to clarify, is this resolved?  If so, please mark it resolved for us.  Thanks

---

