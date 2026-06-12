---
title: "What Streaming Audio Ripper"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by AlistairH on 2007-03-03
On Windows I use RipCast to record and separate individual mp3 files from streaming audio internet radio broadcasts. Is there any comparable Linux tools to do the same job and what would you recommend?

Thanks

Ali

---

### Post by Dekunuts on 2007-03-03
Give Audacity a try, it can record from various sources, including pcm

---

### Post by ubromtoo on 2007-03-03
Streamripper/Streamtuner has been working for me since I downloaded it a few

days ago; but since it won't edit the audio files, today I downloaded Audacity.

     Problem: when I go to Applications >Sound >Audacity , right away there is this

notice:

      THERE WAS AN ERROR INITAILIZING THE AUDIO I/O LAYER

      YOU WILL NOT BE ABLE TO PLAY OR RECORD AUDIO

       ERROR: HOST ERROR

     So what is a newbie like me to do about this?  Thank you            :guitar:

---

### Post by AlistairH on 2007-03-04
Thanks for the replies.

I get the impression from the Audacity website that it can only record up to a max of 96k. Most of the stations I listen to broadcast 128k.

Also, perhaps the most important function I want from such a tool is the ability to automatically split the stream into individual song mp3s without the need for me to go in and do it manually. Is Audacity, or any other streaming audio ripper out there, able to do that?

Ali

---

### Post by ubromtoo on 2007-03-05
AlistairH:


     Streamtuner/streamripper does what you want, so long as the stream 

contains the info ("metadata") on Artist, Song, Time etc..  Some streams

do, some don't.

      For the ones that don't, I'd like to be able to edit the sound files; that's

why I downloaded Audacity.  However, it won't work on my computer so far.

       Can anyone recommend a good sound-file editor for me?

     'preciate any help         :KS

---

### Post by AlistairH on 2007-03-15
I've been using strteamripper for a week and it works a treat. Thanks Ubromtoo

---

### Post by mcduck on 2007-03-15
> **ubromtoo said:**
> Streamripper/Streamtuner has been working for me since I downloaded it a few

days ago; but since it won't edit the audio files, today I downloaded Audacity.

     Problem: when I go to Applications >Sound >Audacity , right away there is this

notice:

      THERE WAS AN ERROR INITAILIZING THE AUDIO I/O LAYER

      YOU WILL NOT BE ABLE TO PLAY OR RECORD AUDIO

       ERROR: HOST ERROR

     So what is a newbie like me to do about this?  Thank you            :guitar:
Audacity uses the old OSS sound, that can only be used by one application at a time. Close all other programs that use sound and Audacity should run just fine.

---

### Post by ubromtoo on 2007-03-22
McDuck:

      Thanks for the advice for Audacity- now it plays fine!

 however....still no luck getting mhWaveEdit to play; whether I try to play

mp3 or wav or whatever, I get:

        
               The sound format of this file is not supported for playing.


        Any advice ?  mhWaveEdit is much easier for a newbie like me to use,

that's why I ask.         :)

---

### Post by robinpc on 2008-07-15
I got that too.  Go to prefs and switch the audio config from JACK to ALSA and things may improve

---

