---
title: "Off loaging commercial flagging to a different backend"
date: 2009-11-10
forum: Mythbuntu
---

### Post by daniel.pool on 2009-11-10
Hey guys,

I wanted to ask some advice on a hardware / myth backend setup I'm planning:

Because of a redecoration of the living room I'm looking at replacing my existing HTPC hardware with a (much) smaller and (much) prettier nVidia ION platform. My current system runs a mythTV backend on the HTPC and uses XBMC as a frontend on the same platform. TV shows are sheduled for recording via MythWeb and then copied on an overnight job to my NAS using the mythnuv2mkv script (this is then made available in the XBMC library).

I'm pretty sure that the new atom processor won't be up to this transcoding job or the task of commercial detection. What I was thinking was to off load these jobs to my gaming rig on an overnight job (it has ubuntu 9.10 installed on it) before then transferring them to the NAS.

So as I understand it I should install the mythTV backend on the new ION htpc and a slave backend on the gaming rig. I then have both machines start up around 2am and begin the transcoding process?

I might be putting it too simply, but is that pretty much all I'd need to do to get things working? Does anyone have any better suggestions about what I could do ... ? I've searched for commercial detection scripts on linux, but by far the most hits were for myth.

Thanks in advance,
~Dan

---

