---
title: "framegrabber NUV convert to mpeg2 or avi?"
date: 2009-03-30
forum: Mythbuntu
---

### Post by mathog on 2009-03-30
Hi,

I have a cheap framegrabber (SAA1730) in my myth box so that we can convert camcorder output (analog NTSC S-video). The video device shows up as /dev/video0 and the sound is routed through a patch cable from the card to the audio input and shows up as /dev/dsp. 
So far I have been able to:

1.  watch camcorder output using VLC (capture device option)
2.  watch camcorder output using MythTV (set up channel 100 to correspond to this device, and just "watch it" like a normal station.)
3.  record to NUV files using mythtv (record channel 100). 

The problem is, I need to get this video, with sound still present and sync'd to the video, at reasonable resolution into an AVI or MPEG2 so that it will work with Windows or Mac video editors.  I have tried a bunch of commands found with Google for recording directly from the framegrabber to a video file, but none of them worked.   (Partially  because the interfaces seem tot change rapidly on these programs and the examples never run verbatim, and partially, I think, because I may be missing libraries.)  I tried using stream export with VLC directly from the capture device, but the results were horrible or didn't work at all.

Anyway, the NUV recording works reliably, so it would be fine to convert that.  I don't want to "mythexport" exactly, there will not be DVD or CD image produced, just some individual video files. How does one do this?  Otherwise, if somebody can provide the magic formula to successfully make AVI or MPEG2 (with sound) directly from one of these framegrabbers that would be fine too.

Thanks.

---

### Post by theophile on 2009-03-30
This doesn't answer your question, but what is your camcorder model? If it has firewire (Sony i-link for example) you can grab the data in much, much higher quality that way and use mencoder or ffmpeg to do conversions. I think VLC can also do conversions or something like mplayer's dumpstream from which you could use mencoder/ffmpeg/etc.

---

### Post by mathog on 2009-03-30
> **theophile said:**
> This doesn't answer your question, but what is your camcorder model? If it has firewire (Sony i-link for example) you can grab the data in much, much higher quality that way and use mencoder or ffmpeg to do conversions. I think VLC can also do conversions or something like mplayer's dumpstream from which you could use mencoder/ffmpeg/etc.

It is an old Sony 8mm cassette model.  No firewire, no USB, nothing digital about it except the controller for its on screen displays.

I know that ***in theory*** VLC, mencoder, ffmpeg, and etc. can all do this, but finding the magic incantation to make them do so ***in practice*** has been difficult.

---

### Post by mathog on 2009-04-04
> **mathog said:**
> 
The problem is, I need to get this video, with sound still present and sync'd to the video, at reasonable resolution into an AVI or MPEG2 so that it will work with Windows or Mac video editors.

MUCH googling and experimentation let to this for conversion:

```
mencoder -ffourcc XVID -oac mp3lame \
 -ovc lavc -lavcopts \
vcodec=mpeg4:mv0:trell:v4mv:vbitrate=1500:ildct:aspect=4/3:acodec=mp2 \
 -lameopts cbr:br=128 \
 -o test.avi \
 test.nuv
```

and this for direct capture from the SAA7130 card:

```
mencoder -ffourcc XVID -oac mp3lame \
 -ovc lavc -lavcopts \
   vcodec=mpeg4:mv0:trell:v4mv:vbitrate=1500:ildct:aspect=4/3:acodec=mp2 \
 -lameopts cbr:br=128 \
 -tv driver=v4l2:norm=ntsc:input=2:adevice=/dev/dsp:width=640:height=480 \
 -o test.avi tv://
```

Key points:  
1.  The cbr:br=128 is crucial to keep audio and video in sync
2.  the vbitrate must be set depending upon the amount of motion or other change in the input.  For a filmed interview (talking head) 1000 or lower will work, but it will be full of image glitches if there is more motion.
3.  using mp3 instead of mp2 only makes it slightly smaller.

---

### Post by nickrout on 2009-04-04
> **mathog said:**
> MUCH googling and experimentation let to this for conversion:

```
mencoder -ffourcc XVID -oac mp3lame \
 -ovc lavc -lavcopts \
vcodec=mpeg4:mv0:trell:v4mv:vbitrate=1500:ildct:aspect=4/3:acodec=mp2 \
 -lameopts cbr:br=128 \
 -o test.avi \
 test.nuv
```

and this for direct capture from the SAA7130 card:

```
mencoder -ffourcc XVID -oac mp3lame \
 -ovc lavc -lavcopts \
   vcodec=mpeg4:mv0:trell:v4mv:vbitrate=1500:ildct:aspect=4/3:acodec=mp2 \
 -lameopts cbr:br=128 \
 -tv driver=v4l2:norm=ntsc:input=2:adevice=/dev/dsp:width=640:height=480 \
 -o test.avi tv://
```

Key points:  
1.  The cbr:br=128 is crucial to keep audio and video in sync
2.  the vbitrate must be set depending upon the amount of motion or other change in the input.  For a filmed interview (talking head) 1000 or lower will work, but it will be full of image glitches if there is more motion.
3.  using mp3 instead of mp2 only makes it slightly smaller.

Keeping synch is much much easier with cbr audio.

good to see you found a solution.

in the past I have used a pvr-150 which converts to mpeg-2.

Now I have a digital camcorder with pass-through, so it will convert analogue video from the old camcorder to AV and then upload it to the computer over firewire.

---

