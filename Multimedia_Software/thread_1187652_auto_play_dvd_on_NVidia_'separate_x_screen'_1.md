---
title: "auto play dvd on NVidia 'separate x screen' 1"
date: 2009-06-14
forum: Multimedia Software
---

### Post by juanoleso on 2009-06-14
I have an NVidia card which I use to display another x screen on a tv.  I would like to be able to pop a dvd in the drive and have a media player start and play the dvd fullscreen on the other screen.  The screen is labeled 1 under the Nvidia control panel and I am using GNOME.  Any links or additional information would be great and I prefer VLC, but any media player would do.

thanks.

---

### Post by juanoleso on 2009-06-25
Bump,

Is this even possible?  Any external links would be great or any reading...

I'm using the NVidia drivers provided from their site.  The card is a 5700LE and I am running Debian Lenny.  I have no trouble getting VLC up on the other screen, I'm just looking to have it all done automatically.

How about, is there a way to run some kind of debug while GNOME is running to see the commands it uses to display vlc on the other screen?  (of course, I might not even know what I'm talking about...  ^_^)

I tried setting the TV as screen 0 but as soon as I log out and log back in it is set automatically back to screen 1.

Thanks in advance

---

### Post by Chronon on 2009-06-25
This post might be helpful to you. 

[http://ubuntuforums.org/showpost.php?p=7457014&postcount=2](http://ubuntuforums.org/showpost.php?p=7457014&postcount=2)

[http://ubuntuforums.org/showthread.php?t=929188&highlight=Autorun+dvd](http://ubuntuforums.org/showthread.php?t=929188&highlight=Autorun+dvd)

---

### Post by juanoleso on 2009-06-25
Perfect,

thank you.

---

### Post by juanoleso on 2009-06-25
For anybody that finds this post, I went to system -> preferences -> Removable Drives and Media.  I did the multimedia tab and I checked Play video DVD discs when inserted. The command I put in was
```

env DISPLAY=:0.1 vlc dvd:///media/cdrom -f

```

which autoplays the DVD on screen 1 and then sets it to fullscreen.

---

