---
title: "Configuring multiple tuners (DVB-T and DVB-T2)"
date: 2013-02-12
forum: Mythbuntu
---

### Post by ceejay on 2013-02-12
I've been running for some time with Myth 0.24 and a Hauppauge dual DVB-T tuner - I am in the UK.

My problem arises from the fact that I have just added a TBS6280 dual tuner card so that I can receive the HD DVB-T2 channels. The driver has been successfully installed, and the card seems to work - my problem is setting up the sources and channels correctly for the two cards / four adapters.

I'm now using Myth 0.25 on Ubuntu 12.04. I understand that I need to set up two sources, one a superset of the other, for the two cards.

The best I've been able to do so far is to run a tuned scan on one of the Hauppauge tuners, specifying just one of the six muxes that I want: miraculously, it seems to get data from that one mux that points it at all the others and I get a very satisfactory scan  - all I need to do is use the Channel Editor to remove the unwanted channels, and all is good - no duplicates.

However, when I try to do the same thing with one of the TBS tuners, it doesn't work. A tuned scan - on any of the six mux frequencies - finds no channels. I can however do a full scan, but then it picks up channels from other transmitters as well as the preferred one - one or two redundant versions of every channel. That meant lots of manually including the duplicates, in many cases with "wrong" channel numbers, because there seems to be no way of telling at this point whether a channel is "good" or "bad".

I was able to get rid of some of the unwanted duplicates by deleting transports that were clearly wrong (I know the frequencies of the six muxes - sadly, by heart!). Then all that I had to do was use the Channel Editor to correct the Channel numbers where necessary (most of them - the "good" channels are at higher frequencies than the "bad" ones).

This is a right pain but it's doable.

BUT - what I still don't understand is that I STILL have a bunch of duplicate channels - mostly the ITV rather than BBC ones - in the "HD" source. How can I tell which of the two I want to keep? The Channel Editor doesn't seem to give any clues.

Is there a better way to do this?

TIA

---

### Post by AlecJ on 2013-02-12
The easiest way is to edit the channels is mythweb. from a laptop on the sofa?

I have 3 sources freesat, freesat HD, Astra 13east.
each card has its connected source that the card can receive, then with mythweb i arrange the channels simlar to how freeview is ..

1 BBC one SE 
2 BBC 2
3 ITV1     etc..

with the BBC HD channels at 99998,99999 so they appear above channel 1 on the tv.

using mythweb you can select many channels and delete altogether and re-number, then scroll to the bottom and click save.

---

### Post by ceejay on 2013-02-12
Good tip, thank you!

---

