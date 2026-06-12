---
title: "What's the best codec to capture screencasts in for editing?"
date: 2013-09-10
forum: Multimedia Software
---

### Post by coeg2 on 2013-09-10
I want to record some screencasts but i will require to do some editing afterwards. I have ffmpeg set up to record my second monitor and it's currently set to capture as .mp4. I don't know enough about video formats and i want to make sure i get the best possible quality uploaded to youtube. I understand that some compression happens on loading up videos too? Or is there a format that youtube prefers and it won't compress any further? So my question is two-fold - 

Which format should I capture at?
Which format should I export my final screencast as from either openshot or kdenlive?

Here is my current command -

ffmpeg -an -f x11grab -r 25 -s 1440x900 -i :0.0+1280 -vcodec libx264 -vpre lossless_medium -threads 0 $HOME/Screencasts/screencast_video_$DATE-$TIME.mp4

Any other tips would be great. Thanks :)

---

### Post by Bucky Ball on 2013-09-10
Welcome.

Which screencasts are you looking to capture? Could you provide a link? Might help.

---

### Post by coeg2 on 2013-09-10
Hi and thanks. I want to do some tutorials so I want to capture my own screencasts. I am able to do that with ffmpeg. I just want to know what combination would give me the best end result, the format of the initial screencast and the outputted format when I export them after first doing some editing.

---

### Post by FakeOutdoorsman on 2013-09-10
> **coeg2 said:**
> Or is there a format that youtube prefers and it won't compress any further?
There is not. YouTube will always, as far as I know, re-encode anything you feed it.

> **coeg2 said:**
> Which format should I capture at?
You should use a lossless format that is editor friendly. huffyuv comes to mind:
```
ffmpeg -f x11grab -r 25 -s 1440x900 -i :0.0+1280 -vcodec huffyuv output.mkv
```
This will result in a large file, but it can be considered to be temporary since you're planning on editing it. If your editor handles lossless H.264 video then you can use that instead. See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

> **coeg2 said:**
> Which format should I export my final screencast as from either openshot or kdenlive?
As high quality as practical for you to upload, so that means using libx264 for H.264 video. I know Kdenlive uses ffmpeg, but I'm not familiar with the presets. You can make a custom preset using the following settings:

```
ffmpeg -i input -vcodec libx264 -preset medium -crf 18 -acodec libfaac -aq 100 output.mp4
```

This should create an output that is roughly visually lossless, although the eventual colorspace conversion (on your end or YouTube's) from rgb to yuv will cause some artifacts and color loss that you may or may not notice. I'm not sure what can be done about that.

> **coeg2 said:**
> Here is my current command 
```

ffmpeg -an -f x11grab -r 25 -s 1440x900 -i :0.0+1280 -vcodec libx264 -vpre lossless_medium -threads 0 $HOME/Screencasts/screencast_video_$DATE-$TIME.mp4
```

Any other tips would be great. Thanks :)
I can't give any suggestions for this command because the complete ffmpeg console output showing the configuration and version information is missing.

---

