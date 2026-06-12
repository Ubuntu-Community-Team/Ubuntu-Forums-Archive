---
title: "Ripping a  ( AUDIO DVD) NOT (DVD AUDIO)"
date: 2008-09-09
forum: Multimedia Software
---

### Post by robertrej on 2008-09-09
I have been trying to find a way to rip my own audio-dvd on linux without
buying a $40.00 program like Apollo dvd for windows.
A standard dvd /cd player will play a (AUDIO DVD) and of course the dvd
allows much more storage compared to a cd.

The technology is very new and may not have be developed by MECODER
or FFMPEG yet. I did notice that when I ran Appollo dvd it transformed
my wav file format to vob format.

So does any one have any ideas on ripping a (AUDIO-DVD)on LINUX?

                         Thanks very much
                         Bob

---

### Post by theacoustician on 2008-09-09
> **robertrej said:**
> I have been trying to find a way to rip my own audio-dvd on linux without
buying a $40.00 program like Apollo dvd for windows.
A standard dvd /cd player will play a (AUDIO DVD) and of course the dvd
allows much more storage compared to a cd.

The technology is very new and may not have be developed by MECODER
or FFMPEG yet. I did notice that when I ran Appollo dvd it transformed
my wav file format to vob format.

So does any one have any ideas on ripping a (AUDIO-DVD)on LINUX?

                         Thanks very much
                         BobWhat DVD is it?  I've never heard of such a thing.

---

### Post by robertrej on 2008-09-09
The Audio DVD I am referring to is a standard   DVD-R , I use Sony DVD-R
and they work well in my 3 year old  TOSHIBA DVD player.The actual
software needed to perform this is very new as far as I know. 

Please see the attached site for more info:
[http://www.createdvd.net/audio_dvd_creator.htm](http://www.createdvd.net/audio_dvd_creator.htm)

I have no affiliation to the above site.

Audio DVD is like  Audio  CD but on a DVD instead.


   I have  burned 1 audio DVD so far and its great!

                            Cheers
                            Bob

---

### Post by theacoustician on 2008-09-09
> **robertrej said:**
> The Audio DVD I am referring to is a standard   DVD-R , I use Sony DVD-R
and they work well in my 3 year old  TOSHIBA DVD player.The actual
software needed to perform this is very new as far as I know. 

Please see the attached site for more info:
[http://www.createdvd.net/audio_dvd_creator.htm](http://www.createdvd.net/audio_dvd_creator.htm)

I have no affiliation to the above site.

Audio DVD is like  Audio  CD but on a DVD instead.


   I have  burned 1 audio DVD so far and its great!

                            Cheers
                            Bob
Ok, if you burned it, why do you need to rip it?  Or are you asking how do you make such a disc in Linux?

From what I can tell from your link, this isn't new at all.  All its doing is burning a DVD Video without the video track in place and generating an IFO file to set the track markers.

So to answer both sides of the questions above ... really anything should work.  Most DVD rippers in Linux can rip the audio separately from the video on a disc.  Equally, almost every program I've used to make DVDs allows you to add video and audio separately.  However, you might want to just skip the middle man er disc in this case and look into a media center PC. MythTV + Ubuntu is a lovely thing.

---

### Post by robertrej on 2008-09-10
Well I had not even considered what you are stating could been done
with existing linux software. I will certainly try that today and let you
know how it works. The way the various software makers discribe it only
there software could perform this function.I must admit I use the terms
ripping  and burning as the same process which may be somewhat wrong.

              In any case thanks for your info on this matter!


                           Get back to you soon/cheers
                           Bob

---

### Post by robertrej on 2008-09-12
Well I managed to burn a very large batch of music to my DVD-R disc
and it ran just fine on my Toshiba DVD VIDEO PLAYER SD3990.
I did not insert a menu but no problem I just wanted to have as
much music on as few disc's as possible.
I converted my older cd's which are wav format to mp3 and used k3b 
to burn with setting "NEW DATA DVD project ".I will try tomorrow
to create sub folders or menu's.


                        Thanks for your input/ Cheers
                        Bob       :)

---

### Post by seanos on 2008-09-17
Bob, if possible you should avoid converting the CDs to mp3; just extract to WAV files.  That way the data won't be converted *twice* which will reduce it's quality.  Requires more disk space, but a better result.

Cheers, Seán

---

### Post by cajunaggie on 2008-10-18
I likewise am trying to burn an audio DVD, rather than a video DVD. If I'm reading this correctly, all I need to do is burn the audio files as a data DVD, put it in my DVD player and press play. Is this right?:confused:

---

### Post by chitowner2 on 2009-05-06
> **cajunaggie said:**
> I likewise am trying to burn an audio DVD, rather than a video DVD. If I'm reading this correctly, all I need to do is burn the audio files as a data DVD, put it in my DVD player and press play. Is this right?:confused:


Yo! Did everybody lose interest here? No replies in 7 months?

I am interested in this also for same reasons; I want to burn an "audio-DVD" (**NOT** a "DVD-audio" disc!), but I am not sure what issues might be involved.

Anybody??:confused:

---

### Post by robertrej on 2009-05-21
I am still interested on this subject to be sure and as stated
above have been only able to burning mp3 to DVD . A very big issue
is of course what type of DVD player you have.I know that
you can combine audio and video to kind of fool the dvd player
to play your audio which I have been working on for a while
and its a little tricky .I had to combine  a mpg video
with audio than convert to DIVX but the sound was not great.
I really wanted to play ac3 5.1 on dvd but this seems a little
more difficult.I am now having problems with a new message:
'big-endian not yet supported' which is new.So thats really
a big headache as well.There is a program you can buy to encode
audio to dvd but I like free things.I can not run besweet on linux so thats another project I am on.Well I would like feed
back on any or all ideas on the above issues.

                   Thanks/have a good day
                    Bob

---

### Post by lukeiamyourfather on 2009-05-21
It seems like you're looking for a solution to a problem that you've created in the first place. So the root of the problem isn't what software to use to rip a DVD-A, but maybe what would work better than a DVD-A for storing music? Creating an DVD-A as if it were just a really big CD seems like a Rube Goldberg machine just to get music to a home theater.

Chances are the homemade DVD-A was made from MP3 files or another lossy source so putting that data back onto a media that's native lossless is a moot point because the data was already lost when being ripped as a lossy format. Then ripping it again to another lossy format only exacerbates the issue. You might as well just put the original audio files on a DVD as data since 99.9% of the DVD and BD players out there can play many audio formats from data discs (CD and DVD). Many will even play lossless codecs like FLAC should the source be lossless.

This might have been a cool feature say 10 years ago, but today its taking a step backwards. There's no software specifically for this not because its new, but because its old. DVD-A launched in 2000, never gained any steam, and is now defunct. That's why there's no software specifically for it. Cheers!

EDIT: Looks like there's some software out there still, check this out if you haven't seen it yet.

[http://dvd-audio.sourceforge.net/](http://dvd-audio.sourceforge.net/)

---

