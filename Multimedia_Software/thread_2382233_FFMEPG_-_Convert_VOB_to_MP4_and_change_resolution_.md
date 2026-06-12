---
title: "FFMEPG - Convert VOB to MP4 and change resolution - Playback looks squashed"
date: 2018-01-10
forum: Multimedia Software
---

### Post by Alan5127 on 2018-01-10
Hi All,

I am using ffmpeg to convert an old VOB video file to MP4 on Ubuntu 16.04.2 LTS.

The VOB is in 'good order' and plays fine on my Ubuntu machine, but I want to play it on devices that won't play VOB, so converting to MP4.

The original VOB is 18mins, and 720 x 576 at 25 fps with a bitrate of 1773 kbps according to a right-click - properties.

When I play it from Ubuntu, using the default video player (I think it might be called 'Totem Movie Player' but it is whatever comes with a plain vanilla install of 16.04 LTS) it plays fine, and it is 'full screen' (16 x 9 which is the same ratio as 1280 x 720) with small black strips down the sides, presumably since 576 x 16 / 9 = 1024 which is more than 720 so it fits vertically, and centres horizontally.

I am using this command to convert it to MP4 and change the resolution:

```
ffmpeg -i input.vob -filter:v scale=1280:720 -c:a copy output1.mp4
```

I want to change the resolution so I can string this video file together with another, which is 1280 x 720.

This 'works', but the file I get (output1.mp4) is:

1280 x 720 at 25 fps, but with a bitrate of 181 kbps (according to right-click, properties).

However, if I play that output1.mp4 in the default player, and then select Movie - Properties from the video player menu, the bit rate it shows is always around 1,000 to 1,110 kbps.

Also, the output1.mp4 now plays 'squashed up' into the centre of the screen with much larger black bands down the left and right - the video is also clearly 'squashed' with the scenes being vertically elongated.  In the video player, if I click View - Aspect Ratio - 16x9 it then looks the same as before (for the VOB) and appears normal.  If I go back to View - Aspect Ratio - Auto, it is squashed again.


Questions:

1) Have I done something silly with the ffmpeg command above?  Should I use different options?

2) Is the output1.mp4 really around 181 kbps or 1,000 kbps?  Why would the figures differ?

3) Why does the 'auto' view option leave the output1.mp4 'squashed'?


If I have failed to provide any pertinent information, please do ask.

Thanks,

Alan.

---

### Post by mc4man on 2018-01-10
Don't have any vobs lying around but what happens if you change that to 
```
scale=1280:-2
```
or -1 if results happen to be divisible by 2

---

### Post by Alan5127 on 2018-01-10
Hi Mc4Man,

Thank you for assisting me.

> **mc4man said:**
> Don't have any vobs lying around but what happens if you change that to 
```
scale=1280:-2
```
or -1 if results happen to be divisible by 2

I ran both of these:

```

ffmpeg -i input.vob -filter:v scale=1280:-1 -c:a copy output2.mp4
ffmpeg -i input.vob -filter:v scale=1280:-2 -c:a copy output2.mp4
```

In both cases, I get an output2.mp4 with:

1280 x 1024 at 25 fps, but with a bitrate of 195 kbps (according to right-click, properties). 

If I play that output2.mp4, it shows a bitrate fluctuating around 1,000 to 1,100 kpbs (same as previously).

It (output2.mp4) also plays 'squashed' with the aspect ration set to 'auto'.



Alan.

---

