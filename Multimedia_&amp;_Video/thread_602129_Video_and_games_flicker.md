---
title: "Video and games flicker"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by czeckk on 2007-11-03
When i open up a 3d game or try and watch a video file, the video file or game flickers

I am running Ubuntu Gutsy Gibbon with
ati radeon x1300 (ati driver installed)

I have compiz fusion working, which in case you didn't know seems to be quite a task with my video card, and when i type in glx info it says that dri is enabled.

I had my system set up earlier where it could do compiz and play videos but couldnt play 3d games, i was told i needed the ati driver installed in order to play games. I did a fresh install of ubuntu on my system and folowed the instructions from the unnoficial ati wiki driver site (method 2)

If anyone can help...PLEASE DO!!!!! i dont understand why my card is so under-supported by ubuntu...

Thanx in advance

---

### Post by markusf21 on 2007-11-04
First it's ATI not supporting Ubuntu not the other way around. But try turning Compiz off and then run the video

---

### Post by dulbirakan on 2007-11-04
I have the same problem, any other suggestions?

---

### Post by ograndedienne on 2007-11-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/157580](https://bugs.launchpad.net/ubuntu/+bug/157580) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,
i've the same problem but partially solved.
Unfortunately this is a known bug: [https://bugs.launchpad.net/ubuntu/+bug/157580](https://bugs.launchpad.net/ubuntu/+bug/157580)

To be able to play videos with totem,  you have to run
**gstreamer-properties** go to the **Video** section and select
**X Windows System (without Xv)**
as plugin. 
This change burns lot of computing power when you play video in totem, but it works for the video files.***It doesn't work for DVD*** because totem can't play dvd (exept if you use totem-xine, that's using xine backend!).

Now i'm looking for "*correct*" video driver selection in Xine (xine-ui package) that plays video without flickering. :(
Worst: VLC just doesn't have driver selection!

And for opengl games...don't know! 

My 2 euro cent.

Valerio

---

### Post by ograndedienne on 2007-11-04
> **markusf21 said:**
> First it's ATI not supporting Ubuntu not the other way around. But try turning Compiz off and then run the video

without 3d effects enabled, he shoud be able to play videos correctly. 
A drawback is that when you re-enable compiz, it resets 3d effects configuration. :(

So i don't want to disable 3d Effects.... 

Valerio aka O( n )

---

### Post by czeckk on 2007-11-04
That did it!
thank you markus, all i did was turn off compiz and played the video,and a game, smoothly.

if anyone knows how to fix it without turning off compiz that would also be great...just as a luxury...

Thank you!

---

### Post by ograndedienne on 2007-11-04
To play dvd with 3D effects and compiz enabled:


1) install xine-ui (and all dvd  related libraries...)

2) run xine

3) go to the settings

4) gui -> experience level -> master of the known universe

5) video -> driver video -> opengl

6) apply and close xine.

7) run xine and play dvd at the full screen. click to the screen.


O( n )

---

### Post by markusf21 on 2007-11-04
No problem glad to help I just wish I knew a better way

---

