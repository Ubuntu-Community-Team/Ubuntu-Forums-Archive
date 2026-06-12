---
title: "normalizing MP3 volume levels"
date: 2011-04-24
forum: Multimedia Software
---

### Post by Quartlow on 2011-04-24
I may be in the wrong forum, if so please correct me. 

I have a rather extensive mp3 collection. 

The problem is some of the songs are louder than others, in other words set the volume and next thing a song comes along that scrambles your brains it's so loud, Or you get one you can't hardly hear. 

I've used a couple of GUI's in the past, but all of them seem to do one song at a time. Not really an option with over 10,000 songs. 

What would be nice is if I could pick one song as a base line and using terminal run a batch of say 500 songs through it. 

Running 10.10 2 gig of memory
Use Rhythm box to handle music currently.

Been using since Dapper Drake, I'm not afraid of the command line, but I am far from an expert user, in other words I know just enough to be a danger to myself and others :D 

I've never written a script file to automate anything but this may well be a time to learn one.

Any and all ideas welcome. The ultimate solution would be something I could run at night while I'm sleeping.

---

### Post by KegHead on 2011-04-24
Hi!

Same problem.

I used the following to standardize:

system... preferences...sound.

KegHead

---

### Post by Quartlow on 2011-04-24
That works ok on the system, You can also use the rythembox plugin to normalize them during playback

Doesn't do any good once the MP3 is transferred to the ipod.

---

### Post by Chronon on 2011-04-24
I use Linux versions of software as much as possible, but the easiest method for me is still to use Foobar2k (running under Wine).  It is fast and can automatically group files into albums and write album gain as well as track gain to metadata tags.

---

### Post by FakeOutdoorsman on 2011-04-24
Perhaps you should investigate **mp3gain**. It has a GUI, easymp3gain-gtk, if that is your preference, and it works with AAC and Vorbis as well I think. Both packages are in the universe repository, but I've never tried them myself.

Using this method has the advantage of not re-encoding the audio, so there would be no quality loss.

---

### Post by Quartlow on 2011-04-24
Thanks guys, MP3 gain seems to be ok I seemed to have missed it before in the software center

At least it does more than one file at a time.

---

