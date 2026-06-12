---
title: "[SOLVED] &amp;quot;cracking&amp;quot; sound during playback [oss]"
date: 2008-07-22
forum: Multimedia Software
---

### Post by ministoat on 2008-07-22
I've been using oss pretty successfully, though I noticed one problem at first in amarok, and it's recently started happening with other applications; mplayer, smplayer, foobar (in wine)..an annoying "crack" sound that appears through the right channel.

I've set up oss so that there's only the soundcard that I'm using (maudio delta 66) that appears in ossxmix window..and the ossxmix window shows the crack as a spike in the mixer. I know that it's not the speakers as when i'm playing cd's or when i'm using windows, the problem isn't occuring.

for the record, i also use Kaffeine for my dvt card, and that hasn't had this problem yet.

any possible solutions to this?

---

### Post by ministoat on 2008-07-22
whether this is related or not, i just tried restarting oss via soundoff, and was given this error:

/etc/oss.conf: No such file or directory

---

### Post by mailmaldi on 2008-07-24
i do not know if my reply is relevant to ur issue or if its of any help, i just stumbled on this thread and adding my 2 cent worth.

i fixed my hissing (steady though, thru both channels) by checking the inputmix-mute option for my green jack.

---

### Post by ministoat on 2008-07-25
thanks for the reply..this may be solved actually but i'm holding off marking it to make sure. 

I enabled esd mixing, and so far so good. I'll give it a good play over the weekend and see if there's anymore cracks :)

---

