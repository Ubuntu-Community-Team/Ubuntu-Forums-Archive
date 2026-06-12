---
title: "[SOLVED] Windows can see Ubuntu netbios names but not acces or even ping"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by ottokruse on 2008-12-09
Hi All,

Yet another variant to the wealth of name resolution threads...

Situation:
Ubuntu 8.10
Samba Server acting as WINS and file server
All Windows clients are setup with the reference to the WINS server
nsswitch.conf setup: files wins dns
smb.conf setup: lmhosts wins host bcast
If I use IP adresses all works fine so it's clearly a name resolution issue
Also bind9 DNS is installed (don't know if this matters)

Problem:
Here's the funny thing: when my I browse the local network on my windows machine I can see the server (called ubuntuserver1). So somehow my windows pc can resolve the name. But when I try to access it (by double clicking) windows complains it cannot find the name. Also ping ubuntuserver1 does not work.

It seems netbios name resolution works fine for some applications (browse) but not for others (ping, access).

This used to work fine a while ago, also in 8.10. But for some odd reason it doens't any more and I haven't even touched samba setup. Is this a regression in the new samba version propagated a few weeks ago?

Note: Name resolution works fine for other linux machines in the network. So it has something to do with Windows (both XP and Vista) compatibility.

Help is highly appreciated, I have been breaking my head on this...

Thanks!

---

### Post by ottokruse on 2008-12-10
I've solved this issue --> it proved to be a firewall issue. My iptables policies were the cause. See below mail discussion:

---
Thanks for the feedback. I am wondering indeed then how the local
master browser got wind of it..

I found out the cause and solution for the problem as well..  turned
out to be a firewall issue. The system is running Firestarter but also
Shorewall is installed. Now Shorewall is 'only' a utility to update
iptables policies and I hadn't actually run it so I figured my
iptables policy would have remained unchanged. But as it seems the
installation of shorewall already created some iptables policies... I
deleted them and set new policies to accept all (and let firestarter
do the firewalling) and now my windows pc resolves the netbios name of
the server again. Whoa!

Interesting to note is that name resolving from other linux machines
worked ok, e.g. wasn't affected by the iptables policies. Only windows
machines weren't able to pass through iptables policies for name
resolving. That's nasty I think, seems to me you would not expect this
difference....

Regards Otto
- Hide quoted text -


On Tue, Dec 9, 2008 at 10:09 PM, Volker Lendecke
<Volker.Lendecke@sernet.de> wrote:
> On Tue, Dec 09, 2008 at 03:21:37PM +0100, Otto Krüse wrote:
>> Here's the funny thing: when my I browse the local network on my
>> windows machine I can see the server (called ubuntuserver1). So
>> somehow my windows pc can resolve the name. But when I try to access
>> it (by double clicking) windows complains it cannot find the name.
>> Also ping ubuntuserver1 does not work.
>
> The fact that "ubuntuserver1" shows up in the list of
> machines in your workgroup does not mean that you can "see"
> it yourself. It means that your local master browser somehow
> got wind of it.
>
> Volker
>
---

---

