---
title: "Audio CD mastering/authoring"
date: 2008-01-02
forum: Multimedia Production
---

### Post by chunderbunny on 2008-01-02
Hey all, 

Are there any apps tailored for audio CD authoring?

I'm looking for something where I can take a bunch of .wav files, concatenate them all together, insert track markers (and CD-text if possible) and then burn it to a CD. 

The trouble is, the .wav files I record rarely align with where I want the tracks to start/end, every CD burning app I've seen so far makes this assumption.

---

### Post by radi0j0hn on 2008-01-02
I'm trying to understand why you are doing all this work. I know in the Windows world, there are plenty of programs that let you just add WAV files to a list, hit a button and then the audio CD is burned.  Why do you need a specific starting point and surely their must be similar programs for Linux.    John

---

### Post by eye208 on 2008-01-03
> **chunderbunny said:**
> I'm looking for something where I can take a bunch of .wav files, concatenate them all together, insert track markers (and CD-text if possible) and then burn it to a CD.
Check out [gcdmaster](http://packages.ubuntu.com/gutsy/sound/gcdmaster).

---

### Post by chunderbunny on 2008-01-03
> **radi0j0hn said:**
> I'm trying to understand why you are doing all this work. I know in the Windows world, there are plenty of programs that let you just add WAV files to a list, hit a button and then the audio CD is burned.  Why do you need a specific starting point and surely their must be similar programs for Linux.    John

I do a lot of location recording (weddings, live gigs etc) which typically results in a few 30 minute .wav files. I need to split these up into a few tracks to separate out different songs, and often the end of the .wav file is not where I want the end of the track to be.

[QUOTE=eye208]Check out gcdmaster.[/QUOTE]

Cheers, that looks like exactly what I need.

---

### Post by radi0j0hn on 2008-01-03
I think I see what you want.  Why not load them into Audacity, then copy and paste the segment into a new file?  Then save it and when you have all the files you need, burn them?  You can also modify the levels, etc, if needed.  

John

---

### Post by eye208 on 2008-01-04
> **radi0j0hn said:**
> Why not load them into Audacity, then copy and paste the segment into a new file?  Then save it and when you have all the files you need, burn them?
Because it's tedious.

It is much easier to load the whole recording into gcdmaster, put the markers where you want them and then burn, without splitting the original file at all. Also this way you can be sure the CD will be written in DAO mode (gcdmaster is the "official" front end of cdrdao), avoiding gaps between the tracks. You don't want gaps in a live recording, no matter how small. You just need the track markers.

---

### Post by radi0j0hn on 2008-01-04
If you use an editor, you can fade out tracks, mix one into another and a lot of small things that polish the overall feel of the final mix. I'm not saying you are doing it wrong or the hard way, but I'll be curious to see if you find the software you need.

Are you able to transfer the audio to the PC digitally?  Doing it in analog was always the tedious part for me!

John

---

### Post by eye208 on 2008-01-05
> **radi0j0hn said:**
> If you use an editor, you can fade out tracks, mix one into another and a lot of small things that polish the overall feel of the final mix. I'm not saying you are doing it wrong or the hard way, but I'll be curious to see if you find the software you need.
Don't get me wrong here. I'm not against using Audacity for pre-mastering. I just don't see the point in splitting up the file as you suggested.

---

