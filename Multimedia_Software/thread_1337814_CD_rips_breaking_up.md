---
title: "CD rips breaking up"
date: 2009-11-25
forum: Multimedia Software
---

### Post by The Cog on 2009-11-25
Some of my CD rips suffer from bad break-up in places. Just a few tracks, on just some CDs. 

I am using an LG DVD rewriter as the CD drive. The break-up seems to occur at the same tracks as the DVD player starts speeding up to full speed, then slowing down (possibly even stopping), speeding up again etc. instead of a more mormal fairly constant medium speed. It feels as though the ripper is trying to read too fast and then failing to keep up. The problem occurs fairly consistently on certain tracks, and when encoding to both mp3 and ogg, but I get the imression that ripping to flac doesn't have the problem. Generally, sound-juicer says it's ripping at around 10x, so most CDs take around 5 minutes. 

Has anyone seen this / found a solution? 

Is there a way to tell it to only rip at (say) 5x to see if that helps?

---

### Post by fancypiper on 2009-11-26
> but I get the imression that ripping to flac doesn't have the problem.If true, then it sounds as if it may be an encoding problem rather than a ripping problem.

Generally, the CD ripping programs are a GUI front end to the command line program cdparanoia, which IMHO is the best ripper I have ever used.

If you rip to *.wav, is it OK?

[Getting the Best Help on Linux Forums](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

---

### Post by The Cog on 2009-11-26
That seems OK. So I have a theory that maybe the encoding is straining the CPU until it can't quite cope with the input rate, and that there is a problem with throttling back the drive speed. It has always seemed to take rather a long time to rev up - maybe 2-3 seconds.

I have found that my laptop doesn't have the same problem so I'm re-ripping everything on there at the moment. But it would be nice of I could figure out how to make my desktop reliable.

---

### Post by ssam on 2009-11-26
sound-juicer has a hidden option to increase its 'paranoia' when ripping. this will slow it down a bit, but give better results on scratched CD.

in gconf-editor (if you can't find a menu entry run it from the command line or Alt+F2). then go to apps->sound-juicer and set the paranoira value to 255. then restart sound-juicer

---

### Post by The Cog on 2009-11-27
That has helped enormously, thanks very much.

I have come to the conclusion that some of my CDs are scratched, even if I can't see the scratches. Ripping with the extra paranoia level makes those troublesome tracks rip very slowly indeed (10 minutes to rip a 4-minute track!!!) but the ogg file sounds OK now. Most tracks rip a little slower than before, but I'm happy to live with that. 

Oh, and just one CD is so badly scratched that I'm surprised that it plays. I lent it to my teenage son. Doh! The rip from that also now sounds perfect. I'm filling my shiny new ogg player with my CD collection.

---

