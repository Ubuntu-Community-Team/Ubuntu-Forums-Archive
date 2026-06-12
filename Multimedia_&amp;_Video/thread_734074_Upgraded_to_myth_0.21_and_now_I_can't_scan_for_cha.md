---
title: "Upgraded to myth 0.21 and now I can't scan for channels"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by agnesdavies on 2008-03-24
I am running a 64 bit mythbuntu setup, with a Hauppauge DVB-S (actually, two, but I've taken one out) card.

Somewhere along the way, I found that mythbuntu was "stuck" on one broadcast channel. A very nice channel, admittedly, but it got a bit tedious, so I tried to fix it.

Since I thought I may have botched it somewhere by setting lots of channels invisible in mythweb, I though I'd clear the lot down and reload them.

Bad move.

I don't know whether it's because mythtv has been upgraded to 0.21, but if I try to channel scan in MythTV by putting in the initial frequency, polarisation and bit rate from the Astra-28.2E file, it just flickers briefly and then gives me an empty channel list. I know the card works, because I've used scan on the command line to generate a channels.conf file which I have also used from within mythtv to try and load the channels...also to no avail.

I'm at my wits' end now - I even tried uninstalling and reinstalling all the myth packages, but that didn't help, either. I'd consider clobbering the mythconverg database if I thought it would help (and if I could be sure I could get mythtv reinstalled without having to go back to bare iron).

Anyone encountered this? Any quick (or even slow) fixes? There's a household here beginning to have some severe doubts about this whole having-a-PC-to-watch-the-telly with, so my credibility's hanging in the balance here... :(

Update: by deinstalling all the mythtv packages, and manually dropping the mythconverg database, then reinstalling mythtv, I am at least getting it a) to run on a rather more convenient VNC session, and b) do Meaningful Things when I try to channelscan. It's about 10% of the way through one now, so fingers crossed - this may have got it going...

---

### Post by agnesdavies on 2008-03-25
Progress update

OK, now I can scan, either from a channels.conf file, or by putting in the frequency, polarisation and bit rate.

Unfortunately, the end result is the same: mythtv sees no channels.

*grr*

---

### Post by sofasurfa on 2008-06-26
I have a similar thing. Since Mythbuntu 8.04 I can't import channels.conf or scan on some transponder (not sure which one.) Myth just disappears. I'm using a Twinhan DVB-S clone card which may or may not be significant. There was no problem producing the channels.conf using dvb-utils and Mythbuntu 7.10 scanned ok too. I'm also looking at Astra 28.2E so I suspect there's some combination of Myth 0.21 and something streaming from that satellite causing my tale of woe. I don't really want to downgrade because there are XMLTV issues for me on 7.10 but if nobody has a fix I'll have to :(.

---

### Post by sofasurfa on 2008-06-26
Oh, I should have mentioned I'm on 32-bit - not 64. I doubt that's important in this case though.

---

