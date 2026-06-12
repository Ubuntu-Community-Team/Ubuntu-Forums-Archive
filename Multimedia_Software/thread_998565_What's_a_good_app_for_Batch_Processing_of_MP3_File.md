---
title: "What's a good app for Batch Processing of MP3 Files (Increase Volume for Whole Album)"
date: 2008-11-30
forum: Multimedia Software
---

### Post by OzzyFrank on 2008-11-30
Hi all. OK, I am aware there are plenty of apps for editing audio files of all sorts, but would like your views on the best one for batch processing, so I don't have to edit each one separately. The scenario is that I rip whole albums to my collection as MP3 files, and of course the earlier an album was released, the lower the volume generally is. So to avoid having massively fluctuating volumes while playing my collection (especially on Random, which gets annoying), I am planning to increase the volume of these older albums to match that of current releases (and in a few cases lower it).

So what I would like is to be able to open/import an album/folder, set the volume based on comparing one song with something more recent, and have that volume setting be applied to all the tracks listed. I am not fussed whether this be an app which is just basically a GUI for accomplishing this task alone or an easy way to do it within one of the more comprehensive apps like Audacity, Audacious or the like. I just would prefer not to have to do each track individually, (preferably) to be able to preview the new volume, and to have the same volume level applied to the whole album. What is your say on which app is best for this task? Cheers

---

### Post by cariboo on 2008-12-01
HAve a look at mp3gain, it is in the repositories. It is a command line program, I've used it quite a bit to set the gain on my collection of mp3. to see the options available in a terminal type:

```
mp3gain -h
```

and of course for more info:

```
man mp3gain
```

Jim

---

### Post by OzzyFrank on 2008-12-01
Hiya. I ended up trying the Windows version, for 3 reasons: I found that instantly, I was in Windows anyway, and I couldn't refuse the fact it has a GUI. Great little app... I did do some reading and looked at some reviews and while I might not get it to equalize my whole collection, it is still great.

For those interested, [COLOR="#8b0000"]**mp3gain**[/COLOR] uses some clever technology to analyse and equalize all tracks, but it didn't surprise me to read that it prefers to lower the volume of louder tracks than raise that of lower recordings. If that was all it could do, I would look at this app as a lost cause, because of course I want to be able to raise the volume of older albums, not lower that of more current ones.

Luckily there are a few options, one of them being Constant Gain, which just lets you raise or lower the volumes of all selected tracks. I can see that a quick command in a terminal opened in the folder of an old album would suffice, but for selecting a bunch of such albums at once for batch processing would be easier with a GUI. For those who want a GUI, there are a couple of apps I found: **[COLOR="DarkRed"]QtGain[/COLOR]** and [COLOR="#8b0000"]**easyMP3gain**[/COLOR]. There is also **[COLOR="#8b0000"]JavaMP3Gain[/COLOR]**, which you can imagine needs Java - no big deal, since most systems these days have it anyway, but apparently it doesn't have all the options the command (and Windows UI) has. I've yet to look at **[COLOR="#8b0000"]easyMP3gain[/COLOR]**, but it looks promising.

---

### Post by OzzyFrank on 2008-12-01
For those who want to use the commandline but what to do as I do, ie not equalize the whole collection, just play with the volume of certain tracks or albums:

**mp3gain -r -d -3 myloudsong.mp3**

That will lower the volume of a specific track by 3 dB; the following will raise the raise the volume of all track in the folder by 5dB:

**mp3gain -r -d 5.0 *.mp3**

Also, if you want to preserve the original file's timestamp, use the -p option -- otherwise MP3Gain will update the timestamp each time you modify the file.

Another option is to apply a gain level directly to the current volume level of a file using the -g option:

**mp3gain -g 3 myquietsong.mp3** 

This will add 3 dB to the song as it is, rather than calculating from the default volume as you would with the -r -d options.

---

### Post by OzzyFrank on 2008-12-03
**[COLOR="Red"]easyMP3gain[/COLOR]** is the way to go for those used to the Windows version of **mp3gain** with GUI. Haven't actually tested it yet, but since it is just a frontend for the command, I gather it should be fine. It was the UI I was interested in, and it is very similar to the Windows app.

---

