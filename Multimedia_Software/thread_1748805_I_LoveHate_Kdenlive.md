---
title: "I Love/Hate Kdenlive"
date: 2011-05-03
forum: Multimedia Software
---

### Post by decoherence on 2011-05-03
So I recently tried doing a project in Kdenlive. I got a few hours in to it but I am stopping as of right now.

It's not the instability I mind... the stuff that makes it crash is fairly predictable and it's a really, really nice video editor otherwise.

No, what sealed its fate is that if you save your project and re-open it, the video clips are no longer in EXACTLY the same place as you left them. In other words, if you are doing any kind of audio syncing, you are going to go freaking mad.

Am I the only one seeing this? I read on their forum that if you lock all the tracks before you save and quit, you don't get this problem. Unfortunately A) Kdenlive isn't terribly stable so I save a lot. Having to lock and unlock tracks constantly is a pain, and B) I might forget.

Can anyone suggest a video editor with really, really good timeline editing (as in, NOT Kino) so I can do nice, intricate audio sync things? I liked Kdenlive because it showed audio waveform for everything as well as the first and last frame of any video clips on the timeline. But mainly, the video program has to actually be able to keep clips in the right @#$% places!!! *ahem* sorry.... a little frustrated.

I really hope this issue gets fixed for version .8 as I really, really like using Kdenlive. Unfortunately it doesn't matter how nice it is to use because this bug makes it completely useless to me. *mutter mutter*

Oh, and for the record I am using DV video files created with ffmpeg.

ok rant over

---

### Post by decoherence on 2011-05-19
Well, after trying various other video editing tools, I've found nothing that matches kdenlive in terms of feature set and usability. So after pondering for a while I hit myself on the head for what must've been the lamest, noobiest mistake ever -- and I once did video editing for a living!

So I had a custom rubber stamp made and I have applied it with great force to my forehead. The stamp reads "MPEG IS NOT FOR EDITING!!!" The motion compensation techniques used modern codecs plays havoc with anything that requires accurate time. Solution? Convert to good old MJPEG! Problem solved!

In my own defence, I was doing video editing before MPEG 1 was on the scene... but still, I knew this and totally forgot! D'oh!

The command to convert to MJPEG is like so

```
ffmpeg -i <input_file> -vcodec mjpeg -qscale 1 -an output.avi 
```

I hope this saves someone some frustration! I am now firmly on the 'i love kdenlive' side of the fence!

---

### Post by zettberlin on 2011-05-20
Good to know that issue with DV-files. 

I never did notice it because I use to do the serious audio-stuff with Ardour synched to Open Movie Editor playing a video already edited.

BTW: 0.8 of KDEnlive features a proxy-mode. You can order to transcode any imported clip to a format that is optimized for editing. In the end the cutting-orders in the project are applied to the original files to render the desired output.

---

