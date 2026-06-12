---
title: "Codecs question"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by Gouz on 2007-08-15
Greetings all, I am kinda new in linux/ubuntu and this is my first post in this forum....
I have a question... when I was using windows, i used media player classic... and the CCCP (codec package) to be able to watch anime.. in ubuntu I don't know any good music/video player and I don't know what kind of codex I will for the anime (.avi , .ogg , .mkv formats)

Any help on where to find the codex/player and how to install them welcomed.

Gouz


PS I have tried to use the codex that can be find in the add/remove options from the GNOME (because I dont know the commands to do it from the terminal)

---

### Post by Bachstelze on 2007-08-15
Post moved to a new thread in the Multimedia & Video section.

All you need is [here](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by Gouz on 2007-08-15
Hi once again

 
I have done everything that was posted in the link that you posted, thought termina and thought add/remove, as well with other Mplayers.. but...
my main problem remain.. when I run full screen application I have no image, and even when run on window size i still dont have any image, I have to move a bit the window so the image is shown and if I want full screen I have to minimize and maximize couple of time (using the F11).


Gouz

---

### Post by RomeReactor on 2007-08-15
Hi. Are you using Desktop Effects (Compiz) or Beryl? if so, try this: open Mplayer, right-click on it and select "Preferences->Video" and change the driver; try with **x11  X11(XImage/Shm)** first and see if it works now. If not, try with the other drivers there.

Once you get it working and have the necessary plugins, you'll see that Mplayer is great for anime, as it doesn't stutter with mkv files as Totem does. It plays practically every format flawlessly, in my opinion.

---

### Post by Gouz on 2007-08-15
I don't use desktop effects, and I just notice that a white spot appear in the down left corner of the screen.
And now I cant even open any anime with the Mplayer :( I think I did something wrong..
The message I got now it :

 Error opening/initializing the selected video_out (-vo) device.

---

### Post by chewearn on 2007-08-15
Not sure if this will solve your problem, because it appears that you might have a video driver issue, rather than the media playback software itself.

But I almost always have less problem playing back a video file using vlc player.  You can install this by synaptic, or simply type the following in the terminal:
```
sudo aptitude install vlc
```

---

### Post by Gouz on 2007-08-15
vlc runs normaly but, one of the videos has sound problems... :(
And still when I open the video i hear the sound but no image until I move the window a bit, and in full screen I have to press F11 several times

---

### Post by Gremlinzzz on 2007-08-15
Like mama says the Book is always Better
here's the book forest gump
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Bablefish on 2007-08-15
Kaffiene works best for me.

---

### Post by Gouz on 2007-08-15
the book of linux...Thanks :P ...

Fixed....Thank you and thanks for the book ;)

---

