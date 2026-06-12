---
title: "Can I rip a widescreen DVD to fullscreen?"
date: 2011-09-13
forum: Multimedia Software
---

### Post by RKCole on 2011-09-13
Hello, everyone.

I will first state that my knowledge of video terminology and conversion techniques is minimal at best.

I recently purchased some movies, and they were only available in widescreen. I have an older CRT standard definition TV which has (at least) a 36-inch screen, so it is quite inconvenient for me to watch widescreen movies on this TV. I would purchase a newer TV, but that is not quite a priority in my budget right now.

For the past day or two I have tried ripping the DVD in HandBrake, adjusting the aspect ration scale to 640x480 (4:3), but this seems to be too zoomed in.

I have also tried ripping the DVD normally with AcidRip and then converting it to the Xvid Fullscreen format in WinFF, but for some reason the movie is still widescreen.

I am at a loss as to what to do, and I would be very grateful for input from experienced users concerning this issue.

Thanks for any input which you can give concerning this situation.

Take care.

---

### Post by 4Orbs on 2011-09-13
I tried to solve the same problem a few years ago with my old crt monitor. You can arrive at a somewhat satisfactory solution with some trial-and-error experimentation. The easiest way is to crop the image an equal or almost-equal amount of pixels from the left and right side of the image. This will have the effect of zooming in the picture and the black bars at top/bottom will become smaller as the picture fills a larger vertical space (depending on how many pixels you remove from the width). But you will always have those black bars to some degree.

Keep the image at 16:9, and start by removing 24 pixels from both sides. It is important to keep the percentage of distortion at somewhere between -2% to 2% or the image will be squashed or stretched too much. In order to crop the images in Handbrake, you'll need to uncheck the "Strict" option first. Sorry for my lack of correct terminology, I'm not a pro... but I have dealt with the same situation as yours.

Also, it's probably better to experiment on just a single small vob file so you can see the results without waiting too long.

Hopefully, somebody with more experience will come along and offer a better solution. You might want to wait awhile before attempting my suggestion.

---

### Post by MartyBuntu on 2011-09-13
You can't change the aspect ratio from 16:9 to 4:3 without distorting the source content.

It is what it is.

---

### Post by RKCole on 2011-09-14
Thanks for the replies.

MartyBuntu, thanks for clearing that up for me. I just did a bit of research so that I could understand the differences between letterbox, widescreen, and fullscreen. I found a pretty good answer to this [here]("http://askville.amazon.com/difference-widescreen-full-screen-blue-dvds/AnswerViewer.do?requestId=5456744").

So now I understand that widescreen is sued so that viewers basically see what the audience saw when the movie was in the theater, as it shows a more broad picture than does fullscreen. I also understand that ripping a movie to fullscreen will distort that "full view" which is given by the widescreen edition.

With what limited vision I have I am able to enjoy movies, but when they are in widescreen format my eyes focus on the black boxes above and below the picture, thus I end up missing everything that is going on. This is my main reason for converting to fullscreen (at least until I can get a newer TV).

I have come across [THIS PAGE]("http://quadpoint.org/projects/simplerip") which has helped me a bit more in understanding how to convert videos and rip DVDs using mplayer/mencoder. The video rips and plays in fullscreen, but there is no sound.

I am getting close, though.

Thanks again for the replies, 4Orbs and MartyBuntu. I have definitely learned a LOT thus far, and I am gaining a much greater appreciation for my terminal. :)

Take care.

---

### Post by Grenage on 2011-09-14
> **RKCole said:**
> Thanks for the replies.

MartyBuntu, thanks for clearing that up for me. I just did a bit of research so that I could understand the differences between letterbox, widescreen, and fullscreen. I found a pretty good answer to this [here]("http://askville.amazon.com/difference-widescreen-full-screen-blue-dvds/AnswerViewer.do?requestId=5456744").

So now I understand that widescreen is sued so that viewers basically see what the audience saw when the movie was in the theater, as it shows a more broad picture than does fullscreen. I also understand that ripping a movie to fullscreen will distort that "full view" which is given by the widescreen edition.

With what limited vision I have I am able to enjoy movies, but when they are in widescreen format my eyes focus on the black boxes above and below the picture, thus I end up missing everything that is going on. This is my main reason for converting to fullscreen (at least until I can get a newer TV).

I have come across [THIS PAGE]("http://quadpoint.org/projects/simplerip") which has helped me a bit more in understanding how to convert videos and rip DVDs using mplayer/mencoder. The video rips and plays in fullscreen, but there is no sound.

I am getting close, though.

Thanks again for the replies, 4Orbs and MartyBuntu. I have definitely learned a LOT thus far, and I am gaining a much greater appreciation for my terminal. :)

Take care.

Well, it's not really 'full screen', as you're getting less of the image. ;)  As stated, there is no way to do what you ask, without either cropping or distorting (shudder) the feed.  Black bars are aren't that bad, once you get used to them;  widescreen viewers have to put up with bars on the sides for old 4:3, and that always seems so much worse.

---

