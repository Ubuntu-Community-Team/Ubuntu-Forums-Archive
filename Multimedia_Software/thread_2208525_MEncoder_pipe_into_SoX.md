---
title: "MEncoder pipe into SoX"
date: 2014-02-28
forum: Multimedia Software
---

### Post by Valpskott on 2014-02-28
I'm trying to pipe audio output from MEncoder into SoX to no avail.

```
mencoder -aid 1 input.avi -of rawaudio -oac mp3lame -ovc copy | \
sox -t mp3 - output.mp3 gain -3
```

The input is an avi file with 3 different audiotracks and I've only found mencoder able to extract specific tracks.
I've been at this for hours, looking at documentation of both mencoder and sox, but can't determine where the problem lies.
The mp3-format isn't a nessecity for me, any format (preferably lossless) with a succesful pipe will suffice.

Any help would be much appreciated.

---

### Post by andrew.46 on 2014-02-28
> **Valpskott said:**
> Any help would be much appreciated.

Well, it has been a long time since I have used MEncoder (I suspect you would be better using FFmpeg) but you could always try:

```
mencoder  **[COLOR="#FF0000"]-really-quiet[/COLOR]** -aid 1 input.avi -of rawaudio -oac mp3lame -ovc copy**[COLOR="#FF0000"] -o -[/COLOR]** | \
sox -t mp3 - output.mp3 gain -3
``` 

I apologise for not testing this...

---

### Post by Valpskott on 2014-03-01
Ohh, so I had to put "-o -" in the mencoder command. I thought "-" was sox own syntax, but it seemed to work. Thank you very very much.
On a side note, I usually use ffmpeg, but while writing the script I found someone saying ffmpeg only have support for one audio-stream and the avi files I create have 3 individual audio-streams (one stereo for game sounds/music, one mono for my voice, one mono for skype).

---

### Post by andrew.46 on 2014-03-01
Good to hear that my lucky guess paid off :). With FFmpeg you should be able to select whichever stream you want with the *-map* option, perhaps make another thread along this line and the Forum's FFmpeg experts might help out?

---

