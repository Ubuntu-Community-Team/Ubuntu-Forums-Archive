---
title: "Bad framerate on video playback"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by The Noodlez on 2007-10-06
I am trying to watch some videos I downloaded and am experiencing a very bad framerate upon playback.
On XP it played flawlessly, but I like Ubuntu a lot better so I was hoping I could get this working right.
Any help is appreciated and thanks in advance.

---

### Post by The Noodlez on 2007-10-06
Bump, can't find the answers on these forums, might have overlooked it...

---

### Post by rsambuca on 2007-10-06
Details?  What is your videocard, what driver are you using?  What type of video is it - ie, wmv, mpeg, xvid...?  Which media player are you using?

---

### Post by The Noodlez on 2007-10-06
Nvidia GeForce 2 MX/MX400
Using the drivers that Ubuntu gave it, because when I used the 'official' ones, it was far worse, like 3 fps.
And it's and MP4 video, but it does the same with all, including AVI, MPEG, etc.
I'm using Totem to play it.

---

### Post by rsambuca on 2007-10-06
Ok, if it is happening with all video types, we can rule out a codec issue.  Either videocard/driver issues, or player issue.  Probably the easiest check is to try another player.  Try installing vlc and see how that goes.

---

### Post by The Noodlez on 2007-10-06
Is there a very simple way to install that, as I am extremely lazy?

---

### Post by The Noodlez on 2007-10-06
SWEET!
I used sudo apt-get install vlc.
Installed it, videos run beautifully!
Thanks a million. 1000% improvement.

---

### Post by rsambuca on 2007-10-06
It is very easy to install.  Just open the Synaptic Package Manager from the top menu bar "System -> Administration -> Synaptic Package Manager". 

Enter your password.

Select "Settings - Repositories" from the top menu bar.

In the Window that opens, make sure you have the '(universe)' box checked, and then close.

Reload by pressing the top left button.

Select 'vlc' for installation and then press "Apply".

After it has done its thing, vlc is installed and ready to go from your "Applications" menu.

---

### Post by rsambuca on 2007-10-06
You can ignore my previous post since you installed it while I was typing.  

A note, though, that since vlc is working, then you probably just need to install the codecs to get better playback with totem.  Make sure you have the universe and multiverse repositories activated, and then try```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg
```

---

