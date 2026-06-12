---
title: "SMPlayer Mouse &amp; Keyboard Controls Not Working?"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by martynp on 2007-11-30
Hi All,

I have always used Totem, However, to be able to use a couple of specific things I need mplayer installed. I have done this on a fresh install along with SMplayer.

Everything works just fine in video and sound quality. However, I just can't get the keyboard and mouse shortcuts to work in both norma and full screen. Yes, i can space to pause, 9 or 0 for volume etc but I cannot use the keyboard to skip forwards or backwards. Neither can i do so with mouse.

I have used this program before and am familiar with how to set it up and I have all the right boxes ticked. Even the skip etc buttons don't work in the actual smplayer window.

Does anyone have any ideas why?

Many, many thanks in advance

---

### Post by rvm4000 on 2007-11-30
If that problem only happens with the seeking actions (and not with the rest, like adjusting the volume) maybe it's because the file you're playing doesn't allow seeking (maybe a broken index), take a look at the mplayer log to see if it complains about that.

In that case you can check the option "Create index if needed" in preferences->performance.

---

