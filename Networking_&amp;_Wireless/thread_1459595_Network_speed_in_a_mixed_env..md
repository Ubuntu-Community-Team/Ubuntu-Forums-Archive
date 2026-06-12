---
title: "Network speed in a mixed env."
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by TitanusEramius on 2010-04-21
Hi guys (and maybe girls?)

I can say that I am sorry in advance for posting a dumb question like this but I simply can't find the answer this time.

When the summer-holidays are a fact and it's time for some fun I will be upgrading my home network with a diskstation of some kind, and since all models I currently looks at supports 10/100/1000 M/Bit networking it got me thinking. 

My desktop also supports 10/100/1000 M/Bit networking and since I already uses a 10/100 M/Bit switch between my desktop and (file)server, it would be very easy to buy a new switch that also supports 1000 M/Bit networking and then connect the diskstation to that switch as well. But the router the new switch will be connected to is only running 10/100 M/Bit so the question is, at what speed will the new switch be running?

---

### Post by dannyboy79 on 2010-04-21
im pretty sure switches have auto-sensing (auto-negotiation capabilities) so if the switch is connected to devices that have 1000 M/Bit ethernet cards in them they'll use that speed. Meaning everything connected to the switch will be using 1000 M/Bit so within your home network you should see great speeds. however anything beyond (internet/outside world) you'll still be using the 100 M/Bit router.

that's as long as your setup is like this

modem
  ^
  ^
  ^
100 M/Bit router
  ^
  ^
  ^
1000 M/Bit switch  >>>>>  computers and disk station

---

### Post by lisati on 2010-04-21
My $0.02:

I don't see any real advantage to installing a 1000 M/Bit capable card if your router can only handle up to 100 - among other things, the maximum network speed is usually constrained by the fastest speed that the slower components can handle. Unless, of course, you plan on upgrading/replacing your router at some point in the not too distant future.

---

### Post by P4man on 2010-04-21
ASCII art!

Am I getting this right:

```
PC [COLOR="Red"]-> [/COLOR]switch [COLOR="Red"]<-[/COLOR] NAS
      [COLOR="Green"]  / \
         |
         |[/COLOR]
        router to internet
```

Red being Gbit and green 100Mbit ? If so, it should work fine on any decent switch, and you should have Gb speeds where it matters (between PCs and the NAS).

---

### Post by TitanusEramius on 2010-04-21
Thanks for the replies, I`ve been looking for this info for weeks now.

The discstation (NAS) I am thinking of buying is capable of running a torrent-client, so from time to time I will have to move some large files between the NAS and my desktop. And since a 1000 M/Bit switch only costs around 40$ flat I would really like to take full advantage of the hardware.

Also, thanks for pointing out the high-speed only will be within the LAN, not WAN, I should have been more specific in my post.

Very nice ASCII :P

---

### Post by P4man on 2010-04-21
I think lisati misread your question. There is absolutely no doubt a gbit switch is worth it if you use the NAS for more than sporadic backups. 100 Mbit is painfully slow (realworld, 8-10 MByte/s or so?).

Mind you, Im looking at a cheap Dlink DNS 323 NAS, which has "gigabit" lan, but struggles to exceed 20MB/s even when configured in RAID 0. I guess this link might help get you an idea if its worth it for a particlar NAS:
[http://www.smallnetbuilder.com/component/option,com_nas/Itemid,190](http://www.smallnetbuilder.com/component/option,com_nas/Itemid,190)

But just to have gigabit between my PCs, id pay for a Gbit switch.

---

### Post by TitanusEramius on 2010-04-22
> **P4man said:**
> I guess this link might help get you an idea if its worth it for a particlar NAS:
[http://www.smallnetbuilder.com/compo...nas/Itemid,190]("http://www.smallnetbuilder.com/component/option,com_nas/Itemid,190")
Thanks, that list is absolutely perfect for reference before I makes up my mind about the discstation!

I am sorry to hear about the D-Link, i'll guess it was a good idea to start this thread then. And yes, the speed of a 100 M/Bit network is = 12.5 mb/s minus the overhead, so normal operations are newer above 10 mb/s... That is indeed extremely slow if you are moving a couple of DVD's around the network. Thanks again for the advices, it's gonna be a fast summer I guess :P

Btw, some reading on D-Link:
[http://www.theregister.co.uk/2006/04/13/d-link_time_row_escelates/](http://www.theregister.co.uk/2006/04/13/d-link_time_row_escelates/)

---

