---
title: "Itunes M4A conversion to MP3 need program"
date: 2008-11-16
forum: Multimedia Software
---

### Post by jukingeo on 2008-11-16
Hello,

I am sure that this question may have been asked a few times before, but here goes anyway.

I do have an Ipod and I had been using Itunes for a while now.  The key word there is HAD.  I am using Linux now more than Windows, and I don't change the songs on my Ipod that much.  However, I found out that ripping songs off my CD's into Itunes was a VERY BAD idea.  Itunes rips everything to their M4A file format.

Needless to say that M4A file format has wrecked havoc on many audio programs that I have (now in Linux) in which I would love to play the songs I bought from Itunes.

The situation became worse when I recently obtained a Jukebox program that I absolutely LOVE, but the program will only read MP3 and OGG files.

So all in all, I managed to rip all my CD's that I wanted to MP3, but now comes the dilema in converting the Itunes bought songs, which are now stuck in the M4a format.

I have been reading that there are programs that can convert M4A files to MP3, but that going from a lossy format to another lossy format will make the M4A files sound worse upon conversion to MP3.   I DON'T want this.  I would like to keep the M4A files the way they are.  Someone suggested burning to a regular audio CD (as Itunes offers this option) and then from there go to MP3.  The premise that expanding the file to a loss-less format and then from there ripping the CD as you would a normal store bought CD to MP3 would not have as much of an effect on the audio.

Now I am not sure if this can be done or not, but I am right no open to any suggestion that will allow me to convert my M4A files to MP3 in a manner that will provide AS LITTLE SOUND QUALITY LOSS as possible.

Thank You,

Geo

---

### Post by cyfur01 on 2008-11-16
I personally use soundconverter with LAME mp3 support:
```

sudo apt-get install soundconverter libmp3lame0

```
This will then be installed under Applications->Sound & Video->Sound Converter. It's a very simple app, but it will convert m4a to mp3 provided you have LAME installed (I believe libmp3lame0 is the right library, but I'm not 100% sure. If it's not, ubuntu-restricted-extras should do the trick, provided you can/wish to install it).

About the whole lossless thing, without descending into the depth that this argument usually goes, if you are converting these for listening on an iPod, a little bit of lost quality won't hurt as the iPod earbuds aren't exactly stellar-quality headphones. I use some decent headphones for listening to most of my music at home, and I can't tell the difference between an m4a and mp3 I just converted as a test. However, rather than arguing, the easiest thing to do is to try converting several of your songs and then see if you're happy.

---

### Post by jukingeo on 2008-11-17
> **cyfur01 said:**
> I personally use soundconverter with LAME mp3 support:
```

sudo apt-get install soundconverter libmp3lame0

```
This will then be installed under Applications->Sound & Video->Sound Converter. It's a very simple app, but it will convert m4a to mp3 provided you have LAME installed (I believe libmp3lame0 is the right library, but I'm not 100% sure. If it's not, ubuntu-restricted-extras should do the trick, provided you can/wish to install it).

About the whole lossless thing, without descending into the depth that this argument usually goes, if you are converting these for listening on an iPod, a little bit of lost quality won't hurt as the iPod earbuds aren't exactly stellar-quality headphones. I use some decent headphones for listening to most of my music at home, and I can't tell the difference between an m4a and mp3 I just converted as a test. However, rather than arguing, the easiest thing to do is to try converting several of your songs and then see if you're happy.


I am actually converting for an mp3 playing jukebox program, so the fidelity will be better than that of your ear-buds for an Ipod...that is for sure.  However, the application is for casual music listening and not critical listening.  I will say that I am very generous with my MP3 sample rates and find out that pretty much anything over 192k, I cannot really tell the difference with.  After this setting, I usually then jump to a .wav file if I want better sound.

The jukebox program will only accept MP3 and OGG files, nothing else.  While I do like the way the M4a files sound, the trouble is that they are not compatible with many players out there.  Whereas Itunes (as well as most other programs) do recognize MP3's.  So this is the way I am going to go.

I guess I will try out the converter and see what happens.  If there is a slightly noticeable difference, it isn't going to be the end of the world.  But if it is dramatically noticeable, I may have to find the songs in question and re-rip them into my machine, or buy them from a site that supports MP3 downloads.

Thanx,

Geo

---

