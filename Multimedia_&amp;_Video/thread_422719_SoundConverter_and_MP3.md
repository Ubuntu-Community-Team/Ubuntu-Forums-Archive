---
title: "SoundConverter and MP3"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by bobromeo on 2007-04-25
Installed SoundConverter 0.9.4.
No MP3
Had gstreamer0.10-plugins-ugly installed, so re-installed it.
No MP3
Found a remark here about ´fleundo´ and found Flumotion, installed it.
No MP3

Ideas ?:confused:

---

### Post by phr0ze on 2007-05-03
I have this same problem. I was hoping there was an answer here, but your post went for a week without an answer.

Trying to use Soundconverter to make/convert to mp3s. It says the MP3 encoder is not installed. It has a link in the preferences to a how-to.  The how-to simply says install gstreamer ugly. Well thats already installed on my Feisty.

Does anyone have a solution?

---

### Post by phr0ze on 2007-05-03
Ok. although Feisty said gstreamer ugly was installed, I decided to install using apt-get. This has solved my problems. All I did was type this on a command line:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by pjrodz on 2007-05-08
> **phr0ze said:**
> Ok. although Feisty said gstreamer ugly was installed, I decided to install using apt-get. This has solved my problems. All I did was type this on a command line:

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

this one worked for me. thanks! :)

---

