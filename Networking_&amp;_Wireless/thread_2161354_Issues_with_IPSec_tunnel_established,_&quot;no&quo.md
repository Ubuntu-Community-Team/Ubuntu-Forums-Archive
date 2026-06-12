---
title: "Issues with IPSec: tunnel established, &quot;no&quot; traffic going through"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by Criena on 2013-07-10
Hi,

I have a weird problem with IPSec. I searched the Internet for days now, tried different things, but all without the much desired success. I hope somebody here is able to give me a clue or little hint on it.

Currently I'm using a Raspberry Pi (RPi) to terminate an IPSec tunnel to another location. The system is running on "Raspbian" (aka Debian Wheezy). I intend to replace the system by a newly purchased Beaglebone Black (BBB). I installed Ubuntu 12.04 and configured the system identical to the RPi (setkey and racoon).  The tunnel is being established, no errors whatsoever, both sides say that the tunnel is up, but no traffic is going through (i.e. I see packets crossing the tunnel, but they seem to just disappear to nowhere).
I grazed the Internet for days now and haven't found any clue why this is the case.  I'm close to giving up as I have no idea anymore what to do.

Based on research on the Internet I tried the following things (obviously without any luck):

   
[LIST]
[*]Added a route manually (even though on the RPi it works without setting any routes) 
[*]Changed the encryption algorithm (from AES to 3DES) 
[*]Changed the hash algorithm (from SHA1 to MD5) 
[*]Turned off NAT traversal (I prefer having the tunnel running via UDP though) 
[/LIST]

  If I ping a machine on *"the other side"* and sniff what is happening within the tunnel on both, the RPi and the BBB, I see the following:

[INDENT]**RPi**: ESP packets are going to *"the other side"* and packets are coming back. Ping and any other communication is working properly.
**BBB**: ESP packets are going to *"the other side"*, but no packets are coming back.
[/INDENT]

If I start a ping from *"the other side"* to my side, the BBB shows ESP packets coming in, but somehow they are not processed. No answers are received back, nor are any reply packets sent.  To me it looked like some ruleset might block everything. I installed iptables and ... no rules defined, default policy is "ACCEPT".

This is so unsatisfying! And I have no clue what the problem might be.  I really hope someone can shed some light into this behaviour.

Thanks
Criena

---

### Post by Whoopie on 2013-07-11
Did you try to set "net.ipv4.conf.default.rp_filter" to 0 in /etc/sysctl.d/10-network-security.conf?

This is a common issue with IPSec, see [Launchpad bugreport]("https://bugs.launchpad.net/ubuntu/+source/ike/+bug/465736").

---

### Post by Criena on 2013-07-11
Hi Whoopie,

I just checked it, set all rp_filter entries to 0, but no success for the tunnel. :-(

---

### Post by Whoopie on 2013-07-11
Did you restart your PC or run "sudo service procps start"? I'm not quite sure regarding the service command, so a reboot is the better choice, I guess.

---

### Post by Criena on 2013-07-11
I set it directly via

*echo 0 >/proc/sys/net/ipv4/conf/*/rp_filter*

But I now also put it into /etc/sysctl.conf and did a reboot - just to have tried everything. No luck though.

---

