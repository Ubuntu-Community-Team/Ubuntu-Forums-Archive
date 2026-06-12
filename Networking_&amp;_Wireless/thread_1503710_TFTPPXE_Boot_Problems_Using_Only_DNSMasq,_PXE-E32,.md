---
title: "TFTP/PXE Boot Problems Using Only DNSMasq, PXE-E32, ICMP udp port tftp unreachable"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by mpare on 2010-06-07
**The Problem:**
Guest computer receives IP address, Mask, DHCP IP, Gateway IP but fails to capture the TFTP file. The guest outputs error

PXE-E32: TFTP open timeout

PXE-E32: TFTP open timeout
PXE-E32: TFTP open timeout
PXE-M0F: Exiting PXE ROM

There is activity when I do a tcpdump on the server end, which I will post below under "Debug Info."

**The Setup:**
I'm running Ubuntu 9.10 (32bit)  on laptop which is just running as a simple server on the shelf. I've setup DHCP, TFTP, DNS via DNSMasq and openssh-server. I've recorded the steps from a fresh fresh install in two posts on my website, [http://paretech.com/node/15](http://paretech.com/node/15) and [http://paretech.com/node/16](http://paretech.com/node/16). Basically these two posts outline the steps I took to remove network-manager, configure dnsmasq. 

Things seem to be working as I intended, all of my computers (4) on the network are receiving proper IPs, they can connect to the internet, they can ping each other by host names defined in /etc/hosts. The computers that I am trying to netboot are just mother boards for kernel development. I use the same boards in a setup at work that is very similar if not exact to what I'm trying to configure at home.

**What I've Tried:**
I've tried my best to record the steps I took to make my setup from a clean install in the two posts above. I think they are very accurate. I've done a lot of searching in these forums and through google in general. I've found lots of posts that sound relevant and most seem to deal with iptable configs. I've tried turning off my iptables using the following,

```

$ iptables -X
$ iptables -t nat -F
$ iptables -t nat -X
$ iptables -t mangle -F
$ iptables -t mangle -X
$ iptables -P INPUT ACCEPT
$ iptables -P FORWARD ACCEPT
$ iptables -P OUTPUT ACCEPT

```But it had zero impact on the result.

I also spent some time looking at, [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot). There they ran through several checks for evaluating the ports but they didn't offer any resolve if things didn't act as purposed. 

For example, check if *dnsmasq* is listening on the *bootp* port 67...

```

# sudo netstat -nulp | grep '67'

udp        0      0 0.0.0.0:67              0.0.0.0:*                           943/dnsmasq 

```But when I, check if *dnsmasq* is listening on the *tftp* port 69
```

# sudo netstat -nulp | grep '69'
<no output>

```Which leads me to believe that there is something wrong with the listening port 69, at least according to the post at [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot).

**Debugging Info**

iptables -L:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  10.1.84.0/24         anywhere            
ACCEPT     all  --  anywhere             10.1.84.0/24        

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```some output from # sudo tcpdump -i eth0 ether host 00:24:8C:A8:59:07
```

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
00:39:27.314326 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:24:8c:a8:59:07 (oui Unknown), length 548
00:39:29.566264 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:24:8c:a8:59:07 (oui Unknown), length 548
00:39:29.629300 ARP, Request who-has barrel tell fish1, length 46
00:39:29.629308 ARP, Reply barrel is-at 00:0f:b0:8c:15:38 (oui Unknown), length 28
00:39:29.629385 IP fish1.2070 > barrel.tftp:  26 RRQ "pxegrub.0" octet tsize 0
00:39:29.629423 IP barrel > fish1: ICMP barrel udp port tftp unreachable, length 62
00:39:31.653139 IP fish1.2071 > barrel.tftp:  26 RRQ "pxegrub.0" octet tsize 0
00:39:31.653173 IP barrel > fish1: ICMP barrel udp port tftp unreachable, length 62
00:39:34.626407 ARP, Request who-has fish1 tell barrel, length 28
00:39:34.626487 ARP, Reply fish1 is-at 00:24:8c:a8:59:07 (oui Unknown), length 46
00:39:35.662830 IP fish1.2072 > barrel.tftp:  26 RRQ "pxegrub.0" octet tsize 0
00:39:35.662866 IP barrel > fish1: ICMP barrel udp port tftp unreachable, length 62
00:39:41.649549 IP fish1.2073 > barrel.tftp:  26 RRQ "pxegrub.0" octet tsize 0
00:39:41.649586 IP barrel > fish1: ICMP barrel udp port tftp unreachable, length 62
00:39:49.613723 IP fish1.2074 > barrel.tftp:  26 RRQ "pxegrub.0" octet tsize 0
00:39:49.613758 IP barrel > fish1: ICMP barrel udp port tftp unreachable, length 62
00:39:59.555281 IP fish1.2075 > barrel.tftp:  31 RRQ "pxegrub.0" octet blksize 1456
00:39:59.555321 IP barrel > fish1: ICMP barrel udp port tftp unreachable, length 67
00:40:04.554551 ARP, Request who-has fish1 tell barrel, length 28

