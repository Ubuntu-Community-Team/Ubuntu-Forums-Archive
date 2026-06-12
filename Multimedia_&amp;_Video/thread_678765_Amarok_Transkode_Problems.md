---
title: "Amarok Transkode Problems"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by mnmlst on 2008-01-26
Firstly, I have no idea what version of Ubuntu I'm running, because my ex installed it.  I think it's Feisty Fawn.

I'm trying to convert ogg files so I can load them onto my ipod.

I've installed the transkode script on Amarok, and when I try to run the script I get the following error message: /home/username/.kde/share/apps/amarok/scripts/transkode/transkode: error while loading shared libraries: libutempter.so.0: cannot open shared object file: No such file or directory

Someone in another thread suggested moving transkode from usr/bin to the above file path, but I couldn't find it in usr/bin.

Another person recommended rockbox, but my ipod is a second generation nano, which doesn't run rockbox.  

Does anyone else have a solution?  Any ideas?  I have a lot of ogg files, so it would be a huge help.

Thanks in advance.

---

### Post by luisromangz on 2008-01-26
You should try using SoundKonverter. I think it is in the official Ubuntu repositories, but there is a newer version in GetDeb.

---

### Post by mnmlst on 2008-01-27
Thanks.  I'll check it out.

---

### Post by Multiplexer on 2008-01-29
I have the same problems as you. Even Recompiled Transkode. Seemed to work as standalone app, then, but not still not as amarok transcoding tool. At least there were no quetionable dependacies any more, but something seems to be broken nonetheless...

I tried the AmaKode script which does just what I need: Automatically transcode my ogg files to mp3 when moving them to the player with amarok.

Make shure you have also lame installed.

---

### Post by banda on 2008-02-09
you can get libutempter from [here]("http://stuff.mit.edu/afs/sipb/project/linerva/project/packages/libutempter/libutempter1_1.1.3-1_i386.deb")

after this install libnfsidmap and  libldap2.3 from synaptic.. say a prayer and transkode would probabally start working(did for me:))

---

