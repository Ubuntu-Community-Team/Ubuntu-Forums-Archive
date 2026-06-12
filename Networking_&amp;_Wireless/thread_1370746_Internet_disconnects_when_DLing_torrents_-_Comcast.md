---
title: "Internet disconnects when DLing torrents - Comcast or computer issue?"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by GammaPoint on 2010-01-02
I think the problem started when I began using Karmic. It seems that when I download torrents with transmission my internet will disconnect, reconnect, disconnect, etc. The problem doesn't occur if I'm using the internet to say, browse the web or to SSH to a remote machine. 

Could this be a problem on my end, or might it be some sort of thing implemented by Comcast (my cable "provider")? The reason that I suspect it might have something to do with Comcast is that the problem only seems to occur during hours like 8 AM-5 PM, and doesn't occur at later times like at night, which makes me think it is some sort of policy for "peak hours". Any thoughts about why this might be?

Thanks in advance :)

---

### Post by GammaPoint on 2010-01-02
Additionally, let me add that when I am experiencing problems, all I have to do is pause my torrents and the problems will go away. So it's definitely related to the torrents (or perhaps for simply using up a certain amount of bandwidth).

---

### Post by darco on 2010-01-02
Well maybe a year ago you could have justly pointed your finger at Comcast as they did throttle p2p but since have had their hands slapped by the FCC. Today, their policy is as long as the nodes in your area are not congested, it will allow you to u/l w/o issue. D/L has never been an issue. 
I would try another bit torrent app like Deluge.

darco

---

### Post by GammaPoint on 2010-01-02
> **darco said:**
>  Today, their policy is as long as the nodes in your area are not congested, it will allow you to u/l w/o issue


Thanks darco. I usually upload at 80 kbps. Perhaps if the nodes in my area are congested during peak hours this could be responsible for the shutoff? Maybe I'll give Deluge a try as well.

Best,
GP (from the other side of the Bay)

---

### Post by darco on 2010-01-02
> **GammaPoint said:**
> Thanks darco. I usually upload at 80 kbps. Perhaps if the nodes in my area are congested during peak hours this could be responsible for the shutoff? Maybe I'll give Deluge a try as well.

Best,
GP (from the other side of the Bay)

Raider fan? ";)

---

### Post by GammaPoint on 2010-01-02
> **darco said:**
> Raider fan? ";)

Don't follow football much anymore, but growing up I was a huge 49er fan, especially in the Montana/Young/Rice days :)

---

### Post by FiReSTaRT on 2010-02-16
I just wanted to note that I am getting the same issue when running Transmission and that it also just started with Karmic. The issue didn't exist while running Jaunty. At first I thought it was a networking hardware issue, so I migrated the networking gear closer to where the computers are being used 99% of the time. Since that didn't help, I started looking into which packages mess with my connection. It's only unstable when Transmission's open. I'll try other torrent clients to see if it's client-related or Karmic-related.

---

### Post by pirateghost on 2010-02-16
99.9% of the time its the cheap SOHO router that causes this.  too many connections and it crashes the tables on the router.  Linksys used to be horrible about this.

[http://www.google.com/search?q=torrents+crash+router&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=torrents+crash+router&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by FiReSTaRT on 2010-03-23
You are correct. As soon as I downgraded the firmware, the issue disappeared. Now I have to wait for a specific distro of OpenWRT to come out for my new router (a week tops), but the problem has been temporarily fixed.

---

