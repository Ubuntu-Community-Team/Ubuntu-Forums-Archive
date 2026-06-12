---
title: "lost all nine networks channels"
date: 2009-08-13
forum: Mythbuntu
---

### Post by owenspa on 2009-08-13
I get digital tv from the Upwey tower on the outskirts
of Melbourne, Australia.

The nine network recently made changes and introduced a new channel.
Subsequently I cannot get mythtv to lock on any of the nine network
channels, all the other networks are fine.

I'm running Kubuntu 8.04 (Hardy) and I have a  DViCO FusionHDTV DVB-T Dual Digital 4 Rev 1 card.  I've attempted to load later versions of its
driver to no avail, and reconfigured mythbuntu numerous times.  I
still cannot get a lock on any of the nine network channels.

However, using testing instructions from a Howto for my DVB card,
as root I used

```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne-Upwey > /etc/channels.conf
cp /etc/channels.conf ~/.tzap
tzap -c /etc/channels.conf -r "Nine Digital"
```

then as a normal user in a different window

```
mplayer /dev/dvb/adapter0/dvr0
```

and there is the "Nine Digital" channel live!!

I'm guessing that I'm missing a mythbuntu configuration stage or there is
some tuning/scanning data that is not being replaced when I rescan.

Scanning the tuners in mythtv finds the channels OK, they just wont
lock for viewing or recording.

Any suggestions?

---

### Post by klc5555 on 2009-08-13
> **owenspa said:**
> 
Any suggestions?

Maybe, since your channels.conf file works, you might want to see if mythtv can tune the channel after you have imported the channels.conf in Input Connections, rather than doing a standard scan.

---

### Post by owenspa on 2009-08-13
> **klc5555 said:**
> Maybe, since your channels.conf file works, you might want to see if mythtv can tune the channel after you have imported the channels.conf in Input Connections, rather than doing a standard scan.

I can't see any way to import this file.

In my hunt through the setup dialogues I came across the "Transport Editor" under "5. Channel Editor".  I don't understand what all the numbers mean, except what is obviously the transmission frequency for each network.

There are 12 transports listed, I suspect only 5 are required to match the available networks.  All the frequencies in the "channels.conf" file are included.

I suspect that these two entries are significant.

```
QAM-64 191625000 Hz netid 4114 tid 1072 (DVB-T)
QAM-64 641500000 Hz netid 12829 tid 1072 (DVB-T)
```

The second line shows the frequency for the Nine Network.  Is it possible that the last number on each line (1072) is a key, and that attempts to tune to a Nine Network channel are using the wrong frequency because its first in the list?

Are the extra entries in this list useful, can I delete them?

---

### Post by klc5555 on 2009-08-14
In Input connections, under the page for your input connection, once you have clicked the option for "Scan for channels" pulls up a page where you set the options for the scan. Instead of "Full Scan", one of the options is for importing a channels.conf

This is where you start before trying the thankless task of editing transports and frequency settings in the channel editor.

---

### Post by owenspa on 2009-08-14
> **klc5555 said:**
> In Input connections, under the page for your input connection, once you have clicked the option for "Scan for channels" pulls up a page where you set the options for the scan. Instead of "Full Scan", one of the options is for importing a channels.conf

This is where you start before trying the thankless task of editing transports and frequency settings in the channel editor.

Thanks for that.  It found the channels OK, but the first time I did it I ended up with 5 transports each with 0 Hz frequency. Of course then I could not lock to anything.

Second attempt I ended up with 6 transports, the first was a runt with 0 Hz and no tid etc.  The other 5 all had frequencies but only 1 I recognized.  Fortunately I kept a record of what was there before and was able to match the tid's to the TV Networks.

So, I edited the frequencies for all the transports to match those in the channels.conf file for the corresponding TV networks.

Hey Presto!   I can now lock to all channels of all the networks.

Thankyou very much for your help.:)

---

