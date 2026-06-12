---
title: "Can not build up connection to MS VPN Server"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by mac-duff on 2008-12-19
Hi,
the strange thing is, I can use it without problems out of a XP vmware without changing any settings, but when I try to use the pptp out of the gnome network manager its fails every time. I tried already different settings but I guess now is my account for some minutes/hours blocked

Has anybody still an idea there outside?

---

### Post by jonobr on 2008-12-19
Open a terminal window and try typing 
 tail -f /var/log/messages

open the vpn and see if errors pop up in the terminal  relating to pptp when you try to connect,
also, posting the ifconfig -a may show something of interest.

---

### Post by mac-duff on 2008-12-20
Hi,
thank u for the answer. This is what I get:

Dec 20 18:25:56 mdl kernel: [28323.557962] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Dec 20 18:25:56 mdl kernel: [28323.558556] sd 5:0:0:0: Attached scsi generic sg2 type 0
Dec 20 18:54:17 mdl -- MARK --
Dec 20 19:02:31 mdl kernel: [30517.896304] device eth0 left promiscuous mode
Dec 20 19:02:31 mdl kernel: [30517.897254] bridge-eth0: disabled promiscuous mode
Dec 20 19:03:31 mdl pppd[4763]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Dec 20 19:03:31 mdl kernel: [30577.984173] PPP generic driver version 2.4.2
Dec 20 19:03:31 mdl pppd[4763]: pppd 2.4.4 started by root, uid 0
Dec 20 19:03:31 mdl pppd[4763]: Using interface ppp0
Dec 20 19:03:31 mdl pppd[4763]: Connect: ppp0 <--> /dev/pts/0
Dec 20 19:04:02 mdl pppd[4763]: LCP: timeout sending Config-Requests 
Dec 20 19:04:02 mdl pppd[4763]: Connection terminated.
Dec 20 19:04:02 mdl pppd[4763]: Modem hangup
Dec 20 19:04:02 mdl pppd[4763]: Exit.

---

### Post by vckeating on 2008-12-20
Hi, 

I don't mean to hijack the thread, but I'm also having issues connecting to a PPTP VPN that otherwise works fine on an XP machine. I'm hoping that you might be able to kill two birds with one stone.  Here's what I get from the tail -f /var/log/messages:

```
Dec 20 15:44:49 chuck-laptop pppd[8843]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Dec 20 15:44:49 chuck-laptop pppd[8843]: pppd 2.4.4 started by root, uid 0
Dec 20 15:44:49 chuck-laptop pppd[8843]: Using interface ppp0
Dec 20 15:44:49 chuck-laptop pppd[8843]: Connect: ppp0 <--> /dev/pts/2
Dec 20 15:44:51 chuck-laptop pppd[8843]: LCP terminated by peer (H&^Es^@<M-Mt^@^@^BM-3)
Dec 20 15:44:54 chuck-laptop pppd[8843]: Connection terminated.
Dec 20 15:44:54 chuck-laptop pppd[8843]: Modem hangup
Dec 20 15:44:54 chuck-laptop pppd[8843]: Exit.

```

and ifconfig -a results in:

