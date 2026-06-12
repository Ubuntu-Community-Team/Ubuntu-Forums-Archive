---
title: "LAME is broken (or Im using it wrong)"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by Milambar on 2007-07-05
I recorded a soundclip on my digital dictaphone, uploaded it to my PC..

The VOICE0001.wav played perfectly..

But when I ran lame on it..

lame VOICE0001.wav -o clip.mp3

All it outputted was white noise. So I tried the -x switch to swap the byte order..

lame VOICE0001.wav -o clip.mp3

Still white noise..

So, I assume several things here...

1) Lame is actually broken.
2) Lame can't convert wav files to mp3's
3) Im using it wrong.

It is probably #3, but, I am following the examples found on the web.

I would appreciate any help with this. Please don't suggest alternative formats. I know about ogg-vorbis, etc. But the final recipient wants an mp3, not a .ogg, or anything else.

---

### Post by MetalMusicAddict on 2007-07-05
Sorry I cant help more ATM but I gotta run. I'll try later. Take a look at the Grip thread in my sig. Has lots of references in it.

---

### Post by xfile087 on 2007-07-05
> **Milambar said:**
> I recorded a soundclip on my digital dictaphone, uploaded it to my PC..

The VOICE0001.wav played perfectly..

But when I ran lame on it..

lame VOICE0001.wav -o clip.mp3

All it outputted was white noise. So I tried the -x switch to swap the byte order..

lame VOICE0001.wav -o clip.mp3

Still white noise..

So, I assume several things here...

1) Lame is actually broken.
2) Lame can't convert wav files to mp3's
3) Im using it wrong.

It is probably #3, but, I am following the examples found on the web.

I would appreciate any help with this. Please don't suggest alternative formats. I know about ogg-vorbis, etc. But the final recipient wants an mp3, not a .ogg, or anything else.

I just tried it on my system and you're not doing it wrong - it works perfect on a few different tracks of mine... Seems odd that it doesn't work for you

Oh and when you say the wav plays perfectly, do you mean on your digital dictaphone or your computer?

---

### Post by JMO707 on 2007-09-29
Have you found a solution?

I'm experiencing the same thing, even when the last time (in the same machine) I used it worked flawlessly.

---

### Post by Frinky on 2007-10-25
I have exactly the same problem. Anyone know of a solution?

---

### Post by garf83 on 2007-12-06
I was having this exact same problem with encoding an MP3 using lame, except on Windows.  The way I solved it was to open the WAV file in Goldwave (an audio editor) and then save the file as a new WAV file.  This new WAV then worked fine being converted to MP3 with lame.  I've got no idea why this worked but it did.  I'm not sure what an equivalent audio editor would be in Linux but I'm sure there must be something available.  

As a point of interest my original WAV file was 5mb, the new WAV file saved by Goldwave was 48mb, and the MP3 created by Lame (on --alt-preset extreme) was 10mb.  So you might actually end up with a larger MP3 file than the WAV file you started with using this method.  I just did it cause the MP3 is compatible with my music player.  

Hope that helps someone!

---

### Post by ron999 on 2007-12-06
Hi
I had an experience like garf83 (but using Linux).
Some of my WAV files would not convert to mp3 using lame - just got white noise.
In my case, I imported into Audacity then exported as wav.
I figured that my wav files had not been encoded correctly but Audacity encoded them as 'genuine' WAV (Microsoft) files.
:guitar:

---

### Post by ledlincoln on 2008-01-08
Yep, I'm having the same experience with noise created by lame, regardless of the switches I've tried.  Importing into Audacity and exporting as .wav worked for me as well, but it defeats the whole purpose--I want to convert batches of ripped CD .flac files without importing them individually.  For that matter, I could import into Audacity and export as .mp3 without bothering with the .wav step and then invoking lame from the command line.  Not what I want to do.

Is there something wrong with the way I'm ripping the CDs (using Sound Juicer)?

Appreciate any help you can offer.

> **ron999 said:**
> Hi
I had an experience like garf83 (but using Linux).
Some of my WAV files would not convert to mp3 using lame - just got white noise.
In my case, I imported into Audacity then exported as wav.
I figured that my wav files had not been encoded correctly but Audacity encoded them as 'genuine' WAV (Microsoft) files.
:guitar:

---

