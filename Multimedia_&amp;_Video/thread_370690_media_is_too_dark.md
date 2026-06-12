---
title: "media is too dark"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by krelverehan on 2007-02-26
I have this problem right now.

It seems that all my pictures and videos I play are too dark. Everything else seems to be at the normal brightness.

I have found that I can make the pictures a normal brightness (and make everything too bright) by entering in the terminal: 

[FONT="Courier New"]
xgamma -gamma 3[/FONT]

Although the videos are always too dark. I have all the levels on my monitor on full, also.

Thanks,
-KV

---

### Post by chewearn on 2007-02-26
What media player are you using?  I am using VLC, where you can adjust the video color, brightness, etc in the player's preferences.

---

### Post by krelverehan on 2007-02-26
I use VLC (V 0.8.6)...


It is weird. The default setting in the options make the gamma and the brightness set both to 1. No matter what I change the numbers to the brightness nor the gamma on the video never changes. Even after restarting the application.

I am trying to do this through:

Settings > Preferences > Filters > Image adjust.

Every media player I have tried is too dark. Maybe my video card is not installed right?

---

### Post by chewearn on 2007-02-26
VLC can be non-intuitive to use.
First you need to enable the image adjust filter in the video post processing chain.

Select on "Filters" (first line).  You will see the view as shown in attached.  Select the "Images properties filter" checkbox; the text "adjust" will appear in the textbox below the list.

Now, the changes you make in the "Image adjust" page should work.

---

### Post by krelverehan on 2007-02-26
You are the man...

Thanks, I can see!

---

