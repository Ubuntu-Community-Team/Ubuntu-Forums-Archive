---
title: "Burn WAV file to an audio cd? (k3b, brasero, mplayer...)"
date: 2008-12-15
forum: Multimedia Software
---

### Post by sgissinger on 2008-12-15
Hi all,
So basically, I have tons of wav files that I want to be able to listen to via a simple cd and a simple cd player. I've already tried burning them as they are, assuming brasero would automatically convert them (as I was starting an audio cd project) but apparently it didn't. I'm sure this is a very usual problem, but I dont use k3b nor brasero that much (in fact it's only the second time I use brasero and I only use k3b to rip audio cd with lame) so...
Thanks in advance

---

### Post by logos34 on 2008-12-15
what if any error messages are you getting?

---

### Post by mc4man on 2008-12-15
If you are using 8.10 then you may run into a situation of a .wav is not always a .wav.
I'm not sure if brasero acts like rhythmbox but I wouldn't doubt it. 

In the case of rhythmbox, .wav's ripped by most rippers or dragged off of a cd will not play. Brasero may or may not act the same.
(ie. fail on the burn

This is what I and a couple of other people have noticed, if you have 8.10 you can test quickly by dragging a track off of a cd and seeing if it's played in rhythmbox or recognized properly in brasero. ( or seeing if your previously ripped tracks are.

---

### Post by sgissinger on 2008-12-16
Actually I don't get any error message and, Brasero simply burns the wav file and nothing more so, as expected, I cannot read it with a basic cd player... I am tying to get my wav file converted to whatever format regular audio cds use (to be played with a basic cd player) before it is burnt... I used to do this with Nero in Windows.
My wav file seems to be Microsoft 16bits PCM (I got it from an Audacity project).

---

### Post by logos34 on 2008-12-16
> **sgissinger said:**
> 
My wav file seems to be Microsoft 16bits PCM (I got it from an Audacity project).

good, 16-bit.  But is it 44100 Hz sample rate?  48000 won't work

sudo apt-get shntool

shntool info file.wav

---

### Post by sgissinger on 2008-12-16
Thanks for advising me to get shntool, as predicted, my wav file is microsoft PCM 16-bit and it is 44100Hz and not 48000.

---

### Post by logos34 on 2008-12-16
what about using Serpentine, the default Gnome cd burner?

after that the next thing to try would be the command-line just to see if this isn't a more serious system/drive problem

---

### Post by sgissinger on 2008-12-16
No dude, you don't seem to understand my problem. Sorry to repeat myself but I am just trying to burn a CD that I will be able to listen on a simple cd player from a wav file. My problem is "Into what must I convert the wav file for it to be listenable on a basic CD player???" It's quite simple really.

---

### Post by logos34 on 2008-12-16
serpentine is an *audio* cd creator app.

tracks need to be converted into the .cdda format

---

### Post by sgissinger on 2008-12-16
Ok thanks, thats what I was looking for. Can I use serpentine to convert my wav into cdda?

---

### Post by logos34 on 2008-12-16
it will only do so in the process of burning it to a CD.

I've never had any reason to convert to wavs to compact disc digital audio format other than to burn an actual cd (and most gui cdaudio burner apps use the cdrecord backend).  But you could maybe try **sox** to make a .raw file on the hard drive, as explained here:

[http://www.topology.org/linux/audio.html#wav2raw](http://www.topology.org/linux/audio.html#wav2raw)

---

### Post by sgissinger on 2008-12-17
Ok thank you for your time.

---

