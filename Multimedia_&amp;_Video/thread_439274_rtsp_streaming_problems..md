---
title: "rtsp streaming problems."
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by SandroG on 2007-05-10
I am having problems playing rtsp video streams from news.bbc.co.uk.

Totem-xine would bring up an error window, both within firefox and with the external player, saying that "There is no input plugin to handle the location of this movie" .

Similar situation with mplayer and in konqueror with kmplayer.

As for VLC, the mozilla-plugin-vlc will show just (No Video)   :???: and yet
The external VLC player will play the image, but with choppy scratchy sound constantly interrupted... 

Now this is the interesting bit:
If on vlc I move back the progress handle for the video several times, sometimes, not always, I would fix the sound. But there'll be many times I'll never be able to hear the sound in a way that is at least bearable, which is nearly as good as seeing nothing at all.

Has anybody had any similar problems to mine?
Is there some way of watching all my bbc videos on Linux?

Thanks in advance for any comments,

Sandro

---

### Post by charlysbrother on 2007-05-28
I have exactly the same problems. Are you using 64bit ubuntu also?

---

### Post by MxGB on 2007-06-10
Same problems here. Running feisty 32bit with mplayer, xine, totem and w32codecs and every gstreamer-related package going.

---

### Post by charlysbrother on 2007-06-13
I was able to view bbc streams using the mplayer plugin from automatix. This was with 'real media' chosen in the preferences for the bbc.

---

### Post by jonqrandom on 2007-06-27
ugly kludge:  copy the url of the file from the error message, paste it into totem's "Open Location" dialog, and replace "rtsp" with "http". can't garauntee this will work all the time, but it proves totem can at least *play* the damned files :/

---

### Post by andrew.46 on 2007-09-10
Hi,

 All you need is the exact address of the .ram file which you will see when you select 'use external viewer' and paste the .ram address into mplayer:

```
mplayer -playlist url.ram
```

 A pity that such sites would not simply post the raw address of their files *as well as* setting it up to run in a browser.

                 Andrew

---

