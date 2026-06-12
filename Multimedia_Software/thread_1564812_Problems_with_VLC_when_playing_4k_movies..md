---
title: "Problems with VLC when playing 4k movies."
date: 2010-08-31
forum: Multimedia Software
---

### Post by sirbender on 2010-08-31
When I start a 4k movie in VLC it tells me: 

Your video output acceleration driver does not support the required resolution: 4096x1706 pixels. The maximum supported resolution is 2048x1706.
Video output acceleration will be disabled. However, rendering videos with overly large resolution may cause severe performance degration.


Can I somehow fix this? Maybe increase my output resolution somehow?

I downloaded 4k movies from here: [http://www.youtube.com/view_play_list?p=5bf9e09ecec8f88f](http://www.youtube.com/view_play_list?p=5bf9e09ecec8f88f)

Thanks,
sb

---

### Post by cchhrriiss121212 on 2010-08-31
As the message says, it is down to your video driver, so what card are you using and what driver are you running?

---

### Post by sirbender on 2010-08-31
I have a Thinkpad T510 with the rather new Intel HD Graphics.

---

### Post by cchhrriiss121212 on 2010-08-31
Integrated graphics will not be able to cope with that ([http://software.intel.com/en-us/articles/quick-reference-guide-to-intel-integrated-graphics/]("http://software.intel.com/en-us/articles/quick-reference-guide-to-intel-integrated-graphics/")source), so you should stick to lower res videos.

---

### Post by sirbender on 2010-08-31
Where do you read at the link that there is any such restiction?

There is a cap on output resolution of 2560x1600. This is however a limitation of the attached display.

I am talking solely about VLC and should be no problem as long as the graphics chip has control over enough RAM. Which it has.

---

### Post by cchhrriiss121212 on 2010-09-01
As far as I can see the link says "Maximum Dsiplay Resolution" and for your chip it does state 2560x1600. As far as I know that refers to a limit on what video you can render in addition to what display size you can output. The link also says it supports 720p, 1080i and 1080p and makes no mention of anything higher. If this chip supported 4k I think they would be very vocal about it. 
Ability to play demanding video will require a powerful cpu and gpu, so having enough RAM will not help you out here.
If you would like to carry on trying to play this video, then have a look at xine or mplayer and maybe they will give you a different error message.

---

### Post by sirbender on 2010-09-01
Nope. I played that 4k clips without problems on other players then VLC.

The problem is VLC or my hardware drivers.

---

