---
title: "Router reset problem"
date: 2006-05-20
forum: Networking &amp; Wireless
---

### Post by Daekharel on 2006-05-20
I'm having trouble with networking using a NetGear WGR614v5 router. The router worked fine until recently, when a bunch of problems came up. I'm not sure how interrelated they are, but here's a short summary of the circumstances:

After removing a redundant user (using System->Administration->Users and Groups) without first deleting its home directory, I used the terminal and tried to "sudo rm -r" their home directory. Nothing happened. I then tried a bunch of other things using sudo, from changing mods to changing the owner, etc, but I could not affect the folder in any way. By trying various things, I found that I was unable to "sudo" anything; it appeared I was no longer in the sudoers file.

I then booted up using [SystemRescue CD](http://www.sysresccd.org/Main_Page), mounted my main linux partition, and manually edited /etc/sudoers to include myself. It also already included the line "%admin  ALL=(ALL) ALL"; presumably I had previously been in the admin group, and somehow been removed. I booted back up into Ubuntu, and added myself to the admin group.

However, at this point I found that I could not access the internet, and furthermore my sound controls were non-functional. I tried to figure out why I couldn't access the internet, and finally decided it was my router. In the course of trying to fix the problem, I went back to using my DSL modem directly, without the router, but had to reset it to factory defaults because I couldn't remember the username/password combination. After doing this, I was able to access the internet directly through the modem; that's how I'm making this post.

I also reset the router, and followed the instructions for setting it up as normal. However, after executing all but the final step, I was unable to connect to the router by any means. The manual (written for installing on Windows, obviously) said that the "NETGEAR Smart Wizard" would be the first page visited by any browser on startup; this would probably normally be the case, since, after checking the router's IP, I found (using a quick interactive [Python](http://docs.python.org/) session and the socket module) that any hostname except "localhost" resolved to the ip address of the router, 192.168.1.1.

However, I was unable to connect to 192.168.1.1. Pinging it resulted in 100% packet loss and traceroute stalled. Here are the results of the tests suggested in [this thread](http://www.ubuntuforums.org/showthread.php?t=87643), spaced for readability:

```
daedalus@Hades:~$ cat /etc/network/interfaces
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

auto eth0


daedalus@Hades:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:88:54:F9
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe88:54f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5518 (5.3 KiB)  TX bytes:9066 (8.8 KiB)


daedalus@Hades:~$ lspci | grep Eth
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)
daedalus@Hades:~$ lsmod | grep mii
mii                     5248  1 e100


daedalus@Hades:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


daedalus@Hades:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

daedalus@Hades:~$
```As I mentioned, I am using a NetGear WGR614 v5 wireless router (although the problems I'm having are with using it wired); my DSL modem is a Westell model 2200. My ISP is Verizon.

While my internet connection works perfectly through the DSL modem alone, others who live with me depend on the wireless functionality of the router to access the internet from their laptops, so any solution or suggestion ASAP would be appreciated. I'd also like to know why my sound card seems to have stopped working, and of course what caused these problems, but those are secondary issues; I'm not even sure the sound trouble is related to the router problems - they just both stopped working after the same incident.

Thanks in advance.

---

### Post by jazzmuzik on 2006-05-20
"sudo -r rm" ?

sudo rm -rf /home/userdir

or

userdel -r username

-r removes the account and the files

---

### Post by Daekharel on 2006-05-20
[QUOTE=jazzmuzik]"sudo -r rm" ?

sudo rm -rf /home/userdir

or

userdel -r username

-r removes the account and the files[/QUOTE]Sorry, I mistyped. "sudo rm -r /home/userdir" was what I used. And I've already managed to delete the user and the home directory. I just recreated the user and then deleted the home folder first, then the user. I'll keep that in mind, though. My main problem now is the router.

---

