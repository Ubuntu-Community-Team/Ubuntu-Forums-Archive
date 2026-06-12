---
title: "Mythbuntu 8.10 HVR-1300 (MyFirst Forum Appearance)"
date: 2009-01-24
forum: Mythbuntu
---

### Post by skyhopper on 2009-01-24
HI members!

I am absolutely new to this forum and I'm happy to be here. I'm from the north of Germany and I'm 29 Years old. I am looking forward to take part in this forum and learn from my mistakes.

I am also new in setting up an htpc and I have chosen Mythbuntu because I'm an Ubuntu-User since 2005.

I'm trying to set up a small htpc mit Mythbuntu 8.10 on a P4-2.8GHz, 1GB of RAM, a 256MB FX5500 TV-Out.
I have completed the setup but now a problem occurs. I can't find any channels. I think, it uses DVB-T to find the channels, wich the card supports. But it also supports analog cable TV and this is the mode that I want to use.
Is there a possibility to tell mythbuntu, that it should scan on cable TV instead on DVB-T?

Thank you very much for your help because I really do need a success at this stage...this winds me up :-)

cheers
Torsten!

---

### Post by joshoekstra on 2009-01-25
AS i understand it, it's a dualtuner card with DVB-T and analog. If the card is recognized under linux there should be a /dev/videoX device, you add that card as probably v4l. After that it should be possible to run a channel scan.
If that doesn't work it's probably possible as well to set up a video-source as well and change the channelfrequencies reflecting your area.

---