```I've also attached my dnsmasq.conf, with some of the mac addy's removed.

**Conclusion**
So I'm pretty new to Linux and Ubuntu, there is a lot I don't understand. But I have put in several hours of searching, trying, and reading. I know how offensive it can be when someone doesn't try before they post in the forums but I felt like it was time to ask for some help. 

If you need any more system information I will be happy to respond back, I probably won't be able to respond back until after 6pm PST 6/7/10 so please ask for what ever data you need and if you don't mind including what you are looking for in that data and then the next logical step. I appreciate your help and value your time.

-Matt

---

### Post by puppywhacker on 2010-06-07
which tftp server did you use/install? I prefer tftpd-hpa you checked port UDP/67 for DHCP, but you skipped through port UDP/69 quickly so to me it looks like there is no tftp-server running?

with "lsof -i:69" you can check which process is listening to port 69 that should give you a huge clue.

install lsof with "sudo apt-get install lsof"

---

### Post by mpare on 2010-06-07
I will definitely check this when I get off work. In regards to what tftp server I am using, I am using DNSMasq as my tftp as that is how I believe we have it configured at work. I checked my dnsmasq.conf against the setup used at work and they are congruent except to the regard of my base IP selection.

In the posts that I read I saw that most of them were using atftp or tftp-hda, is this recommended over DNSMasq? DNSMasq just seemed very simple to me and the config was very well documented.

-Matt

---

### Post by puppywhacker on 2010-06-07
from what I've read it does not have a builtin tftp server so you will have to install one separately, my experience with tftpd-hpa were slightly better than the other one, configuration should be straightforward using "sudo apt-get install tftpd-hpa"

---

### Post by mpare on 2010-06-08
Ok so I tried a couple things...

The man page on my system says dnsmasq is an tftp server. This is conducive to my setup at work.

I had previously tried netstat for port 69, I posted that in my original post but it had a typo so it looked like I checked 67 twice. On my server machine there are no matching results for port 69.

To tie these two items up, I did try something on a ubuntu 10.04 64-bit machine I had laying around,

```

# sudo apt-get install dnsmasq
# sudo vi /etc/dnsmasq.conf

```

I uncommented two lines, <tt>enable-tftp</tt> and <tt>tftp-root</tt>, then,

```

# sudo /etc/init.d/dnsmasq restart
 * Starting DNS forwarder and DHCP server dnsmasq                                            [ OK ]
# sudo netstat -apn|grep ":69 "
udp        0      0 0.0.0.0:69              0.0.0.0:*                           2857/dnsmasq
# sudo /etc/init.d/dnsmasq stop
 * Stopping DNS forwarder and DHCP server dnsmasq                                            [ OK ]
# sudo netstat -apn|grep ":69 "
<no_return_output>

```

So it does appear that dnsmasq has a built in tftp server and I really would like to use it because it reduces how many files I need to edit, dnsmask allows me to place multiple "net" identifiers on each host allowing me to do some interesting routing rules which I use for complicated chain loading of certain net bootloaders (etherboot, gpxe, men32, GRUB Legacy, GRUB2, PXELINUX, etc...). 

Dnsmasq has proven to be an easy and robust system for the development work I am doing. So it seems to work on 10.04 but can you now please help be debug it on 9.10? I don't know enough about the system to do it alone but I feel determined to figure it out. I'm new to linux and I've been using ubuntu solid for the last 4 weeks and I've learned so much and want to learn some more. In addition I try to document my work and your solutions will be reiterated in my private postings as well.

-Matt

---

### Post by Sob Rogue on 2010-06-11
Hi mpare,
 
I am having a similar issue. My setup is slightly differant, but I think the underlying cause is the same. I am attempting to run Fog (imaging software) that uses tftp. This on its own works fine, but I would like to also setup a nat, so that clients recieve internet. It seams that anytime I setup the nat, and attempt a PXE boot, I get the same error message as you:
 
TFTP open timeout
TFTP open timeout
Exiting PXE ROM
 
But, the second I disable nat, TFTP starts working fine. I'm stilling working on a solution. There must be some conflict between the two services....
 
Please post any of your findings or solutions,
 
Thanks,
Rogue

---

### Post by mpare on 2010-06-11
Rogue,
Two quick questions... 

(1) What version of Ubuntu are you running.

(2) What is make/model is the host network adapter (the one your trying to server TFTP from)? Is it, by chance, a Realtek 8139?

I ask (1) to see if this might be version specific and (2) because I've seen a few posts that try to conclude that it's an issue with Realtek 8139 NIC. My computer is indeed trying to serve TFTP on a Realtek 8139.

I don't know enough to even give any gravity to (2) being a real assumption, my gut tells me to be suspicious but I'll remain open to the idea if I can get a better understanding.

You can do a quick google on "realtek 8139 tftp" to see some of these posts but again I'm skeptical.

-mpare

---

### Post by Sob Rogue on 2010-06-11
1) Ubuntu 10.04
2) I am using a NetXtreme BCM5755(DHCP/TFTP/Fog) & Realtek 8111/8168B(Internet)
 
I will attempt this setup with all non-Realtek NICs, and see if the problem persist.
 
-Rogue

---

### Post by mpare on 2010-06-11
Hmm... I haven't tried Ubuntu 10 on the same computer that I have the Realtek card on but TFTP started up fine for me on another laptop running 10 and the following

```

06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

I believe the Realtek card was only an issue for the TFTP side.

-mpare

---

### Post by Sob Rogue on 2010-06-11
The symptoms were the same after I removed the realtek card. Like you said, probably didn'm matter because it wasn't on TFTP side.
 
I also tried only using DNSMasq, and I got the same error. I then removed DNSMasq, tftp started working again...
 
What is DNSMasq doing that causes tftp to stop?
 
I'm going to try using an old router insead of DNSMasq....
 
-Rogue

---

### Post by mpare on 2010-06-11
Rogue,
When you say when you removed DNSMasq, TFTP starts again, does that mean that you removed/turned off DNSMasq then installed another TFTP server or it just started running? DNSMasq is a TFTP, DNS, DHCP server so if you have two TFTP servers that may be causing you trouble which is a different issue than my original post. I'm starting to wonder if we are experiencing two different issues. You might try running a 

```
# ps aux
```

to see what your active processes are to see if you are perhaps running another TFTP server.

-mpare

---

