---
title: "Renaming pulseaudio sinks"
date: 2009-01-04
forum: Multimedia Software
---

### Post by timandjulz on 2009-01-04
Hi all,

I have 5 computers on my network all using pulseaudio.  This leads to a long confusing list of sinks/sources. Especially for my wife and kids who have no idea if they should select "ALSA PCM on front:0 (ALC883 Analog) via DMA" or "ALSA PCM on front:0 (USB Audio) via DMA" or any of the other 15 sinks displayed.

What I want to do is alias the names to more friendly names like "JVC Receiver in Den" or "Dad's Office" or "Mom's Desk Speakers".  They could even show up twice as the device and the alias.

Is there a way to do this?

Thanks,
Tim

---

### Post by timandjulz on 2009-01-06
bump

---

### Post by markbuntu on 2009-01-06
There is some discussion of this issue on the pulseaudio mailing list a while ago but no results yet.

I think the only way you can do that is to edit the etc/pulse/default.pa  and diable hal-detect and module-detect and explicitly load each sink and use the sink_name property to rename them but I am not sure how that will work. 

It would certainly be handy to be able to do that. There is a Ubuntu team working on a new gui for pulseaudio. I do not know where they hang out but you should defintely be talking to them.

---

### Post by timandjulz on 2009-01-07
That is good information.  Thanks Markbuntu

---

