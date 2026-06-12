---
title: "Cue+WAV in Ubuntu"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by pika2000 on 2007-06-14
I just installed Ubuntu + Beryl yesterday, and so far my experience is better than past linux distros. However, there is 1 thing that I have no idea how to do in Ubuntu.

I backup my AudioCDs using EAC in windows as CUE + WAV file, meaning the whole CD is ripped to 1 big WAV file, and a .cue file is created containing the track info. In windows, this is great since there's Daemon Tools that can mount the CUE+WAV combo as an AudioCD so I can rip it using any CD-ripper program. Even foobar2000 supports the .cue directly, and will list all the tracks properly.

My goal is to be able to use/mount my CUE+WAV image files in ubuntu, so I can rip and encode my music collection into Ubuntu.

In Ubuntu, I can't seem to find a way to work with this. mount doesn't work. I've researched cdemu, installed it, and it doesn't recognize the .cue as a valid image file (since it's not the regular cue/bin). I heard about Amarok, installed it, but apparently it only support cue sheet embedded in FLAC, not an external .cue. I even installed Wine and get foobar2000 working, but then I can only play the tracks since encoding in foobar2000 requires commandline encoder, and those doesn't work in Wine.

Anybody have any ideas? Is this something just not doable at all outside windows?

---

### Post by pika2000 on 2007-06-15
Hmm, no ideas?

Currently my workaround is to encode the big WAV file into Vorbis, edit the .cue file to match the .ogg extension, and use mp3splt commandline to splice up the big .ogg file into seperate tracks. A big hassle compared to doing a straight rip/encode, especially since this is the way all my AudioCDs are backed up.

---

### Post by pika2000 on 2007-06-16
Bump?

---

### Post by mekkah on 2007-06-20
The way i see it; Cue+Wav is a pretty useless way to backup Music. I used to do that too, until i realised that i never burn audio CD's. It's much easier & more universal, ripping into separate tracks & burn it gapless in GnomeBaker. GRIP + FLAC is my formula to copy my own music for backup purposes.

But to answer your question: It's possible to run EAC under Ubuntu using Wine

---

### Post by julian67 on 2007-08-12
I had the same problem and there isn't a Daemon Tools equivalent. There are tools like bchunk and shntools and cuetools but they don't handle .wavs well (id3 data gets discarded, filenames get discarded etc). 

One possibility is to install wine (sudo apt-get install wine) and then use Wine to install and run EAC (it works perfectly for me using the latest EAC and the standard Wine from Ubuntu repo). 

Using EAC go to tools>split wav by cue sheet. This splits the .wav and correctly writes the file names. You now have all the individual tracks as wavs which can be easily tagged and converted to mp3/ogg/flac etc using easytag and SoundConverter or similar or any of the command line encoders or a script like lossless2lossy.

[lossless2lossy]("http://lossless2lossy.sourceforge.net/") is a conversion script for mass converting your ENTIRE music collection from one format to another whilst mirroring the directory structure and tags of the original format. It differs from most other conversion scripts because it is able to convert multiple files from multiple directories recursively.

You can use it to convert from lossless (flac) to lossy (mp3) or recompress you lossless collection to another lossless format.

It still isn't as quick or convenient as ripping from a mounted image and having all the encoding, tagging and playlist writing done for you automatically but at least it's possible to accomplish the task without Windows. For myself I still have a PC with a OEM Windows on a partition and I guess I'm going to spend a day or 2 using Daemon Tools and EAC and a burning app to rip a lot of stuff to OGG and then convert the cue+wavs either to iso images with CD-Text  or to individual flac files.


edit: you can of course use EAC under Wine to compress the wavs you just split. Tools>Compress Wavs. It works fine and you will just need to tag them and maybe write a playlist. Easytag can do this almost automatically.

---

### Post by atti_simon on 2007-09-30
I had a .cue + .ape combination.
I found a way to transform the whole bunch into .ogg tracks.

First: 
With the .cue [view its content], you have to decompress the .ape to .wav.
There is a wonderful tool for this:
[http://www.legroom.net/software/apeinfo](http://www.legroom.net/software/apeinfo)
and
[http://sourceforge.net/projects/mac-port/](http://sourceforge.net/projects/mac-port/)

After compiling MAC and apeinfo, i simply used mac to decompress the ape into a wav:

```
[]$ mac CDImage.ape CDImage.wav -d
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Decompressing...
Progress: 100.0% (0.0 seconds remaining, 468.8 seconds total)           
Success...
```

Second:
After that I started a new audio project in K3B, simply opening the cue file.
There I had the "Convert to other audio formats option" and I converted the "big" wav file into .ogg tracks, using the .cue file.

I'm on Fedora 7, I used K3B 3.5.7-21 with extras.

Hope this helps!

Good luck!

---

### Post by julian67 on 2007-09-30
I think we can be grateful that monkey's audio/ape is dying a slow death and flac is becoming the default lossless codec for so many people on all platforms.

I actually worked my way through hundreds of cue and ape rips i'd accumulated over the years, all the time regretting how I'd preferred ape over flac for its slightly stronger default compression. It's horribly slow to decompress compared to flac. I now have all my archived lossless music in flac only.  

I think the solution you found looks pretty good for anyone who uses kde or is happy to install the required kde libraries to use k3b and it's nice to use a free burner/ripper, though EAC was OK for me as I don't have any kde stuff but I did already have wine and I did the whole lot within Ubuntu....I really couldn't face spending that much time using Windows :lolflag:

---

### Post by atti_simon on 2007-10-01
I also like flac better than ape, but sometimes you need tools to transform something you can't get in other format. (the other thing is, that it's nice to have a solution for almost anything :) )

As I saw, ape has little support on Linux, but still it's good to have something like MAC to decompress the ape and after that transform the resulting .wav into something you need.

I am a gnome user too, but as I use K3B for cd/dvd burning, it was the easiest way to transform one big ape to .ogg tracks.
I didn't have the time to experiment with other programs, but after you get your ape file decompressed, I think there are many programs, that could read and use the cue file to transform the "big" wave into tracks in lossy or lossless format.

That's why I like Linux: great community, lots of solutions, free to use anything :lolflag:

---

### Post by nekr0z on 2007-10-21
A stupid question maybe...

I have a flac+cue backup of a CD. Now I want to make a lot of OGG files out of it, to listen with my car audio. How do I do that?

---

### Post by julian67 on 2007-10-21
There's a helpful guide to splitting the cue+flac here [http://aidanjm.wordpress.com/]("http://aidanjm.wordpress.com/")

You will probably need to tag or at least rename the individual flac files, easytag is great for this. To encode the files to ogg is also extremely simple. 

```
oggenc -q 6 *.flac
``` will encode all flacs in the folder to ogg quality 6 and preserve the filenames and tags. You might even prefer quality 5 if it's just for listening in the car as unless you have a beautifully quiet car with high end audio there is enough environmental noise to make higher quality encodes pointless. 

If you prefer a gui you could use soundconverter or one of the scripts for Nautilus, or soundkonverter script for Konqueror/Krusader for KDE but I believe you will still have to use the terminal to split the cue+flac. Other gui option is to use EAC in Wine to convert the flac to wav, and then split it by cue. You would need to edit the cue file to show wav instead of flac. But it's a lot quicker and simpler to use the terminal in this case.

---

### Post by nekr0z on 2007-10-21
Thanx a lot!

---

### Post by julian67 on 2007-10-21
> **nekr0z said:**
> Thanx a lot!

You're welcome. All those cue+wav, cue+ape, cue+flac rips look so easy in the Windows world but are a real pita on the free desktop. If you're enjoying other people's rips there's not a lot you can do but all my CD rips these days are to flac/ogg  multiple tracks +m3u playlist.... makes life a lot easier. Fortunately there seem to be an awful lot of people these days who make  flac rips to multiple files with m3u.

---

### Post by gonzalo3k on 2007-12-26
Well, my english is bad, but I will try to make me understand.
I had the same problem, I had a WAV + one CUE file with the information for split the file, and finally found the way to do that, is easy:
Open the CUE file with K3B, go to Project > Convert Tracks.
This is all, now you can select the file target, if you select WAV, only the will be splitted the original WAV in individual tracks renamed as you want.
I hope this help you.
Take care!

---

