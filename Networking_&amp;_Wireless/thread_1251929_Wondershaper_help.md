---
title: "Wondershaper help"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2009-08-28
hi all i have just installed wondershaper which is used to limit and shape bandwidth.

i have got it all running good i have tuned my internet download speed to only 220kb/s which is all working ok..

but i have just remembered i have a NAS drive on my network and wondershaper shapes all bandwidth.

i was just wondering if i can shape my bandwidth from just the gateway and not shape traffic from the internal network??

thanks

---

### Post by yota on 2009-08-28
Hi,

I had a similar problem and ended in making myself a modified version "wlanshaper.sh" which is able to exclude a subnet from traffic shaping (it's in attachment).

The core of the fix is:
```

tc filter add dev $DEV parent ffff: protocol ip prio 1 u32 \
    match ip src $LAN_SUBNET/24 \
    match ip dst $LAN_SUBNET/24 \
    flowid :1

```
which I took from this work (sabishape is interesting, but less straightforward than wondershaper IMHO):
[http://packages.pardus.org.tr/info/2009/stable/source/sabishape.html](http://packages.pardus.org.tr/info/2009/stable/source/sabishape.html)

Don't forget to tune all the variables to suite your environment!

---

### Post by elliotbeken on 2009-08-28
wow i wish i could do that stuff lol

but how do i add this or set it all up 

thanks

---

### Post by yota on 2009-08-28
[LIST=1]
[*]download the attached script
[*]copy it under /usr/local/bin
[*]make it executable (sudo chmod +x /usr/local/bin/wlanshaper.sh)
[*]edit the following section of the script to match your environment/need
[/LIST]

```

#Local Network
LAN_SUBNET=192.168.0.0

# low priority OUTGOING traffic - you can leave this blank if you want
# low priority source netmasks
NOPRIOHOSTSRC=

# low priority destination netmasks
NOPRIOHOSTDST=

# low priority source ports
NOPRIOPORTSRC="4662 4663 4664 4665 4667"

# low priority destination ports
NOPRIOPORTDST="4662 4663 4664 4665 4667"

```

So if you are in a 192.168.1.* network you should put 192.168.0.0, and so on.

Hope this helps!

p.s. you should never download and execute scripts made by strange, unknown individuals... well... like me! ;-)

---

### Post by own3mall on 2013-03-29
Author's original fix is outdated.  The WonderShaper script has been updated to NOT filter LAN traffic properly for the latest Ubuntu versions (fix posted below works in 11.10).  

Check out the guide here:  [http://blog.eamster.tk/?p=166](http://blog.eamster.tk/?p=166) (Exclude LAN from Speed Limits Section)

Hope it helps someone!

---

### Post by oldos2er on 2013-03-29
Old thread closed.

---

