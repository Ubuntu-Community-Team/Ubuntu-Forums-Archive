---
title: "DHCP stories"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by Marais on 2010-05-26
Alas Mr. Google is not infallable!
:confused:
After  many days of looking hither tither and yon I ask you my fellow  UBUNTUins for some difficult tech advice.
If this is not the correct  forum please tell me and I'll post it elsewhere.

Now I've set up a  permanent DHCP lease for my MAC address. I did this hoping to resolve  the fact that I share my Internet ADSL connection with my wife and my  daughter (the latter a great bandwidth hog)!

So I was hoping this  would give my connection priority. It seems that is faster but for the  life of me can't find anywhere thanks to Mr. Google on the advantages of  WHY one should set up a permanent lease in the first place.

If  anyone could explain this to me or direct me to the site I've been  looking for, I would greatly appreciate it.

Thirst I have for  knowledge...:KS

---

### Post by puppywhacker on 2010-05-26
DHCP normally works with an expiring lease, the DHCP server defines the maximum lifetime and the DHCP client should after 50% of the time start the renewal process, best explained in pictures, below link paints an fine image.

[URL="http://www.tcpipguide.com/free/t_DHCPLeaseLifeCycleOverviewAllocationReallocationRe.htm"]http://www.tcpipguide.com/free/t_DHCPLeaseLifeCycleOverviewAllocationReallocationRe.htm
[/URL]

Why you would setup a permanent lease is only of benefit that your lease never expires, it does not give you any priority and if a DHCP client and server are behaving well you should have no benefit over an expiring lease. The only benefit is that you can keep the same ip-address for a longer period without worrying that you can not reach your computer from the internet. But you can achieve the same nicer by setting a static address assignment in the dhcpserver if you have full control over the dhcp-server.

If you want to share a connection equally you can split create class-based queue's on the uplink to your provider where your traffic has higher priority over your daughters traffic, unfortunately you can barely control the downlink from your provider. IP works hop-by-hop. traffic shaping can be done with "tc" but it is a bit complicated. An easier solution is to use "squid" as proxy, but this is mainly for HTTP traffic.

---

### Post by Marais on 2010-05-26
Hey thanks alot! Finally a clear answer.
I more or less gleaned this from what I could.
So as they said in the original Godzilla "There's no hope for Tokyo now"! and I'll have to grin and bear up and downloads (unless I throttle my daughter's bitorrent client which I already did for downloading (during the day).
I even set up my own router but that also seems to have no capacities for dividing the pie other than what the server does naturally.

She's 20 and is moving out in a few months so be it. Just rather annoying. :(

---

### Post by lavinog on 2010-05-26
> **Marais said:**
> Hey thanks alot! Finally a clear answer.
I more or less gleaned this from what I could.
So as they said in the original Godzilla "There's no hope for Tokyo now"! and I'll have to grin and bear up and downloads (unless I throttle my daughter's bitorrent client which I already did for downloading (during the day).
I even set up my own router but that also seems to have no capacities for dividing the pie other than what the server does naturally.

She's 20 and is moving out in a few months so be it. Just rather annoying. :(

Why not ask her to throttle her torrents herself?
Some torrent clients even have a scheduler so that torrents only run at times when no one is using the net.

utorrent uses a protocol that automatically gives other traffic priority.
Since this protocol was recently opened, I would assume other clients will start implementing it.

---

### Post by Marais on 2010-05-26
It's really a parenting problem. I don't want to make her unhappy:(
She doesn't know for instance that I throttled her bitorrent client during the day.
We live in France and she likes to watch streaming and downloaded TV shows from the good ol' USA.
I need to work.:confused:
So there is a conflict, and as she's leaving in three months for good I don't want her last three months at home to be sad:(

---

### Post by Iowan on 2010-05-26
I use a static lease for my development server and network printer - they always have the same address, but don't need to be manually configured themselves.  It's also good for a machine that needs a static address at home, but still needs to use DHCP mobile. Good luck with your daughter - "for good" doesn't always mean "good"...

---

