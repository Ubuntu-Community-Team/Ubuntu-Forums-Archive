---
title: "Graphics support"
date: 2012-06-11
forum: Mythbuntu
---

### Post by stefanst on 2012-06-11
Hi,

After many years of service our backend/frontend finally went to the big junkyard in the sky. Rather than trying to replace components on a system that is at it's core over 6 years old, I'll build a new box.

Specs MUST:
- Hardware support for h264 playback
- Expansion slot for IEEE1394 card (for channel changing)
- Quiet

Specs nice to have:
- Built in remote receiver 
- Small

In the past I've been using exclusively NVIDIA graphics for VDPAU playback on all mythtv systems. But it seems, that these days most boxes you can get use built-in Intel graphics. 

On the mythtv Wiki it looks like most modern Intel graphics, like the ones built into the "i" series processors support hw decoding of h264 in Linux, but I can't find definitive info.

Any recommendations?

Thx.

ST

---

### Post by nickrout on 2012-06-11
IMHO you run a risk that anything else will be inferior to vdpau.

Intel built in graphics (Sandybridge) is reported to work via vaapi on myth 0.25, but is not as good as vdpau.

---

### Post by stefanst on 2012-06-12
OK- I'll stay with NVIDIA for now. Any Ion board should do nicely.
For the backend/frontend I would then go with something like this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131663]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131663")

It's a 1.8GHz dual core Atom with built in Ion. All passive cooling, so it won't make much noise :-)
Will it be fast enough to handle mild back-end tasks? I'm not transcoding or commercial-flagging, so I don't see why it would need much ooomph....

---

### Post by nickrout on 2012-06-12
> **stefanst said:**
> OK- I'll stay with NVIDIA for now. Any Ion board should do nicely.
For the backend/frontend I would then go with something like this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131663]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131663")

It's a 1.8GHz dual core Atom with built in Ion. All passive cooling, so it won't make much noise :-)
Will it be fast enough to handle mild back-end tasks? I'm not transcoding or commercial-flagging, so I don't see why it would need much ooomph....

On that basis it should work fine.

---

