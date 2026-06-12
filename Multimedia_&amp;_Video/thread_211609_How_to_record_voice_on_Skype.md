---
title: "How to record voice on Skype?"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by matjaz_pirnovar on 2006-07-08
Hi,

I'm trying to record voice with Sound Recorder on Skype. I can record my voice but not other person's on the other side.

Any tips? Special settings?

Which programme records both voices? Audacity?

Thanks.

M

---

### Post by ajgreeny on 2006-07-08
What version of skype have you got as all before 1.3 had problems with sharing the sound system as it didn't use alsa but oss instead.  If you gat the beta1.3 version it uses alsa and makes thing generally a lot easier.  Have you tried audacity for sound recording?  I'm not saying it will solve your problem but it is a great prog with all sorts of filters and editing options.  Worth trying!

---

### Post by matjaz_pirnovar on 2006-07-09
Hi,

Thanks for answering.

I'm using new 1.3 beta skype. It works perfectly. And ALSA of course.
I can't really make Sound Recorder to record other persons voice.

That's why I installed Audacity - but it gives me error message I posted in separate posting in this Vide&Sound section, see here:

"When installing Audacity from Add/Remove it installs okay, but when starting it I get the message:

"There was an error initializing the audio I/O layer.
You will not be able to play or record audio.

Error: Host error"


I'm sure some of you came across it.

I have ALSA enabled."


So, either I fix Audacity somehow to record or I don't know. 
Sound Recorderd doesn't have ability to record voice on the other side?

There must be someone playing with recording vioce conversation in this communuty. Where are you all freaks  ;)  ?

Thanks.
Matjaz

---

### Post by matjaz_pirnovar on 2006-07-10
Any clues on how to record skype conversation?

M

---

### Post by SethD on 2006-07-11
I am also interested in recording using Skype v1.3 and ALSA. I have thus far been unable to find an ALSA utility similar to esdmon which would sit as a recorder between the ALSA mic/speaker channels. I imagine this should be pretty simple, but is anything like this available yet?

Thanks, Seth

---

### Post by matjaz_pirnovar on 2006-07-11
Hey Seth :)

Just wondering...did you post on Skype forum about this too?
I think I replied you (about 'skype-rec' programme not putting files into right format)...


I hope we get some suggestions here.

:)  Matjaz

---

### Post by grizzly on 2006-07-14
Isn't it possible to record by selecting 'line'  option in the sound mixer?

---

### Post by matjaz_pirnovar on 2006-07-15
Hi,

No. By selectin Line-in option Sound Recorder automaticaly changes to Capture option.

It's the skype-rec programme that should enable you recordng See here: [http://sourceforge.net/projects/skype-rec/]("http://sourceforge.net/projects/skype-rec/")

Apparently works only under OSS so you should switch to OSS for the recording session.

---

### Post by matjaz_pirnovar on 2006-07-15
For me, this link hasn't worked yet.

It gives me error:
ERROR: Couldn't locate oggenc binary at 'oggenc'

I suppose I need to set my oggenc binarry location. Don't really know how to do that.

Any clues????

Thanks. M

---

### Post by matjaz_pirnovar on 2006-07-15
Nobody uses skype-rec???

---

### Post by matjaz_pirnovar on 2006-07-17
For ogg binaries to work I had to install ogg vorbis tools from synaptic manager.

Few additional settings and now skype recording works.  :)

M

---

