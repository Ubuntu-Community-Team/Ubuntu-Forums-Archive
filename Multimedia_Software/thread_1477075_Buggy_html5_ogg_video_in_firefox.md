---
title: "Buggy html5 ogg video in firefox"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Ylon on 2010-05-08
This problem is driving me mad: the video load and the buffer go on but the video won't play. This happen mostly always. I am the only one with this problem?

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3
```


site example: [http://tinyvid.tv/](http://tinyvid.tv/)

---

### Post by WinterRain on 2010-05-08
Those vids work for me. I use the gecko-mediaplayer plugin.

---

### Post by Ylon on 2010-05-09
> **WinterRain said:**
> Those vids work for me. I use the gecko-mediaplayer plugin.
I've installed the codec.. but looks like it's the same thing.
Maybe I had to turn of the internal codec in order to see them? How can I do?

---

### Post by spaceshipguy on 2010-09-07
I have the same problem. I know my machine has the codec because it will make an ogg or ogv file, but it won't play a file it streams off the internet. Downloads it OK (according to the status bar) then plays three frames and blip of audio before hanging. Even the ogg file on the Wikipedia page about ogg won't play.

---

### Post by lovinglinux on 2010-09-07
> **WinterRain said:**
> Those vids work for me. I use the gecko-mediaplayer plugin.

The gecko-mediaplayer plugin is not used to play those videos. In fact, no plugin is used at all. That is html5 video, which means there is no need to use any plugin, the video is rendered by the browser itself.

Try to create a new Firefox profile, just to see if it works. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by no2498 on 2010-09-07
right down your settings so if needed you can set them back



&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

