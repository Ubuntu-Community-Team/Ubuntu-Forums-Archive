---
title: "rescan dvb-s advice"
date: 2009-12-28
forum: Mythbuntu
---

### Post by stevanbt on 2009-12-28
Hi,
I'd like to rescan for channels on our dvb-s mythbackend box and have a couple of questions (I'm intending doing ```
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
``` and importing them into mythtv):-

[LIST]
[*]What will happen to the existing recording schedules?  Will I need to reapply them or will they work after the rescan?

[*]and the first time I did the channel scan I ended up with BBC 1 Channel Islands, BBC 1 North West, BBC 1 Scotland etc.  Is there an easy way to remove all the multiple BBC, ITV channels?
[/LIST]

Any other gotchas? 

Thanks in advance, Steve.

---

### Post by ian dobson on 2009-12-28
Hi,

With regards to the multiple channels, they are all there unless a channel has moved (then you'll have the old one and the new one). On my system I just imported all the channels from channel.conf then set the ones I don't want to invisible. This means that when I scan/import next time only the channels that are new will show up and the ones I don't want just stay invisibe.

As long as the channel ID's don't change your schedules should be OK. If you have a schedule defined on a channel that has moved you'll need to edit/re-schedule it.

regards
Ian Dobson

---

