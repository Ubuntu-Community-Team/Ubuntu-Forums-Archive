---
title: "mp3 converter?"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by nate22 on 2007-06-27
hey guys im wondering if there is a good converter of all the uncomatible mudic formats to compatible one 
OR have a player that can play them all


w/ my move to ubuntu i saved all my belowed music but most of them are unplayable w/ most of the stuff i have the only one that plays them right is xmms player...but the interface on that is very arcaic

im looking for somthing on the highend of the interface-scale

---

### Post by click4851 on 2007-06-27
I have had good luck with the VLC media player for playing formats that gave me trouble....

---

### Post by tater_3001 on 2007-06-27
i have amarok and it plays all my mp3s  ihad to install the w32codecs though .. did gstreamer work for the sound problem? also i believe there is a program called lame that converts music... not 100% sure though..

---

### Post by nate22 on 2007-06-27
no it didnt fix sound probs

---

### Post by Sonofmoog on 2007-06-27
> **nate22 said:**
> im looking for somthing on the highend of the interface-scale

You don't need to convert.  What you need is the libxine library, then any music program in GNOME should be able to use this library to play your music.  

If you do want to convert, I suggest you use Audacity to convert from mp3 to ogg.  A fringe benefit is your music will sound better in ogg format ..

---

### Post by regomodo on 2007-06-27
soundKonverter is good

as far as i can tell it can convert almost anything to anything

---

### Post by bikeboy on 2007-06-27
True, ogg sounds good, but converting from mp3 to ogg will sound worse than the original mp3. It's a compressed file being compressed again.

nate22, which file formats in particular can't you play? As people have said, mp3's should be fine once a suitable codec is installed through Synaptic. Same goes for wmv, most avi files and just about anything you can throw at it.

---

### Post by nate22 on 2007-06-27
mostly mp3 and wmv

what should i type in on SPM to get the codecs?

---

### Post by bikeboy on 2007-06-29
The first thing I would try is all the gstreamer10 packages like plugins-ugly and ugly-multiverse.

---

### Post by nate22 on 2007-07-01
are you able to get those via SPM?

---

### Post by bikeboy on 2007-07-02
Yes. Just search in SPM for gstreamer.

---

