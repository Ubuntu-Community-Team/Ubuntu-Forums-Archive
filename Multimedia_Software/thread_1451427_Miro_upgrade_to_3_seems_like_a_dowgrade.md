---
title: "Miro upgrade to 3 seems like a dowgrade"
date: 2010-04-10
forum: Multimedia Software
---

### Post by miniyak on 2010-04-10
I recently upgrade to Miro 3 from Miro 2.5 under Karmic. I have notice that it boots faster. Unfortunately It has now started to choke on HD video (like the HD revision 3 shows). After a few minutes of watching video will slow down and audio will stay at the same speed.

Just a couple of observations, This happens when the cpu/s jump to 100%. It seems (through looking at the process manager) that python is using up a lot of horsepower. Python is what Miro is written in right? 

At this point im just kinda looking at "downgrading" back to 2.5 without losing any meta info. What would be the easiest way to do this?

Latter i'll try reinstalling 3, is anyone else having these issues?

---

### Post by iKonaK on 2010-04-11
I experience 100% cpu load even when I don't play anything, the process responsible is python2.6 which is used by Miro 3.

---

### Post by miniyak on 2010-04-11
yeah, for me its off and on at hitting 100%, Mainly python. Especial for the first 5 minutes or so after starting up.

 I don't think reinstalling helped from what i have observed so far.

---

### Post by miniyak on 2010-04-13
Its actually ok once left on for a while, i just find it hard to want to go with a "upgrade" if everything just got more bloated, form what i heard the only changes were subtitles.. and streamlining.

i just noticed something. Wasn't there an option to use xine or gstreamer in the last version? I believe xine is a little more light weight then gstreamer an it helped smooth playback out on my older desktop.

---

### Post by miniyak on 2010-04-14
seems like things are going a little better after a restart. maybe...

(sometimes i forget this can make difference, having my computer on or in stand-by all the time.)

---

### Post by splicerr on 2010-04-16
Ugh, they just upgraded miro to version 3.0 in the Lucid repositories. The thumbnailer in miro 3 seems severely broken.  Only a few of my videos have thumbnails now, the rest all have a black placeholder  :(

So yes, it seems like a downgrade to me.

---

### Post by miniyak on 2010-04-16
im going to say that things are going better after the restart. Miro has yet to choke on hd since then.

splicerr- my thumbnails seem to all be still there in karmic... the ones that came through before that is. Have you tried a reinstall/restart... might sound too simple to work but sometimes that does it.

Lucid is using the same version of python right? pretty sure karmic is running 2.6

---

