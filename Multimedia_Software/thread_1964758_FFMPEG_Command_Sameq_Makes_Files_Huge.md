---
title: "FFMPEG Command Sameq Makes Files Huge"
date: 2012-04-24
forum: Multimedia Software
---

### Post by ChannelZ28 on 2012-04-24
i have some musicals in wmv format where i want to cut out certain songs and i usually use avidemux for movie editing. avidemux doesnt like wmv video so i want to convert them to something else so i can edit.

i also have boilsoft video editor that i use in wine, but it doesnt do wmv video either.

i use ffmpeg and i tried the -sameq command to convert to avi and the resulting files were like 4 times larger. i want the same quality AND same size video. what should i do different?

---

### Post by FakeOutdoorsman on 2012-04-25
You have several options. This first thing to do is to forget about *-sameq*. It doesn't mean "same quality" and is not designed to be used between different formats.

If you want to cut out a section of video and discard the rest that is easy to do with ffmpeg and it can do it losslessly. For example, if you want to skip the first 1 minute and 23 seconds, and then keep the following 10 seconds:
```
ffmpeg -i input.wmv -ss 00:01:23 -t 10 -vcodec copy -acodec copy song1.wmv
```
Basically ffmpeg is "copying and pasting" the input to the output and not re-encoding anything. However, if you want to cut out the middle of a video and join the sections the easiest method is to probably use a video editor.

Since avidemux doesn't like WMV you can either try another editor such as Kdenlive or Openshot. If they don't like WMV either, or you don't want to use another editor you can convert the file as you already mentioned. I recommend using a lossless format as an intermediate editing file. It should be editor friendly and will preserve the quality of your video. If you use a lossy format then you will lose quality although it may not be noticeable depending on your settings. The downside of a lossless format is that the file size will be huge, but these are usually temporary anyway.

```
ffmpeg -i input.wmv -vcodec huffyuv -acodec pcm_s16le output.mkv
```

You can then use this output in your editor.

---

### Post by ChannelZ28 on 2012-04-25
awesome, thanks. thts great information. i dont actually know yet if i want to join the files, it might be good enough to have individual songs. using that winff command, will that delete the original file? or can i do it multiple times, cutting 4 or 5 files out of the main one?

otherwise, if i convert to lossless, like mkv and then use that in the editor, once its been edited i would then compress it back to keep the file small? that kind of seems like a lot of steps.

i will try those other editors you mentioned and see if they work. thanks.

---

### Post by FakeOutdoorsman on 2012-04-25
> **ChannelZ28 said:**
> using that winff command, will that delete the original file? or can i do it multiple times, cutting 4 or 5 files out of the main one?
The input file will remain untouched and you can make as many clips as you like.

> **ChannelZ28 said:**
> otherwise, if i convert to lossless, like mkv and then use that in the editor, once its been edited i would then compress it back to keep the file small? that kind of seems like a lot of steps.
Yes. The editor will probably give you a choice of formats you can export to.

---

### Post by ChannelZ28 on 2012-04-27
thanks.

---

