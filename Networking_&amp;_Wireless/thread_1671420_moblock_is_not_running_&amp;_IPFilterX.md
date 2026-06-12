---
title: "moblock is not running &amp; IPFilterX"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by TheNomad on 2011-01-20
For the past couple of day I am unable to start moblock. I am getting :


 * moblock is not running
 * blockcontrol.wd is running


I searched the forums and found a reference to IPfilterX being the cause of this problem with IP addresses starting with leading zeros and moblock not liking this format. 

Despite how many different searches I made using forum and using google in general, I am unable to find anything to this ipfilterx as in either how to disable it or modify the format (if possible)

Can someone direct me where to look. I am quite lost. I am not even sure if this is the source of my problems. 

When I start blockcontrol while watching the log with tail -f, I see no error messages but when I check the pid file, the PID in this file is not running immediately after start process completes. 

Can anyone give me any pointers ?

Thanks in Advance

---

### Post by jre on 2011-01-20
You can disable this list the same way, as you enabled it (per default it is not enabled).
Just edit (with root rights) /etc/blockcontrol/blocklists.list and remove the line with the URL.

Which update URL do you use for IPFilterX? I just checked iblocklist.com and there it seems to be ok (.p2p format with no leading 0)

---

### Post by jre on 2011-01-20
[deleted double post]

---

### Post by TheNomad on 2011-01-20
Okay, I must have been smoking something. Today, I launched the moblocker from the gui (I always do command line) and checked the enabled block lists. IPfilterX is not even there let alone being disabled or enabled.

The status log is as follows:

```

Current IPv4 iptables rules (this may take a while):
Chain INPUT (policy ACCEPT 198K packets, 23M bytes)
pkts bytes target prot opt in out source destination
8 799 blockcontrol_in all -- * * 0.0.0.0/0 0.0.0.0/0 state NEW mark match !0x14
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination
0 0 blockcontrol_fw all -- * * 0.0.0.0/0 0.0.0.0/0 state NEW mark match !0x14
Chain OUTPUT (policy ACCEPT 267K packets, 373M bytes)
pkts bytes target prot opt in out source destination
2 487 blockcontrol_out all -- * * 0.0.0.0/0 0.0.0.0/0 state NEW mark match !0x14
Chain blockcontrol_fw (1 references)
pkts bytes target prot opt in out source destination
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0 mark match 0xa
0 0 RETURN all -- * * 0.0.0.0/0 192.168.0.1
0 0 RETURN all -- * * 192.168.0.0/24 192.168.0.0/24
0 0 NFQUEUE all -- * * 0.0.0.0/0 0.0.0.0/0 NFQUEUE num 92
Chain blockcontrol_in (1 references)
pkts bytes target prot opt in out source destination
0 0 DROP all -- * * 0.0.0.0/0 0.0.0.0/0 mark match 0xa
0 0 RETURN all -- lo * 0.0.0.0/0 0.0.0.0/0
2 487 RETURN all -- * * 192.168.0.0/24 0.0.0.0/0
6 312 NFQUEUE all -- * * 0.0.0.0/0 0.0.0.0/0 NFQUEUE num 92
Chain blockcontrol_out (1 references)
pkts bytes target prot opt in out source destination
0 0 REJECT all -- * * 0.0.0.0/0 0.0.0.0/0 mark match 0xa reject-with icmp-port-unreachable
0 0 RETURN all -- * lo 0.0.0.0/0 0.0.0.0/0
0 0 RETURN all -- * * 0.0.0.0/0 192.168.0.1
2 487 RETURN all -- * * 0.0.0.0/0 192.168.0.0/24
0 0 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:21
0 0 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:22
0 0 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:443
0 0 RETURN tcp -- * * 0.0.0.0/0 0.0.0.0/0 tcp dpt:80
0 0 NFQUEUE all -- * * 0.0.0.0/0 0.0.0.0/0 NFQUEUE num 92
Please check if the above printed iptables rules are correct!
* moblock is not running
* blockcontrol.wd is running
PID: 29830 CMD: /bin/sh /usr/bin/blockcontrol.wd

```

This might as well  be in Swahili as my understanding for both are pretty much the same. Any gaping failures looking at my face that I am not seeing ?

Thanks again

---

### Post by jre on 2011-01-21
Have you checked moblock.log AND blockcontrol.log?

If it is blocklists related, you may post your /etc/blockcontrol/blocklists.list

The watchdog is running and the correct iptables rules exist - so moblock (the daemon) was started before, but must have crashed later.

---

### Post by Spartan23 on 2012-01-17
ipfilterX is now out with a 2nd version !
We split from iblocklist at november 2011 , if there are here ours users please reach us 
via eMail or IRC .

Thank you .

---

