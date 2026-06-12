---
title: "Interlace-related problems transcoding to MPEG4"
date: 2008-10-01
forum: Mythbuntu
---

### Post by zoiks on 2008-10-01
I am using mythbuntu 8.10-fixes.

My inputs are 2x HDTV using HDHomeRun, and 2x SDTV using Hauppauge PVR 500. TV is Sharp Aquos LC-52D64U.

Whenever I transcode high definition (in particular 1080i) video to MPEG4, I get some nasty motion effects that make the video hard to watch. Untranscoded video from the HDHomeRun device looks terrific. I have set the transcoding to:

[LIST]
[*]Bitrate=2000 kbps (but *scaled* from 640x480 so should be closer to 13000kbps for 1080i, from an untranscoded 18000kbps)
[*]Max/min quality = 2/15 (defaults), quality difference = 3 (default)
[*]Scale bitrate for frame size = On
[*]Enable high-quality encoding = On
[*]Enable 4MV encoding = On
[*]Enable interlaced DCT encoding = Off (*)
[*]Enable interlaced motion estimation = Off (*)
[/LIST]

(I've tried the transcoding with the last two settings both on and off).

The problem is when HD video is transcoded, scenes with motion in them make me dizzy. It's an effect somewhere between a double image moving across the screen to a high-frequency jerking back and forth of the image that's moving, like perhaps the odd/even fields get transposed. When you look at the video before the transcoding and after the transcoding, the difference is very remarkable.

What kinds of things should I be trying to make this better? I'm not sure where to even start.

Or, is this just something you have to put up with when using MPEG4?

Or, would RTJPEG produce better results?

My goal is to be able to transcode down these massive HDTV programs, to somewhere between 50% and 75% of the original size.

Thank you!

---

### Post by zoiks on 2008-10-02
Nothing?

How about this, has anybody been able to encode their HD video (from HDHomeRun, for example) to MPEG4 and have it look nearly as nice as the original, even with motion scenes?

TIA

---

### Post by laga on 2008-10-02
You could try specifying a deinterlacing filter for transcoding. The MythTV wiki should have some documentation about that.

---

### Post by dodle on 2008-10-02
I've never worked with 1080 resolution before, but I have learned to always deinterlace my videos before I start doing anything with them.  Avidemux works well and has the best free deinterlace filters that I have seen.

BTW, the term "HD" has always bothered me.  It shouldn't, but it does.  "HD" is a marketing term:  "This is the new *HD* tv!"  Why can't they just say "This television has a resolution of 1080x(whatever the second number is)"?  Yeah, I already know the answer -- money.  People hear "High Definition" and somewhere in their mind they think 'Whoa! It's High Definition, that's waaaay better than that old tv stuff (whatever it's called)'.  Then they've got to have it.  If somebody told them it was just a higher resolution they might think 'hmmmm, I guess I'm already satisfied with the resolution that I am getting', and maybe not.  Don't get me wrong, I think HD is cool, I just find marketing techniques annoying.  "It's the new glycemic advantage!!!!"  What the heck is "glycemic advantage" anyway?

Edit: Sorry to rant, I just had to get that out.

---

### Post by anonymousdog on 2008-10-02
I'd be shocked if you could achieve that level of compression without noticeable loss of quality and, probably, introduction of visual artifacts.

---

### Post by zoiks on 2008-10-03
Thanks for the suggestion to use the transcode filter.

So far, I've tried using "bobdeint" in the "filter" box of the transcoder settings. I then had it transcode some 1080i content, and in fact the double-image artifact (while something moves across the screen) was still there, after transcoding. I tried using bobdeint because I was under the impression it's the best deinterlacing method.

Does bobdeint work as a transcoder filter? Do I need to set bobdeint=<value> or something to that effect? The wiki and other documents don't say much about this.

Meanwhile, I'm going to try using kerneldeint=12:0, and see if that helps. I'll report back after a transcode (the transcodes take hours).

As far as suffering significant video quality issues, I'm not expecting it. I'm only going to reduce the file size by 25-50%, and with my (limited) experience MPEG4 is capable of around that much reduction without significantly hurting the video quality.

---

### Post by zoiks on 2008-10-04
Eh.

Putting "kerneldeint=12:0" as a filter in the transcoder (which, FWIW is "autodetect from MPEG2") didn't work. I still get double-images in motion scenes.

Some additional information: my display is a Sharp 1080p display. In normal TV viewing, I use bob deinterlacing (2x). Watching untranscoded 1080i recordings with this configuration looks pretty sharp. It's only when I transcode to MPEG4 that I get the double-images.

Any other suggestions?

---

