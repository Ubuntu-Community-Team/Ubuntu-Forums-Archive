---
title: "How to Save MP3 Files"
date: 2010-05-17
forum: Multimedia Software
---

### Post by gwm on 2010-05-17
How does one save files in MP3 (or MP4) format.

This would apply to converting an existing audio file to MP3 or to ripping a CD.

This question must be as old as Ubuntu, yet I find very little in our forums. What I do find, refers me to items that don't seem to be in the repositories anymore, so perhaps someone in the know can update us again.

Yes it is lossy and proprietary, but it's fine for speech and produces a much more compact file than flac. Also, flac and ogg are not well known to non Linux users, programs and equipment. So, for compatibility, I often want to convert flac to MP3.

I have Ubuntu 64 bit, 10.4 installed.

---

### Post by Rhubarb on 2010-05-17
Too easy :)

You need to grab a program that goes by the name of soundconverter, you can install it thus:

```
sudo aptitude install soundconverter
```

You'll find it in Applications --> Sound & Video --> Sound Converter
Then, from the Edit --> Preferences menu you can change the default conversion format to mp3.
Load up your audio files into it and it'll convert them all into mp3s :)

---

### Post by aeon.flux on 2010-05-17
if you want to extract Audio CD to MP3 or any similar format, you can use "Rhythmbox", "Banshee" or many other players, but I prefer "Audio CD Extractor" (you can find it in Ubuntu Software Center)
if you want to convert music, i'd recommend you to use the "Sound Converter". After installing the MP3 plugin you can convert any kind of audio and video files into any quality of MP3 :mrgreen:

---

### Post by gwm on 2010-05-22
Thanks for the responses.
They motivated me to do what I should have done in the first place, I googled using the title of this thread and found this link. It wasn't immediately there on Audacity's main page, so I didn't see it.

[http://wiki.audacityteam.org/index.php?title=Lame_Installation#GNU.2FLinux.2FUnix_instructions](http://wiki.audacityteam.org/index.php?title=Lame_Installation#GNU.2FLinux.2FUnix_instructions)

I turns out that all I needed was to install **lame** and **libmp3lame0**. Since the multiverse repository was already enabled, marking **lame** for installation automatically marked **libmp3lame0** for me. I applied the changes and Audacity was mp3 enabled. Voila!

The page indicated by the above link has some more really interesting information about **lame** and I thoroughly recommend it. Now I know that **lame** comes with an executable binary that does it all from the command line. It suggests to me that the various converters are actually GUI front ends that collect options from the user and then spawn an execution of **lame** with the appropriate parameters.

---

### Post by Rhubarb on 2010-05-24
Argh, good point!

I forgot to mention that - as I usually install lame, flac, and vorbis-tools from a fresh install anyway.

lame is (perhaps one of) the best mp3 encoders available now.

Anyway, glad to know that you're back in business with mp3 :)
- And if you can, give vorbis and flac a try out.

I've got an mp3 player that supports ogg vorbis (and flac for that matter).
So I have my cd's ripped into flac, and merely convert to ogg vorbis to be dumped onto my mp3 player.

---

