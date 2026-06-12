---
title: "Sound Converter Trouble"
date: 2009-05-31
forum: Multimedia Software
---

### Post by Mirages on 2009-05-31
hi I just got the "Sound Converter" from the repository and I am trying to convert some .wav files in to mp3 files. the option to convert to mp3 is displayed in the applications properties but when I start converting it doesn't work and converts nothing.

I am rather new to linux/ubuntu but I knew enough to take a look in the synaptic package manager and search "mp3" the only package I have installed is "lame" which I guess allows me to play back mp3 audio files? there are quite a few so which package do I need to convert (encode?) audio files into mp3 files?

I also tried to convert the wav files into ogg vorbis but that didn't work either. so I searched the synaptic package manager and I have no packages installed that have to do with "ogg".

So overall what I am asking is if someone could tell me what I need to do to make the sound converter 100% work.

***this just came to me. would installing the ubuntu restricted extras solve all my problems?***

thanks in advance!

---

### Post by xc3RnbFO8P on 2009-06-01
> ***this just came to me. would installing the ubuntu restricted extras solve all my problems?***
It should solve your MP3 encoding problem

---

### Post by Mirages on 2009-06-01
thanks for the help, I was almost there, I was just to afraid to try, because the "restricted" title and the pop-up afterwards to confirm, and the 1-star rating had me thinking it wasn't a good package to try.

thanks again!

---

### Post by 7Lj3)(P38J on 2009-07-18
Well I have exactly the same problem, and it persists even after installing the Ubuntu restricted extras!
A pity the need for so many useless workarounds.... I still can't convert a WMA or whatever into  OGG or MP3.

---

### Post by cozmicharlie on 2009-07-18
They are not "workarounds" - it is because of the basic philosophy of linux that some codecs (proprietary codecs) are not installed. Follow the instructions in this thread and you should be able to play all your media [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).  Each distro handles this differently - some add the codecs some don't.  Make sure you add the medibuntu repository and install FFMPEG.

Personally, I prefer other programs than Sound Converter.  I like Sound Konverter (with a K - this is kde and will install a lot of dependencies so if you do not want all the kde stuff then you may not want to install this).  I like PACPL (there is a tutorial for installing from source but it is in the repos now so you can install it via Synaptic.  The tutorial though also shows how to use it so it is worth reading.  

Good luck

---

### Post by dartmusic on 2009-07-20
There was (and possibly still is?) an ongoing issue with Sound Converter where conversions will fail if you try to place the converted files into your home folder.  If you simply create a folder elsewhere or even IN your home folder (i.e., /home/[username]/transcoded,or whatever you want to name the folder other than transcoded) then it should complete the conversions successfully, granting you have the appropriate codecs installed.

Hope this helps...Sound Converter is definitely my favorite package for format conversion around, even with this silly bug.

---

### Post by Oldude on 2009-07-28
Thanks for this solution!  I use 8.10 and Sound Converter did not convert.
Once I changed the output file to /Home/'username'/Music I had no problems.

---

### Post by cozmicharlie on 2009-07-28
> **dartmusic said:**
> There was (and possibly still is?) an ongoing issue with Sound Converter where conversions will fail if you try to place the converted files into your home folder.  If you simply create a folder elsewhere or even IN your home folder (i.e., /home/[username]/transcoded,or whatever you want to name the folder other than transcoded) then it should complete the conversions successfully, granting you have the appropriate codecs installed.

Hope this helps...Sound Converter is definitely my favorite package for format conversion around, even with this silly bug.

This is very helpful info - thanks dartmusic.

---

