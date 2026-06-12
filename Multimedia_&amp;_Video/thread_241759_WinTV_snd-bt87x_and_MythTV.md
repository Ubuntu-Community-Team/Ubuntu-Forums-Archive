---
title: "WinTV snd-bt87x and MythTV"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by tbonius on 2006-08-22
I have a couple questions with an issue that I have been tearing my hair out over.  

I have a Hauppauge WinTV radio model 401 that I am using based on recommendations from various online resources.  I have a current installation of MythTV with Dapper and wanted to finally use btaudio instead of the line in on the sound card.  

Upon installation of Dapper.. I discovered that apparently btaudio has now been deprecated and replaced with snd-bt87x and now I have two dsp devices in /dev:

```
/dev/dsp
/dev/dsp1
```

Now /dev/dsp works great (My onboard Nforce2 audio card).. and I assume that /dev/dsp1 is the "btaudio" device.  I set the MythTV backend to use this device as its sound input device.. and set the frontend to use /dev/dsp as its output.

Upon starting MythTV and running "Live TV", it seems that I get audio along with my video.. but both seem to be very slow and lagged.

I tried grabbing audio directly from the device to see if I got slow-sounding audio:

```
sox -c 1 -u -r 32000 -t ossdsp /dev/dsp1 /storage/dsp1.wav

```

The resulting wav file also appears to be mis-sampled or slow. I assume that the audio coming in should be 32khz since that is what TV audio is broadcasted at.. but regarless of the samplerate I use.. I get the same result. 

If I remember correctly.. btaudio used to create two devices.. one digital and one analog so that there would be three dsp devices in all.

Is there something that I am missing in getting btaudio (snd-bt87x) going?  Any help is appreciated.

---

### Post by tbonius on 2006-08-25
I was hoping to post against my own thread so that this topic stays active and perhaps someone might have some insight to the subject.  I really would like to get the snd_bt87x module going and use the onboard sound on the Hauppauge card.  I dont really want to regress back to Breezy.. but will I have to.

Anyone have any thoughts on what I might be overlooking?

T

---

### Post by tbonius on 2006-09-14
So no one uses a Hauppauge WinTV that has btaudio/msp34xx capabilities?  No one knows what dsp device I should be using for sound input and capture?  Any input would be appreciated.

T

---

### Post by keredson on 2007-01-13
i have the same problem.  i can get correct audio by setting the sampling to 12000 (aplay /dev/dsp1 -r 12000), but myth doesn't support 12k sampling rates.

i don't have a solution yet.

---

### Post by nigel502 on 2007-02-02
I have the exact same issues on 6.10.

Were you guys ever able to resolve them?

---

### Post by Skerit on 2008-02-02
One year later I still have the same problem.. geez

---

### Post by h2gofast on 2008-03-28
I also have the same issue.  Picture in tvtime is fine, but no audio.

---

