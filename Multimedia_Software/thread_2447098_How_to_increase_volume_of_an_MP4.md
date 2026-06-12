---
title: "How to increase volume of an MP4"
date: 2020-07-12
forum: Multimedia Software
---

### Post by Autodave on 2020-07-12
Very new to video recording.  I am using OBS which works quite well, but some folks are complaining about the volume is too low.  When recording, the VU meter is constantly peaking high in the yellow zone, so I really don't want to go any higher than that.

Is there a way / program that I can use to raise the volume after the video is saved?  I realize that I will probably have to recode it and that is OK if that is the only way.

---

### Post by Dennis N on 2020-07-12
Audacity has **Effect > Amplify** which you would apply to an already recorded file.

Edit: This probably won't work since its a video. Unless Audacity can import and re-save just the audio track. Sorry.

---

### Post by CatKiller on 2020-07-12
The term you'll be looking for is *compression*. It lowers the peaks so that you can then increase the levels of everything.

---

### Post by SeijiSensei on 2020-07-12
ffmpeg can do this.

[https://trac.ffmpeg.org/wiki/AudioVolume](https://trac.ffmpeg.org/wiki/AudioVolume)

---

### Post by Autodave on 2020-07-12
SeijiSensei: and that will work on an MP4?  Will I have to encode it again then?

What I am doing is recording our church service.  Using OBS and taking the recording level to the red zone, it is still somewhat too soft when replaying.  What I want to do is to raise the volume after the recording is finished but before I upload it.  Will this do what I want?

And to expand on that: does anyone know why the level is low?  Is there something that I am missing when recording it?  I used Audacity for years to just do the audio portion and I had no problem with the volume level.  I really do not know why the audio is so soft using OBS.

---

### Post by SeijiSensei on 2020-07-12
I ran a couple of tests and found this works with .mp4 files.

```
ffmpeg -i input.mp4 -vcodec copy  -filter:a "volume=1.5"  output.mp4  
```

If the file has soft subtitles (.ass or .srt) you'll need to read the documentation to carry the subtitles over to the output file or burn them into the image.

This works quite quickly since you don't need to render the video into the output file.

---

### Post by Autodave on 2020-07-13
How do I actually do this....I am lost.  I am assuming that somewhere I need to tell it what file to do that to?  I don't see how to that.

Let me make sure that I am understood in what I am trying to do.  I want to take an MP4 file that I created and then raise the volume of that file before I upload it to YouTube.

---

### Post by Dennis N on 2020-07-13
Use the ffmpeg man page as a guide. Substitute the path/file name of the existing video file for input.mp4. Replace output.mp4 by the path/file name for the result to be saved. So it does not change the original, but makes another copy for the output.

---

### Post by SeijiSensei on 2020-07-13
```
ffmpeg -i input.mp4 -vcodec copy  -filter:a "volume=1.5"  output.mp4  
```

Use "cd" to go to the directory which holds your file. Replace "input.mp4" with the name of the file to be converted. Replace "output.mp4" with the name you'd like to give to the resulting file with the augmented volume.

```

-i  - identifies the input file

-vcodec copy - copy the video stream from the input to the output without alteration

-filter:a "volume=1.5" - use an audio filter ("filter:a") to increase the volume by 150%

```

---

### Post by Autodave on 2020-07-13
Thank you: both of you.  I will give it a go and report back.

---

### Post by Autodave on 2020-07-15
I don't know what to say now.  I tried that command many times and always kept coming up with errors.  As I recall, it said that file didn't exist, but I copied and pasted the name of the file into the terminal.

Anyways, playing with OBS and adding the compressor and expander filters seems to have fixed the issue.  Thanks for your help!

---

### Post by SeijiSensei on 2020-07-15
Maybe you weren't running ffmpeg in the directory where the file resides?  If so, you would have needed "/path/to/the/input.mp4".

Anyway, glad you solved your problem.

---

### Post by Autodave on 2020-07-15
I was in the correct directory.  Brain may have been to fried from fighting with all of this for a few weeks.  I will try again one of these days.  Thanks for your help!

---

