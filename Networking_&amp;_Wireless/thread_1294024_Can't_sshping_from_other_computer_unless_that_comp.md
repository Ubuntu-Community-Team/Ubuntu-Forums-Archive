---
title: "Can't ssh/ping from other computer unless that computer is first ping'd from the 1st"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by houbysoft.xf.cz on 2009-10-17
Hi all,
I have a pretty simple but annoying problem:
it includes 2 machines : one is a laptop with ArchLinux (up to date), the other is Ubuntu (also up to date).

Because the laptop with Ubuntu is way more powerful, I obviously installed ssh on it.

Both laptops are connected to the same public WiFi (ie no WPA / WEP key but I don't think that matters).

Now let's say I want to ssh to the Ubuntu machine from the Arch : I always get No route to host. This is very strange, since I **can** ping the router, the internet, and other machines on the WLAN - therefore I guess the problem is in the Ubuntu machine, otherwise I wouldn't be able to ping other systems on the WiFi. Also, if a try
```

nmap -sP 192.168.1.*

```
it discovers everything except the Ubuntu laptop.

However, I found out that if I first ping the ArchLinux laptop from the Ubuntu one (that works perfectly), I can afterwards ping the Ubuntu laptop from my ArchLinux laptop and then use it normally, ie ssh works.

I would be very glad if someone would provide help since the need for pinging first pretty much destroys the purpose of ssh; and my temporary solution (a python script pinging all IP's in a certain range on the network) isn't that kosher either (yes, it works, but...).


Thanks in advance and sorry if it's some stupid configuration option, I am used to ArchLinux where you almost build your system and therefore know exactly what's installed, ie firewalls etc.

---

### Post by houbysoft.xf.cz on 2009-10-18
Bump, any ideas?

---

### Post by smeee on 2009-11-16
Just installed 9.10 on an HP Mini 1030NR. Had issues with the broadcom wireless and had to install the bcmwl-kernel-source package, remove network-manager-gnome and install wicd to get it to connect (WPA2). Now I am having this exact same problem where you can only connect to the machine remotely (ssh) if the machine is already communicating to the remote host. 

Is your machine using the broadcom driver as well?

Sorry at this point I haven't found a fix but will update the post as I find out more.

---

### Post by doas777 on 2009-11-16
it sounds like powermanagement is turning off the recieving nic. has the machine been inactive for some time?

another possibility is that a firewall is blocking ICMP until the host sends a packet, at which point the firewall opens the port for a period of time. ICMP is hard to get working with stateful packet filtering, as it is connectionless, and its state cannot be determined. never seen a firewall do that, but I've read that they do exist.

---

### Post by smeee on 2009-11-17
Thought it may have been a power management issue at first and tried disabling power management on the interface (eth1 in this case). No luck there and dropped the idea of a power management problem since it is a problem specific to the machine ip initiating the outside connection (ex. if computer A is the computer is question-problem machine, then computer B can not connect to A until A communicates with B (by pinging B from A for example), while A is pinging B, B can then connect (ssh) into A but C still cannot see A as A is not yet in communication to C. Once A stops pinging B then the connection will shortly be severed and the ssh connection from B to A will drop.)

This is an ubuntu 9.10 32bit install fresh off the disk and the only things changed where the installation of bcmwl-kernel-source, removal of network-manager-gnome and installation of wicd. There should be no active firewall and as far as I can tell there is no firewall active (ufw status is inactive). The ip tables (sudo iptables -L) reveal that there are no rules defined for any chain.

Really scratching my head on this one and running out of ideas.

---

### Post by smeee on 2009-11-17
I should mention that I have 2 of these machines (hp mini 1030NR) and it is only the 9.10 machine that has this problem. The other (9.04) does not have this issue at all (although will drop the wireless if not in use due to power management setup). 

I have been unable to determine the difference between the machines that is causing the problem.

Output from "lshw -C network" on 9.04 (working machine):

```
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:25:2b:8a:c1:88
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.20.107 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```Output from "lshw -C network" on 9.10 (non-working machine):

```
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:25:2b:bb:87:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.20.120 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feafc000-feafffff
```

---

### Post by doas777 on 2009-11-17
just to clarify, you (or someone) are logged into to both terminals prior to pinging, right? the new userspace network managers only establish a network connection after login.

---

### Post by tapas_mishra on 2009-11-17
Do an experient let the wifi machine you are referring to do a ping on some other machine or say ping to a non existent host on network and then repeat the problem which u said when you started the thread if there is no problem then that means that when wifi is not being used some how some module is saving power it is similar to wake on LAN sort of thing I am not sure though

---

### Post by smeee on 2009-11-18
Yes, users were logged in prior to pinging on both machines. 

Thanks for all the help thus far, my wife spilled a drink on the keyboard (laptop) and the problem has subsided (along with the general working state of the machine). 

On the up side maybe there will be a patch in place for this problem by the time I have the machine replaced!

---

### Post by doas777 on 2009-11-18
wow. that is the most unsatisfactory, successful remediation of a problem ever. that just sucks.

anyway good luck and have fun

---

### Post by smeee on 2009-11-28
Might have a fix for this issue. Got a loner machine to replace my pop filled laptop and installed arch on it and ended up with this same freaking problem. Intel PRO 4965 wireless in this machine as opposed to the broadcom in the previous machine. After hitting this I figured it had to be a problem with my router and not with the distro setup (seeing as how its arch now and a different car chipset). Turned off the SPI (stateful packet inspection) on the router and so far so good, has only been 15 minutes and I'm still thinking it could be too good to be true but on the other hand it is working better than ever.

Hope this helps. I'll run some more tests in the morning and see if it's still working.

---

### Post by smeee on 2009-12-01
Seemed to solve the issue for a while but in the morning it was back to it's old tricks again. Downgraded the wireless encryption from WPA2 to WPA and seems to have solved it for good. Is it just me or is wifi always this much of a headache.

---

### Post by mswoon on 2013-02-10
I have the same problem but with a HP laptop. This is what I have at home: a 14" HP laptop connected via ethernet LAN, a 17" HP laptop via wireless LAN, a 15" toshiba laptop via wireless LAN. The LAN / Wireless router is a Verizon FIOS modem. The 14" and the 15" can SSH to each other fine. The 17" appears to be *invisible* on the network even though my wife / son is logged in to it and browsing the Internet fine! I have to ask them to open a terminal, do a SSH to any of the other machines ( don't need to login ) , or just ping another machine, and all of a sudden I can SSH into the 17" from either the 14" or 15" machines. Wierd, no?

---

### Post by wildmanne39 on 2013-02-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

