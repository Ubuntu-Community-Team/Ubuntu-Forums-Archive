---
title: "Live TV choppy but recorded programmes fine??!!"
date: 2008-01-12
forum: Mythbuntu
---

### Post by zzztownsend on 2008-01-12
Can anyone help me on this problem...?

In live TV the video playback is slow - say 3 frames per second - however...

recorded programmes playback properly, as do DVDs and even programmes that I watch while they are recording

what's the difference between linve tv and watching a programme while its recording??

spec - ubuntu gutsy desktop/backend/frontend
ICore2duo 2gig ram, 500Giig HDD
nova-t-500 DVB -t  dual tuner card - driver/firmware installley using the mythtv wiki.( UK freeview)
 PAL TV out (s-video to scart lead)
/mythtv recordings to an XFS partition -

any help apprecieated

Cheers 

Matt

---

### Post by rusty0101 on 2008-01-13
Just as an observation, live tv is watching while recording. (You can see what is being recorded as it's being watched on another system through a front end where you switch the view profile in 'recorded programs' to live recordings. That does require multiple front ends, so most people don't select it, but it's there.)

You may want to take a look at tips for tweeking hard drive access. The big step here is that you are trying to read from the live recording file at the same time as it is being recorded. That may be causing issues for read-write buffers, etc. If you select to record the show, then start watching that recording after it has been recording for a few minutes, you will be looking at different sectors on the hard disk, which the controllers may behandling better. Also the read-ahead buffer will kick in and put more video in memory to be watched while write activities are happening.

I am also not sure what sort of throughput you are looking at as being right for your systems hard drive. Besides the archetecture of the hard drives, it does depend upon the requirements of the video stream. HD format video being downconverted to PAL out is going to have different hard disk and processor requirements than PAL streams.

Hope that is somewhat useful.

---

### Post by kitsos on 2008-01-22
I have the same problem! 

I was using a PVR 150 and all was fine...as soon as i started using the Nova T the problems begun. I have tied testing the card using dvbstream and mplayer and works excellent even in full screen...i'm pretty sure my hardware is more than adequately fast (Core 2 Duo 2.1 with a raptor HD)...it must be something that is going wrong specifically with mythtv. 

running mythtv -v playback shows some dropped video frames and out of sync sound...

Did you manage to find a solution? Has anybody had similar problems or any hints at all? Any help would be mostly appriciated!

Thanks

---

### Post by Rhiadon on 2008-01-23
I had a similar problem using two ATSC-110 cards. So it's not exactly the same but it might be important. I got the prebuffering pauses just like you are getting. 

To fix it I checked the "extra audio buffering" checkbox under playback. Apparently my sound card has a tiny audio buffer. I'm not certain. As soon as that was checked my Live TV problems went away.

Also useful would be to use realtime priority threads. To do this you'll need to use rlimits and check the "use realtime priority threads" under playback. I don't have a link handy but there is plenty of data around on how to use rlimits.

---

### Post by zzztownsend on 2008-01-25
thanks for your replys to this guys - I haven't made much progress so far but I have been able to repeat the problem outside of mythtv

$tzap <whatever channel>
$mplayer /dev/dvb/adapter0/dev0    
is choppy

but...
$tzap <whatever channel>
$cat /dev/dvb/adapter0/dev0 > junk.file
(from a new terminal) $mplayer junk.file
works fine,

Conclusion - I think that rusty1010 you are probably right - any suggestions on how I would get started in poking around into buffers / HDD read/write etc

cheers

matt

---

### Post by kitsos on 2008-01-26
I tried using the extra audio buffering and rlimits without any luck. However, increasing the cache size seems to help.

After tzap-ing 
Try:

```
dvbstream -o -ps 600 601 -qam 16 -cr 3_4 | mplayer -vo gl2 -cache 16384 -
```

This starts playback using the X11 openGL driver with a big cache.. it seems to solve my problems of viewing liveTV with mplayer...Just the occasional artifact here and there...

I still can't find out how you can increase the cache size for MythTV.. you can play with the ringbuffer size in versions 0.18 and before that..can't find any settings for 0.20...there's an HD ringbuffer size but that doesn't help in this case.

Any clues on how to set the cache for LiveTV in MythTV?

Regards

---

### Post by kitsos on 2008-01-26
It's finally working for me!!!

Matt is your video card by Nvidia?
If yes read on...

I followed the suggestion on this thread:

[http://ubuntuforums.org/showthread.php?t=404863]("http://ubuntuforums.org/showthread.php?t=404863")

and added ```
libXvMCNVIDIA_dynamic.so.1
``` in my /etc/X11/XvMCConfig (it has to be the first entry in the file)
restart your X server...
go to mythtv frontend playback settings and use Standart XvMC for the encoding...
 
and enjoy...

---

