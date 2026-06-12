---
title: "Intel Graphics Output Question"
date: 2009-12-22
forum: Mythbuntu
---

### Post by sabre2th on 2009-12-22
I've been thinking about a new fileserver/backend/frontend for a while now and the plan has been to use a dual core Atom processor (I guess I'm feeling green lately).  I've already built a barebones system in my head that should work great, using Nvidia graphics and my existing PVR-500 card.

Then I stumbled onto this guy:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359)

My question is: can the Intel graphics handle component output through the 7-pin s-video connector?  I have a couple of these adapters that I've used successfully with Nvidia cards, but I'm not sure if it'll work with Intel.

It would save me a chunk of money and give me more flexibility with the build if it's possible.  I appreciate any info you guys have

---

### Post by blue_z on 2010-01-07
Hi there

>My question is: can the Intel graphics handle component output through the 7-pin s-video connector?

I haven't actually tested for component video, but the s-video certainly does work on the D945GCLF2.  The Intel documents make no mention of component video for this 7-pin DIN connector, so I wouldn't expect it.  Manufacturers rarely _not_ mention features or capabilities of a product. 

Reportedly there is composite video on the other pins.

*edit:*
I connected a nVidia DIN-to-3xRCA adapter, but I don't have a display that accepts component video.  The green RCA connector displays a luminance 480i signal, i.e. half of the s-video.  If there is a component video output, then it is only at 480i.

Regards

---

### Post by sabre2th on 2010-01-08
I'm tempted to reply to your first message, but I'll leave that alone.

Thank you for trying.  The only reason I asked is because none of the Nvidia cards I've done it with specifically mentioned support for component output.  I thought there might be a chance it would work.  Given the mess of 7-pin outputs, I'm not surprised that it's not supported, but I wanted to be sure.

---

