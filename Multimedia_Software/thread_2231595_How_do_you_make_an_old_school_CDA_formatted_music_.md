---
title: "How do you make an old school CDA formatted music CD?"
date: 2014-06-26
forum: Multimedia Software
---

### Post by cwmoser on 2014-06-26
The CD Player in my car will my play MP3 or WAV formatted audio CDs.
How do you covert those type audio CDs to CDA format?
Is there a utility I can install on my Ubuntu 14.04 that will do this?

Carl

---

### Post by Vladlenin5000 on 2014-06-26
Any CD/DVD burning utility (+codecs) can burn a music CD from music files.

---

### Post by cwmoser on 2014-06-26
Still not sure I understand how to make an audio CD that will play on older CD players.

I assume the technology is called "cda" ??

---

### Post by Vladlenin5000 on 2014-06-26
You're focusing in names/naming conventions when you should be focusing on learning how to burn an Audio CD (different from a CD-ROM with MP3 files inside - it's a still a CD-ROM, not an Audio CD) with your favorite app. Usually you only have to select an Audio CD project, add the files in the intended order and click burn.

What software do you use to burn CDs/DVDs?

---

### Post by LastDino on 2014-06-26
Try K3b or xfburn.

They seem to have specialized option for burning Audio CD/DVD.

Given you've installed all the codecs/restricted extras and all, I don't see the problem.

---

### Post by newb85 on 2014-06-26
Last time I was in a recording studio, the engineer told me that's referred to as "Redbook format".  That might just be recording industry jargon, though.

I'll use Brasero as an example, since it's easy to use, in the repos, and installed by default on Ubuntu.  Open Brasero Disc Burner.  Click the Audio Project button in the top-left corner.  You can then add .mp3, .wma, .wav, etc. files (assuming codecs are installed) to your heart's content (or until the project size reaches the disc limit).  At the bottom, you can name the CD, and you may need to select the drive to burn to (or an .iso image that can be burned later).  It also appears to have a few other features for splitting tracks and adding pauses, but I haven't experimented with those, yet.

---

### Post by oldos2er on 2014-06-26
Moved to Multimedia & Video.

---

### Post by Yellow Pasque on 2014-06-26
I've never heard "CDA" used (though I've heard of DVD-A). I've always heard it referred to as an "audio" or "regular" CD.

CD's with music files on them are referred to as data CD's, CD-ROM, iso9660, etc.

---

### Post by cwmoser on 2014-06-26
> **newb85 said:**
> Last time I was in a recording studio, the engineer told me that's referred to as "Redbook format".  That might just be recording industry jargon, though.

I'll use Brasero as an example, since it's easy to use, in the repos, and installed by default on Ubuntu.  Open Brasero Disc Burner.  Click the Audio Project button in the top-left corner.  You can then add .mp3, .wma, .wav, etc. files (assuming codecs are installed) to your heart's content (or until the project size reaches the disc limit).  At the bottom, you can name the CD, and you may need to select the drive to burn to (or an .iso image that can be burned later).  It also appears to have a few other features for splitting tracks and adding pauses, but I haven't experimented with those, yet.


I used Brasero to create an Audio project.
I added some *.wav files to the project.
It created a brasero.bin and a brasero.iso file.
When I open brasero.iso with auto mounter, it shows one file named brasero.bin

Carl

---

### Post by Vladlenin5000 on 2014-06-26
[http://en.wikipedia.org/wiki/Red_Book_%28audio_CD_standard%29](http://en.wikipedia.org/wiki/Red_Book_%28audio_CD_standard%29)
And the (in)famous *.cda are just [http://en.wikipedia.org/wiki/Compact_Disc_Audio_track](http://en.wikipedia.org/wiki/Compact_Disc_Audio_track)

---

### Post by 3rdalbum on 2014-06-27
An "audio CD" has CDA-formatted audio on it. If your car CD player plays MP3-CDs, that's not an "audio CD", that's just a data CD which contains MP3s.

Just burn a CD containing MP3s - an ordinary data CD-ROM for a computer - and it will play in the car.

---

### Post by cwmoser on 2014-06-27
I think I'm making more into CDA file format than it is.
I also tried to copy an old CDA CDROM using Brasero but the copy did not work.
I opened both with Ubuntu and both just had a directory of *.wav files.
Looked at the directory in terminal mode using **ls -al** to see if there were any hidden files.
There were none.
Still the copy would not play on the CD player in my car.

---

### Post by SuperFreak on 2014-06-27
[http://soundconverter.org/](http://soundconverter.org/)

---

### Post by mc4man on 2014-06-27
> **cwmoser said:**
> I think I'm making more into CDA file format than it is.

Audio cd's are CD-DA
The cda you referred to may be a windows only deal which is .cda
These are small virtual files that you'd see on windows when browsing an audio cd, they just point to the location of a track on the audio cd.
So cda (.cda) is of no consequence for what you are doing.

Can a real (orig) audio cd play in your car?

---

### Post by MartyBuntu on 2014-06-27
> **cwmoser said:**
> 
Still the copy would not play on the CD player in my car.

Audio CD players can be "picky" about media. Especially car audio.

Try a different brand.

---

### Post by Vladlenin5000 on 2014-06-27
> **cwmoser said:**
> I opened both with Ubuntu and both just had a directory of *.wav files.

Therefore neither the original nor the copy - obviously - are CD-DA. They are - again - plain CD-ROM with audio files (wav) inside.
CD players usually support CD-DA only. A few are also able to read MP3 files from within a CD-ROM but take it as bonus feature. It isn't, never was and never will be a standard feature.

Now, honestly, I don't understand your confusion with such simple process and the results - a .bin file ???? - especially with such SIMPLE tool like Brasero where after adding the files you want (in the order you want) you just have to make sure your drive is correctly selected - not Image File nor something like that but the ACTUAL name of your PHYSICAL drive - then burn. The resulting CD is a CD-DA playable in ANY* CD player.

* Some players are indeed picky about CD-R as already commented here. However, as I just explained, that has nothing to do with not being able to work with a CD-ROM filled with wav files.

---

### Post by mc4man on 2014-06-27
> **cwmoser said:**
> 
I opened both with Ubuntu and both just had a directory of *.wav files.

> **Vladlenin5000 said:**
> 
Therefore neither the original nor the copy - obviously - are CD-DA. They are - again - plain CD-ROM with audio files (wav) inside.

An audio cd, (CD-DA),  either orig. or a proper copy, when opened in linux will show just a bunch of  "*.wav files". So what is the ^ of yours  supposed to mean?

---

### Post by Vladlenin5000 on 2014-06-27
> **mc4man said:**
> An audio cd, (CD-DA),  either orig. or a proper copy, when opened in linux will show just a bunch of  "*.wav files". So what is the ^ of yours  supposed to mean?

Indeed, just like this: [IMG]http://i61.tinypic.com/2r43lmg.png[/IMG]

But NOT inside any directory... I guess I never bothered to actually check how it looks like in Linux (and I'm using it for over a decade!) :lolflag:
Now, if it looks like this _and_ Ubuntu correctly recognizes it as "Audio CD", _then_ it should be playable in most CD players. Again, some players are really picky. The only solution is to find and test different brands of CDs.

---

