---
title: "Dolby Software Decoders"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by darkphoenix16 on 2006-11-21
Hi,

I was wondering if there is a software Dolby Pro Logic II decoder around? If not, how hard would it be to create?  I am a professional programmer but I do not have any experience with ALSA at all.  Here is the encoding matrix for Dolby Pro Logic II.

Dolby Pro Logic II 	Left 	Right 	Center 	Rear Left 	Rear Right
Left Total 	1.000 	0.000 	0.707 	j0.8165 	j0.5774
Right Total 	0.000 	1.000 	0.707 	k0.5774 	k0.8165

j = + 90º phase-shift , k = - 90º phase-shift

I am not sure how much audio card hardware could be used to help in this task, but it seems like a CPU intensive project.  Any comments?

---

### Post by caish5 on 2007-03-20
I know nothing about programming, but this is a worthy idea. AC3 filter performs this job for pro logic files in Windows but so far i can't find anything to do it in Ubuntu.

---

