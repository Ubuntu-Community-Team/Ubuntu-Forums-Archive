---
title: "Samba issue"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by ShinHadoken on 2010-07-26
*sigh* So sick of this. Samba has consistently plagued me from the moment I began using Ubuntu two or so years ago.

So, I set up a share, my Public folder in my home folder. All my Windows computers can see it. Sounds great right? Problem is, I can't see the Windows computers. I go into Nautilus, click Network, and I see Windows Network. Clicking on it cause Nautilus to hang for about two and a half minutes, before finally informing me that it couldn't retrieve the share list from the server. This is the same when looking for a Windows printer in the print dialog (System>Admin>Printing) Also, I don't have this problem at all when running a Live CD, my Vista partition, or when I am using a hard-wired connection. Only when booted into my Ubuntu partition (10.04) using my wlan do I have this issue. Can anyone offer any insight?

Much appreciated,

SH

---

### Post by yoshi121212 on 2010-07-26
I had a similar problem that I fixed by changing my DNS server. Since it works with a hard-wired connection, something is just funny about the WLAN one. The hanging that you describe could easily be caused by the packets destined for the network share just not finding a route and eventually timing out. If everything is connected to the same wireless router, it might be easily fixed by making the router the primary DNS server.

---

### Post by pricetech on 2010-07-26
Can you connect to the windows shares by IP address ??

---

### Post by ShinHadoken on 2010-07-26
> **yoshi121212 said:**
> I had a similar problem that I fixed by changing my DNS server. Since it works with a hard-wired connection, something is just funny about the WLAN one. The hanging that you describe could easily be caused by the packets destined for the network share just not finding a route and eventually timing out. If everything is connected to the same wireless router, it might be easily fixed by making the router the primary DNS server.
Alright, that fixed it. I've been using OpenDNS servers lately. All is well! But, does this mean I can't use OpenDNS? I use OpenDNS on my Windows PCs, and they work just fine.

---

### Post by CharlesA on 2010-07-26
Just set the router to do local dns and use open dns as secondary.

---

### Post by lisarox on 2010-07-27
> **CharlesA said:**
> Just set the router to do local dns and use open dns as secondary.
and that could be easily done by....?:popcorn:

---

