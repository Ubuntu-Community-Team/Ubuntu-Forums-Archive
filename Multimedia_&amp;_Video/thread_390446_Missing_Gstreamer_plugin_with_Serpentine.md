---
title: "Missing Gstreamer plugin with Serpentine"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by yamswirl on 2007-03-22
I give.  I've been trying to figure this out for two days. (solved 2 other problems though :-D)

I'm trying to burn a cd using Serpentine 0.6.91, Ubuntu 6.06.  I ripped the tracks as mp3s and I get this message:

"If you're having problems opening certain files make sure you have the GStreamer plugins needed to decode them."

I've gone into the synaptic package manager to try to apply the right gstreamer plugins but don't really know what I'm looking for.  I applied both 0.8 and 0.10, which maybe is the problem.  I'm still getting the same message.

I'm new to Ubuntu so simplified instructions would be great.  If there's another program that I can use to burn a mix cd, I'm open.  I haven't tried yet but if .ogg files will play on a cd player that would also solve my problem. 

The goal is very simple.  I want to be able to make fun mix cds.  Please help.

I'll try to supply any other information that could be helpful.

Thanks!
Yamswirl

---

### Post by matemargo on 2007-04-17
You could try k3b with this plugin libk3b2-mp3.
Or you could rip again into OGG format.
Or you could use mp32ogg utiliy to convert the MP3 into OGG.

---

### Post by the badger on 2007-04-21
i too am stumbling around trying to figure out how to burn a cd (?!). for some reason just "copy disc" stalls and abandons the process after some time. i've been trying to copy a disc of mp3  files in serpentine and keep getting the "unsupported file types" message telling me to find gstreamer plugins, and then it might consider working for me. i can find gstreamer.net, but i'll be damned if i understand what's going on there. 
help?

i'm running only ubuntu (6.06) on my 'puter. no, i don't know unix commands. i can sign in and out and that's about it. not that i'm not trying to learn, but the beginning is steep my friends.

anyone who has the time to explain in slow-speak what matemargo posted above, or any other suggestion as to how to find and install this missing plugin(s), i would really appreciate it.

explanations are great.
thanks.

---

### Post by supaphly42 on 2007-04-24
I was having the same problem. What I ended up doing was going into Synaptic, doing a search for gstreamer and mp3, and then downloading anything that looked useful, lol. Anyway, it worked, and it can now burn using mp3 files. (you may need multiverse and universe enabled in synaptic)

---

### Post by ElaneFreuyh on 2007-09-18
the gstreamer site is most unhelpful, it does not specify exactly which formats are covered by which plugins.

I have a sneaking suspicion that WAV would fall under UGLY (good quality + bad  licensing), but installing that plugin  does not help with the 'unsupported file type' error.

---

