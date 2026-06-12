---
title: "Coherence, fuppes, or x360mediaserve"
date: 2009-10-02
forum: Multimedia Software
---

### Post by Flarkis on 2009-10-02
I'm in the process right now of setting up a home server and one of my goals is to be able to stream content on it to an xbox 360. The majority of my music is stored in FLAC or ogg vorbis, so transcoding is necessary. So far the only options i have seen on the forums have been using fuppes or x360mediaserve. Both which seem to be unmaintained and lacking in features/buggy. Well doing research i stumbled upon coherence which seems to offer all the functionality I need and it is in active development.

Does anyone here have experience or suggestions? Has anyone actually tried using coherence?

---

### Post by Flarkis on 2009-10-06
bump?

---

### Post by KillaB7 on 2009-10-08
Just checked out the Coherence wiki.  Unless it handles more than mpeg2 video, it's of little use to me.

> Sony PlayStation 3
    There is a growing - yet subtle - relationship between Coherence and the PlayStation 3.
    The PS3 can browse the content of a Coherence MediaServer, playback mp3 audio and mpeg2 video files and display jpeg images.
    Kudos go to Christian Schaller for his patient debugging assistance.

I've been using Fuppes for ages now and it's great.  I've just recently been trying to enable video transcoding for MKV's, but can't seem to figure it out.
According to this post, transcoding "might" not work with MKV's:
[http://ubuntuforums.org/showpost.php?p=7527769&postcount=2](http://ubuntuforums.org/showpost.php?p=7527769&postcount=2)

Guess I'll have to give PS3 Media Server another try.

---

### Post by Flarkis on 2009-10-10
my problem is that the xbox 360 uses a broken implementation of UPnP. So alot of projects dont support it. I only need to transcode FLAC really in the end. I was reading that fuppes doesnt have support for rewind and fast forward though.

---

### Post by s1500 on 2009-10-13
> **Flarkis said:**
> I'm in the process right now of setting up a home server and one of my goals is to be able to stream content on it to an xbox 360. The majority of my music is stored in FLAC or ogg vorbis, so transcoding is necessary. So far the only options i have seen on the forums have been using fuppes or x360mediaserve. Both which seem to be unmaintained and lacking in features/buggy. Well doing research i stumbled upon coherence which seems to offer all the functionality I need and it is in active development.

Does anyone here have experience or suggestions? Has anyone actually tried using coherence?

I have an Xbox 360 + Linux server downstairs. Fuppes was working okay for me up until I upgraded to 9.04. That's when Fuppes outright refused to work, and it really ticked me off. I just installed the latest version, and it complains about some missing libavformat file, which I've had no luck reinstalling the lib from apt-get. 

x360mediaserve is okay, but it only does audio files. This package, and fuppes have a tendency to work painfully slow on startup if you have files in the thousands. 

I really wish there was a Linux package that worked every bit as good as Windows Media Player for sharing media to a 360. All packages I have tried are painful to configure, buggy, just don't plain work, feature deficient,  or cleverly hide the fact they only work with a PS3.

---

### Post by Flarkis on 2009-10-13
i actually had some luck with coherence, the only problem being that ubuntu installed python 2.6 well coherence is tested with 2.5. I`m going to work this weekend to see if i can get something rigged up.

---

### Post by jngrim on 2009-10-30
Does anyone know if the Coherence tutorial on Coherence?I am have been able to set up the Music, Pictures and Video folders for upnp devices to see and it works. However, I am trying to set up the IRadio Plugin and all I get is like 4 items when I view...Has anyone got there Iradio plugin working correctly? Also, has anyone been able to play these stations through a PS3? 

If not, can anyone suggest a media server that will stream shoutcast to PS3? thanks

---

### Post by Shhnap on 2009-11-03
You can get fuppes working just fine, with a little bit of work, on 9.10, see this thread by PorchSong: [http://ubuntuforums.org/showthread.php?t=1310511](http://ubuntuforums.org/showthread.php?t=1310511).

I can vouch that it has all of the information that you need and it happens to be really nice.

---

