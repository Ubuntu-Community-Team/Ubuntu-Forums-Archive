---
title: "tv recording?"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by Robocoastie on 2007-11-10
Is there a program I can use to record TV programs with my PVR-150 card other than mythtv?
The reason I ask is that I've learned through help here and trial and error that Compiz and mythtv don't mix. Not only will live tv video not show or even playing videos in mythtv not work but it won't even record correctly as long as compiz is running.

I actually like compiz because its fast app switchability I actually find useful for my work so I've come to find compiz to be more than eye candy but actually a killer app.

If there isn't any no biggie either, I have another box I could add a bigger hard drive to and make it a mythbuntu only box rather than a frontend only like it was originally planned but thought I'd check first.

thanks,

Rob

---

### Post by reckless2k2 on 2007-11-10
you can supposedly do it with mplayer. i saw something not too long ago about this. try a google search but other than mythtv that's about it.

---

### Post by JBAlaska on 2007-11-10
SageTV for Linux, although I have not tried it.

---

### Post by rsambuca on 2007-11-10
VLC will work, as will the command line.

---

### Post by Robocoastie on 2007-11-11
SageTV I'd try IF they had a trial version for Linux but they don't and there's no support from them since it's OEM and no money back guarentee, so if I purchased it and it turns out I have the same problem with it as I do mythTV I'm out $100.

I've been able to get VLC to work but I haven't figured out how to change channels or record, much less schedule recordings (that part might not be possible). I've dug through the VLC manuals to no avail, any hints how to change channels and/or record?

thanks!

Rob

---

### Post by rsambuca on 2007-11-11
You have to change channels via the command line.  Some people have found a gui for it, but I never bothered.  If you are using the coax input, then you can change the channel using the command:  v4l2-ctl -c #
where the '#' is the channel you want.  You will have to install 'ivtv-utils' first.

---

### Post by Robocoastie on 2007-11-12
thanks.

---

