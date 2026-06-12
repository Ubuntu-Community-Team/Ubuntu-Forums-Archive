---
title: "can't ping Ubuntu computer unless Ubuntu computer pings other computer first"
date: 2013-09-04
forum: Networking &amp; Wireless
---

### Post by rclocher3 on 2013-09-04
Hi all, I'm trying to troubleshoot some Samba difficulties, and I've run across an absolutely baffling problem: I can't ping my netbook running Ubuntu 13.04 (Raring Ringtail) by either IP address or hostname.  I did find an exception to that rule, so read on...

I have a home network with a DSL wireless router. The netbook running Ubuntu connects wirelessly, and there are also a couple Windows machines, one of which is wireless and the other is on ethernet. All the computers can surf the web. The Windows computers can ping each other by NetBIOS name or by IP address.  All the computers are in the usual 192.168.0.x IPv4 subnet, and the subnet mask is correct at 255.255.255.0.  The router sees all the computers by hostname. 

I don't believe the Ubuntu firewall is up: "sudo ufw status" reports "Status: inactive".  I'm not quite sure how to interpret the results from "sudo iptables -L"; I'll post the output at the bottom of this post.

I've fiddled around quite a bit, and I discovered something: the Ubuntu computer will respond to pings, but only when the Windows computer pinging it is in its ARP table, which normally isn't the case.  (I just found out about ARP yesterday, and I'm not quite sure what it does.)  Pinging the Windows computer puts that machine in the Ubuntu computer's ARP table, but only for a short time, not even five minutes.  Here's the whole experiment.  "teeny" is the Ubuntu machine, "work" is one of the Windows boxes.

Starting on the Windows computer, I'll ping the Ubuntu machine by IP address:
```
C:\>ping 192.168.0.105
 
Pinging 192.168.0.105 with 32 bytes of data: 
```**(always times out)**
 
Next ping the Ubuntu machine by hostname:
```
C:\>ping teeny
 
Pinging teeny.PK5001Z [198.105.251.23] with 32 bytes of data:
``` **(wrong address, times out)**

```
C:\>arp -a
 
Interface: 192.168.0.211 --- 0x2
  Internet Address      Physical Address      Type
  192.168.0.1           b0-b2-dc-82-47-23     dynamic
  192.168.0.105         00-26-82-af-a1-f6     dynamic
``` **(just the gateway and itself -- Ubuntu machine not listed)**

Now to the Ubuntu machine.
```
rob@teeny:~$ arp -a
PK5001Z.PK5001Z (192.168.0.1) at b0:b2:dc:82:47:23 [ether] on eth1
``` **(just the gateway is listed)**

```
rob@teeny:~$ ping work
PING work.PK5001Z (192.168.0.211) 56(84) bytes of data.
64 bytes from WORK.PK5001Z (192.168.0.211): icmp_req=1 ttl=128 time=5.07 ms
64 bytes from WORK.PK5001Z (192.168.0.211): icmp_req=2 ttl=128 time=6.30 ms
```[B] (correct address, normal ping response)
[/B]
```
rob@teeny:~$ arp -a
WORK.PK5001Z (192.168.0.211) at 00:12:17:64:ed:f1 [ether] on eth1
PK5001Z.PK5001Z (192.168.0.1) at b0:b2:dc:82:47:23 [ether] on eth1
```** (Now the Ubuntu machine sees the Windows computer)**

Now for the surprise -- back to the Windows machine:
```
C:\>ping -t teeny
 
Pinging teeny.PK5001Z [192.168.0.105] with 32 bytes of data:
 
Reply from 192.168.0.105: bytes=32 time=1024ms TTL=64
Reply from 192.168.0.105: bytes=32 time=1ms TTL=64
Reply from 192.168.0.105: bytes=32 time=330ms TTL=64
(skipping a bit...)
 
Ping statistics for 192.168.0.105:
    Packets: Sent = 10, Received = 9, Lost = 1 (10% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 1659ms, Average = 461ms
```

Now the Windows machine can ping the Ubuntu computer!  But only after the Ubuntu computer has pinged the Windows computer, which puts the Windows computer in its ARP table.  If I wait just a short time, five minutes or so, then the Ubuntu computer no longer has the Windows computer in its ARP table, and when the Windows computer isn't in the ARP table then pings from the Windows computer to the Ubuntu computer time out.  Also, when the Ubuntu computer can be pinged, then its ping response times vary enormously, from 1ms to timing out.

So somehow something in the Ubuntu computer is rejecting ping packets unless the other computer is in the ARP table, which only happens when the Ubuntu computer has contacted the other computer first, and within the previous five minutes or so.  I'd be grateful if anyone could help me figure this out!  I'm pretty sure this problem explains why Samba doesn't work, and I need Samba to work...

- Rob

P.S. ufw is down, but here's the output of "iptables -L" as promised:

```
rob@teeny:~$ sudo iptables -L
[sudo] password for rob:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination
```

---

### Post by houstonbofh on 2013-09-04
Check your subnet masks.  It looks like the Ubuntu system is not responding to arp broadcasts...  That would happen if the Ubuntu system was in a /24 and the Windows system was in a /20, for example, as the broadcast address for /20 is not in the range for /24.

---

### Post by rclocher3 on 2013-09-04
Thanks for looking into my problem.  I double-checked, and both subnet masks are 255.255.255.0.

---

### Post by houstonbofh on 2013-09-05
OK, look into the troubleshooting steps here.  This is for blocking arp, but it can be used in reverse.

[http://www.linuxquestions.org/questions/linux-networking-3/how-can-we-block-arp-packets-344914/](http://www.linuxquestions.org/questions/linux-networking-3/how-can-we-block-arp-packets-344914/)
[http://serverfault.com/questions/175803/how-to-broadcast-arp-update-to-all-neighbors-in-linux](http://serverfault.com/questions/175803/how-to-broadcast-arp-update-to-all-neighbors-in-linux)

If anything works, it is another lead towards the problem.

---

### Post by rclocher3 on 2013-09-06
So I tried a bunch of things, but haven't gotten anywhere really.  arptables isn't installed.  I looked at sysctl.conf to see if there were any fancy settings making the kernel ignore packets, but everything in sysctl.conf is commented out.  I ran tcpdump:

rob@teeny:~$ sudo tcpdump -ni eth1
13:08:46.754758 ARP, Request who-has 192.168.0.105 tell 192.168.0.1, length 28
13:08:46.754817 ARP, Reply 192.168.0.105 is-at 00:26:82:af:a1:f6, length 28

The computer saw the ARP request from the router and replied to it, but it never saw the ping packet from the Windows computer!

So it looks to me as though ARP is working normally.  Wow, I'm really stuck.

---

### Post by houstonbofh on 2013-09-06
Swap with known good ethernet cables, and if you can try a different router.  Something is dropping that arp, and I am not sure why.

---

### Post by rclocher3 on 2013-09-10
The Ubuntu computer is on Wi-Fi.  The internet connection is reasonably reliable, and two Windows computers can ping each other, so I don't think the problem is the router.

So I put windump on the XP machine and fired it up, and then I tried to ping the Ubuntu computer from a different window on the same XP computer:

C:\>windump -i 2 -n
windump: listening on \Device\NPF_{CC5BAD95-9B3C-4353-B5E8-D31F3523D825}
[In another window I entered the command "ping 192.168.0.105" after starting windump.]
21:06:51.300570 arp who-has 192.168.0.105 tell 192.168.0.211
21:06:56.283240 arp who-has 192.168.0.105 tell 192.168.0.211
21:07:01.780075 arp who-has 192.168.0.105 tell 192.168.0.211
21:07:07.251531 arp who-has 192.168.0.105 tell 192.168.0.211

The XP machine is asking who has .105, but the Ubuntu computer isn't responding.  The XP computer never sent the ICMP echo request packets because it didn't even know the MAC address to ping.  You were right that it's an ARP problem, good call houstonbofh!  I was running tcpdump on the Ubuntu computer, and it never saw any traffic at all.  For the sake of comparison I rebooted the Ubuntu computer into the seldom-used Windows 7 side and fired up Wireshark on it, and ran windump on the XP computer again, and tried the ping experiment again between the two Windows computers:

C:\>windump -i 2 -n
windump: listening on \Device\NPF_{CC5BAD95-9B3C-4353-B5E8-D31F3523D825}
[In another window I entered the command "ping 192.168.0.105" after starting windump.]
00:18:51.052338 arp who-has 192.168.0.105 tell 192.168.0.211
00:18:51.055252 arp reply 192.168.0.105 is-at 00:26:82:af:a1:f6
00:18:51.055259 IP 192.168.0.211 > 192.168.0.105: ICMP echo request
00:18:51.057750 arp who-has 192.168.0.211 tell 192.168.0.105
00:18:51.057757 arp reply 192.168.0.211 is-at 00:12:17:64:ed:f1
00:18:51.059691 IP 192.168.0.105 > 192.168.0.211: ICMP echo reply
00:18:52.040531 IP 192.168.0.211 > 192.168.0.105: ICMP echo request
00:18:52.042355 IP 192.168.0.105 > 192.168.0.211: ICMP echo reply

Everything is normal there.  So in the first experiment, when the Ubuntu computer running tcpdump never saw the ARP requests, I think there actually were ARP requests that it could see, because when I ran Winshark on Windows 7 (on the same computer even) then there were the ARP requests.  I think that the Ubuntu kernel was ignoring the ARP requests so that even tcpdump couldn't see them.  If the Ubuntu machine is ignoring ARP requests, then I'm not surprised Samba isn't working -- Samba's my real problem, not ping.

If anyone can shed some light on why the Ubuntu machine is ignoring ARP requests, that would be great.  In the meantime I can Google "Linux not responding to ARP" or something.  If I know what to Google then my problem is half-solved already ;)

---

### Post by houstonbofh on 2013-09-10
Check your AP for "User mode isolation" or something like that.  Some APs make it so the clients can not see each other for security.

---

### Post by rclocher3 on 2013-09-10
Okay, Google pointed me to this bug: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/414724](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/414724) , which explains my problem.  The bug is in the drivers for the Broadcom BCM4313 wifi chipset, which are contained in the bcmwl-kernel-source package.  (There is a different driver in the broadcom-sta package; I'm not sure if switching drivers would solve my problem or not.)  Anybody else with a similar problem who wants to know if the same bug affects them can go to this web page for help finding out what wifi chipset they have: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) .  Then they can go to this page for instructions on how to find what packages are installed: [http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages) .

So the work-around is to insert a static entry in the ARP cache for all the other computers in the network that need to interact with the affected computer.  For a Windows computer, "arp -h" gives an example of how to do that; for a Linux machine, "man arp" should tell you what you need to know.  Also the affected computer needs to always have the same IP address, either a static IP address or a DHCP reservation, so that the static ARP entry is guaranteed to be correct.  For me there aren't many other computers on my home network, so the work-around isn't much of a hardship.  I did the work-around, and now both ping and Samba seem to work, hooray!

Thanks again for your help houstonbofh, it meant a lot to me that someone cared enough to look into my problem!

---

### Post by houstonbofh on 2013-09-11
If I remember right, I am using the STA drivers on an older Dell I have.  Good luck!  That card is a nightmare!

---

### Post by Manoj_Rk on 2014-03-29
Hi,
Faced the same issue on 12.04 while trying to setup Unified Remote Control. 
Any idea how to go about this on an Android Phone ?
Regards,

---

### Post by rclocher3 on 2014-03-31
Hi Manoj, could you explain more?  Are you trying to ping a Ubuntu machine from an Android phone?  I don't have a smart phone, so I'm not familiar with Android.  Can you get to a command prompt on an Android phone?

---

