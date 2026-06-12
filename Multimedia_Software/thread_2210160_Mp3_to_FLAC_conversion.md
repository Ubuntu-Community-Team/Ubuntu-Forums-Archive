---
title: "Mp3 to FLAC conversion"
date: 2014-03-09
forum: Multimedia Software
---

### Post by Owen_Murphy on 2014-03-09
Let me preface this by saying I know that is a stupid idea...

I am beginning to think that some of the FLAC files I have were once MP3s that someone had converted to FLAC, since they sound pretty terrible (even worse than some of the higher quality MP3s I have).  Has anyone heard of people taking MP3s and converting them to FLAC, then distributing the "lossy" FLAC files?

Is there anyway to detect to see if this has happened?  Is there some sort of signature you can look for in a file to see if it has been an MP3 in a previous life?  I'd like to be able to purge my library of any imposter FLAC files.

---

### Post by TheFu on 2014-03-09
It is possible to convert any audio file into FLAC.  If you get files from disreputable sources, you got what you asked for, IMHO.
Do any reputable sources distribute FLAC files?  I admit, my knowledge in that area is extremely limited.  

All my files were ripped directly from CDs that I own or a tiny number were purchased from Amazon as mp3s.  I'm not a fan of "virtual property" where I only get a license, not true ownership.  If my children cannot inherit the property forever, then it isn't real and I don't want to spend money on it.

Oh - and yes, that is a stupid idea. I hope you didn't pay any money.

---

### Post by Yellow Pasque on 2014-03-10
See conversation here:
[http://www.head-fi.org/t/415887/how-to-check-if-a-flac-file-is-real/15](http://www.head-fi.org/t/415887/how-to-check-if-a-flac-file-is-real/15)

Yes, people convert mp3->flac either out of ignorance or because they think such social engineering makes them l33t.

Homework exercise: Take a flac file that you know to be good and (making sure to keep the original) transcode it to mp3, then back to flac. Then compare the two flacs in Audacity and see if you can tell the difference from the spectrograms.

---

### Post by shantiq on 2014-03-10
yes people do that to cheat or out of ignorance     here is a track which shows the same in the flac version and the mp3 version
it shows that the flac is a fake


you can use     ```
sudo apt-get install spek
```   to verify files as i did here using [spek]("http://spek.cc/")  flac specs should be way higher on the graphic if it truly was a flac

[IMG]http://s20.postimg.org/rz3yok3kt/02_Sunrise_of_the_Planetary_Dream_Collector_fla.png[/IMG]

[IMG]http://s20.postimg.org/9ky0ybgnx/Riley_Terry_Cherry_Don_Koln_1975_02_Sunrise_Of_T.png[/IMG]

---

### Post by Owen_Murphy on 2014-03-10
So I've been looking at various files in Spek, and I've noticed that all of the FLACs that I've converted to MP3 (with soundconverter) look like they are clipped at around 17kHz and the FLACs that I have converted with Audactiy clip at about 20kHz.  I guess the different programs use different algorithms to encode the MP3s?  Both programs were set to produce MP3s at 320kbps  

Some of the MP3s that I acquired as MP3s (they were never FLACs) have a spectrum that reaches all the way to 22kHz.

---

