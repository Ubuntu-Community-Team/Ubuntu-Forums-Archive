---
title: "ffmpeg presets - bitrates?"
date: 2012-12-14
forum: Multimedia Software
---

### Post by dannyboy79 on 2012-12-14
I am trying to stream to twitch.tv using the following ffmpeg command [http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html](http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html)
and the ffmpeg preset is quality "medium". How can I find out what the bitrate is for that preset? Can someone please post all the libx264 presets and their settings for each preset. I can't find them anywhere. Thanks!

---

### Post by evilsoup on 2012-12-14
It's more complicated than that, unfortunately. You might find [this]("https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide") useful.

EDIT: OK, I just did some tests, and with a CRF of 23 (which is the default), a music video of mine came out at (video bitrates as reported by avconv):

ultrafast - 4568 kb/s
superfast - 4551 kb/s
veryfast - 2253 kb/s
faster - 2188 kb/s
fast - 2289 kb/s
medium - 2267 kb/s

These are obviously just broad guidelines, depending on the particulars of the video you'll get different results. I didn't test slow, slower or veryslow (my computer struggles to get a reasonable time with medium), but they're probably not relevant to your purposes. The big dropoff in terms of bitrate seems to be at veryfast, so I'd probably recommend using that. I'm not sure why faster has less of a bitrate than fast or medium, I'd have to test out on more videos to see if that's a bug in x264 or some quirk of the particular video I tested it on.

Other ways of lowering the bitrate would be: to use a higher CRF(=lower quality); the default crf for ffmpeg is 23, and an increase in 6 should approximately half the bitrate, adding -crf 29 would do that in your script (don't go any higher than that though, or the quality will be too horrible to watch); or reduce the output frame size (though I see that script does that already); or reduce the frame rate (may not be acceptable for you; IIRC, the ABSOLUTE MINIMUM framerate needed for the human eye to see a smooth image is around 15 or 16 frames per second, but it won't look the best).

---

### Post by dannyboy79 on 2012-12-14
> **evilsoup said:**
> It's more complicated than that, unfortunately. You might find [this](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) useful.
well, I am using a script I found here: [http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html](http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html)
that has a preset of medium. So somewhere some file on my system has to contain all the settings for libx264 medium right?

---

### Post by evilsoup on 2012-12-14
Oh dang, I edited in a bunch of new information without noticing that you'd added another post.

[Here](http://pastebin.com/fuL1BC31) is a version of the script from that blog, edited for a lower bitrate, and also to include the -crf flag.

I would definitely *strongly* recommend reading the ffmpeg/x264 guide I linked in my first post, since there are other approaches that I haven't gone into that you may find useful.

---

### Post by dannyboy79 on 2012-12-14
> **evilsoup said:**
> Oh dang, I edited in a bunch of new information without noticing that you'd added another post.

[Here](http://pastebin.com/fuL1BC31) is a version of the script from that blog, edited for a lower bitrate, and also to include the -crf flag.

I would definitely *strongly* recommend reading the ffmpeg/x264 guide I linked in my first post, since there are other approaches that I haven't gone into that you may find useful.
see the problem I have is that my upload from my ISP is only .5mb. I was told to try to stream 240p and around a 350 bitrate max @ 30 FPS. how would I achieve those settings using the presets and or crf. Any more help would be much appreicated. I did read that whole page but its sinking in only very slowly. LOL

---

### Post by evilsoup on 2012-12-14
Yeah, the page is kind of complicated, and not really focused on what you want to do - though there is useful information there.

You can change the output resolution in that script - just change the line
```
OUTRES="852x480"
```
to
```
OUTRES="426x240"
```
This will give you 240p video. You can set a maximum bitrate with -maxrate; for a max rate of 350kb/s, use
```
-maxrate 350k
```
You would probably be well served setting a lower framerate, again I would recommend about 16 fps. Less frames = more bits can be spent per frame by the encoder; so you'd get somewhat better image quality per frame (though we're still not talking miracles here), while running the risk of having stuttering video, especially during any high-speed action.

Of course, all of this will give you pretty bad quality, but that's the tradeoff you'll have to make.

---

### Post by dannyboy79 on 2012-12-14
> **evilsoup said:**
> Yeah, the page is kind of complicated, and not really focused on what you want to do - though there is useful information there.

You can change the output resolution in that script - just change the line
```
OUTRES="852x480"
```
to
```
OUTRES="426x240"
```
This will give you 240p video. You can set a maximum bitrate with -maxrate; for a max rate of 350kb/s, use
```
-maxrate 350k
```
You would probably be well served setting a lower framerate, again I would recommend about 16 fps. Less frames = more bits can be spent per frame by the encoder; so you'd get somewhat better image quality per frame (though we're still not talking miracles here), while running the risk of having stuttering video, especially during any high-speed action.

Of course, all of this will give you pretty bad quality, but that's the tradeoff you'll have to make.is 426x240p a 16:9 resolution? How do I figure that out? THanks again for all your help. I know with only .5mb upload I won't have the best looking stream, just don't want it to be all laggy. Hell, maybe I won't even be able to stream the game.

---

### Post by andrew.46 on 2012-12-14
> **dannyboy79 said:**
> So somewhere some file on my system has to contain all the settings for libx264 medium right?

If you are using the FFmpeg fork have a look in */usr/share/avconv/* . But I believe these are mapped to x264 presets...

---

### Post by evilsoup on 2012-12-14
To tell if a screen resolution is 16:9, simply divide the vertical by the horizontal, and if the result is 1.777... then the resolution is 16:9.

426/240=1.775, close enough for government work. I got that originally by halving the resolution stated in that script.

I don't think you'll find the x264 presets very enlightening, they are just a collection of fairly obscure options for ffmpeg to send to x264. Really, the only way to find out if all this will work is to try it out.

If you want to set the maxrate within that script, put '-maxrate 350k' (without the quotes) on the end of the line that starts with '-vcodec libx264', but before the '\'.

---

