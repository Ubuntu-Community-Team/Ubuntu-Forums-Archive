---
title: "Ripping CDs Without Splitting Tracks"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by AlistairH on 2007-03-12
Many of the CDs I listen to have tracks that run into each other (yes, I know, I'm an aging hippy!). In Windoze I used MusicMatch to rip CDs which, to the best of my knowledge, was the only product that allowed you to specify a start and stop time for the rip thereby enabling you to span track intersections and treat them as one mp3.

Is there an equivalent product available in the Linux world that has this functionality and save me the bother of having to stitch the files together again?

Ali

---

### Post by MetalMusicAddict on 2007-03-12
I have been looking into this as well. I use Grip (best linux ripper/encoder IMO. see my sig) and havnt found a way yet.

---

### Post by bswilson on 2007-03-12
I don't know of an MP3 ripping program specifically, but if you'll download and install **Audacity,** then you can load up any music file (track) and chop off the beginning or end as you see fit, if you know the start and stop times of the tracks.

```
sudo apt-get update && sudo apt-get install audacity
```

---

### Post by AlistairH on 2007-03-12
Thanks, I'll check Grip out.

I've already got Audacity but I was hoping to avoid having to glue them all together.

It's a general gripe I have with virtually all CD ripping software, irrespective of platform. As someone who tends to listen to complete albums rather than individual songs there's occasion when I might want to record the whole album, or at least large portions of it as one audio file. I cannot understand why this facility is not generally available in ripping software.

Thanks again.

---

### Post by AlistairH on 2007-03-25
I've just downloaded Grip as I couldn't get Sound Juicer to rip to MP3 properly. I'm glad I did because Grip has the ability to rip multiple, concurrent tracks as one audio file.

On the Grip interface you'll find the RIP tab. There you'll find the option to Rip Partial Track which implies you can rip a section of a track rather than the whole thing. However, use the following trick to rip multiple tracks as one file.

1. With a CD in your CDROM drive switch to the **TRACKS** tab on Grip.
2. Select the first track of the multiple tracks you wish to rip.
3. Switch back to the **RIP** tab and make sure that **Rip Partial Track** checkbox is selected.
4. Take a note of the figure in the **End Sector** box.
5. Switch back to the **TRACKS** tab and select the next track.
6. Back to the **RIP** tab and take a note of the **End Sector** figure for this track.
7. Carry on doing this for how many consecutive tracks you want to rip as one audio file.
8. On the **TRACKS** tab make sure only the first song has a tick mark in the corresponding  **Rip** checkbox.
9. Switch back to the **RIP** tab and in the **Start Sector** box make sure it has a 0 (zero).
10. In the **End Sector** box the figure should be the total of all the End Sector figures you recorded in the previous steps.

Click on the **Rip + Encode** button and away you go.

You can also do this in reverse by selecting the last track you want and putting a negative number in for the Start Sector figure. A little bit more complicated but it works.

The Grip version I'm using, ver 3.3.1, complains afterward when I try to quit the application that it is busy doing something. However, the audio file has already been created. Simply confirm that you want to quit doesn't seem to cause any harm. I'm presuming this error has something to do with the technique I'm using here but as it does appear to be critical I won't lose sleep over it.

---

