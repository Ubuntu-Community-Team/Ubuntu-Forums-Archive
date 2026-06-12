---
title: "Video only plays when my screens are aligned vertically."
date: 2011-07-16
forum: Multimedia Software
---

### Post by kevinlyfellow on 2011-07-16
I using 10.04 lucid lynx with a tv screen using svideo.  My graphics card is an intel 945gm.  As the title says, video will only play when the screens are aligned vertically.  I find this behavior very unusual.  This problem happens with totem (gstreamer), mplayer, and xine so its not a problem specific with a video player.  Does anyone have some insight on how to resolve this issue?

Thanks

---

### Post by tgalati4 on 2011-07-16
On board video chips have limited capability.  It's possible that you need to align the displays in order to use a common refresh rate between both.

In addition, the S-Video is an analog output, so the digital resolution has to go through a digital-to-analog converter, which further limits it's output capability.

Finally, S-Video was really designed to display single-screen only.  Since it only puts out ~640 by 480 (standard VGA), it's not really useful for day-to-day use.  Perhaps playing a vacation slide show on the big screen TV, but that's about it.

---

### Post by kevinlyfellow on 2011-07-17
Thanks for the reply.

I have used the svideo in the past for the purpose I spedified, so its not a weird hardware limitation.  I'm also not trying to use this as an everyday display, just wanna watch ted talks on a larger screen, so the low res doesn't bother me.  Video looks pretty good to me, but I'm not one for movies.  I have actually done this before with my current install of Ubuntu, so either I did something to screw it up, an update screwed it up, or something changed in the way ubuntu is configuring xorg.  That said, I doubt I screwed something up, since I can't even find xorg.conf anymore.  I'm not sure why vertical alignment of the screens (tv needs to be above or below my laptop monitor in the configuration) but video does not play when they are set up horizontally.  Note that everything else works fine.  Does anyone know how ubuntu is configuring this these days?  Again, I can't find xorg.conf, so I don't know where to look to begin to figure out the problem.

---