```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:77:80:9f  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe77:809f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:39062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40641289 (40.6 MB)  TX bytes:5329030 (5.3 MB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16311 (16.3 KB)  TX bytes:16311 (16.3 KB)

pan0      Link encap:Ethernet  HWaddr c6:e7:08:59:cd:35  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a5:67:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-A5-67-6A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Thanks!

---

### Post by jonobr on 2008-12-20
vckeating Shame on you, take yourself into the corner and give yourself a good talking to.... [-X

Just kidding :guitar: , unlike other threads I have seen , where people say ,
"I have exactly the same issue" and then another says "so do I" and both describe completely different experiences,
I think yours are the same.


From both of your logs it appears both are failing at the same point , LCP negotiation.

The starting phase of PPP (point to point protocol which sends packets over a link) includes LCP  and IPCP negotiation.
Your both dealing with failed LCP negotiation.

LCP , step 1, checks the remote device and accepts or rejects the other device , it determines the acceptable packet size for transmission,  config errors and will terminate if both ends disagree,
If they agree, the negotiation moves to IPCP which you are not going to. IPCP ,If I recall rightly involves the exchange of username + passwords, so this appears to be unrelated to password problems 
They will never go to IPCP if the LCP stage determines the link is not acceptable.

Im guesing the VPN is built on ETH0 and the MTU size of that is used for LCP negotation.
VPNs cause trouble for MTU and I think this is whats going on when your PPTP is trying to negotiate.

Looking at your ifconfig your MTU is 1452 or so, but for ETH thats usually 1500.
Im wondering if you changed this or it is just that way from initial config.

I would recommend a temporary change of MTU to 1500.
Try another connection and see if the logs go further.

I would also recommend disabling all things IPV6 as you are  not using them and it could be slowing down your internet config.

I would recommend against changing MTU to anything other then that recommend and if 1500 works, I would strongly recommend checking your other connections torrents , download and surfing speeds etc......

If things are not good or better I would recommend changing back.

mac-duff could you check your ifconfig MTU also?

Cheers all

---

### Post by mac-duff on 2008-12-21
Hi,
I am sorry, but I have no idea what u r talking about :(

But my MTU size is also 1500 without changing something

---

### Post by vckeating on 2008-12-21
Hey there, 

I reset the MTU but I'm still not getting any love.  Here's what things look like now:

```
Dec 21 08:17:53 chuck-laptop -- MARK --
Dec 21 08:37:16 chuck-laptop pppd[7048]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Dec 21 08:37:17 chuck-laptop kernel: [ 2392.718195] PPP generic driver version 2.4.2
Dec 21 08:37:17 chuck-laptop pppd[7048]: pppd 2.4.4 started by root, uid 0
Dec 21 08:37:17 chuck-laptop pppd[7048]: Using interface ppp0
Dec 21 08:37:17 chuck-laptop pppd[7048]: Connect: ppp0 <--> /dev/pts/1
Dec 21 08:37:19 chuck-laptop pppd[7048]: LCP terminated by peer (8M-^LgG^@<M-Mt^@^@^BM-3)
Dec 21 08:37:22 chuck-laptop pppd[7048]: Connection terminated.
Dec 21 08:37:22 chuck-laptop pppd[7048]: Modem hangup
Dec 21 08:37:22 chuck-laptop pppd[7048]: Exit.
```

```

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:77:80:9f  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe77:809f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3427093 (3.4 MB)  TX bytes:687402 (687.4 KB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5262 (5.2 KB)  TX bytes:5262 (5.2 KB)

pan0      Link encap:Ethernet  HWaddr 46:ec:92:65:9e:25  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a5:67:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-A5-67-6A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

As for disabling IPV6, I wasn't quite sure what this meant but I found a post [here]("http://ubuntuforums.org/showpost.php?p=4891172&postcount=2") that seemed to describe what you were talking about.  Unfortunately this didn't seem to help, as you can see above.  Oh, and tThe MTU is the original from the install - I haven't touched it.  

Any other suggestions would be appreciated!  :)

---

### Post by mpokrywka on 2008-12-21
Add "debug" option (checkbox) in NM vpn settings, try to connect and then paste /var/log/messages, use **tail -n 100 /var/log/messages** because there may be more debug lines

---

### Post by jonobr on 2008-12-22
Also, do you guys have access or can you get assistance from the MS end of things?

---

### Post by vckeating on 2008-12-24
> **mpokrywka said:**
> Add "debug" option (checkbox) in NM vpn settings, try to connect and then paste /var/log/messages, use **tail -n 100 /var/log/messages** because there may be more debug lines

Hey, thanks for the help.  Unfortunately there doesn't seem to be a debug checkbox anywhere in the VPN settings in Network Connections.  I'm pretty sure that I've checked everywhere.  Any idea?

---

