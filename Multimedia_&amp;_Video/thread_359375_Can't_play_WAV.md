---
title: "Can't play WAV"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by bobetko on 2007-02-11
1) How can I play WAV files?

2) Which player can play most of the different encoding formats?

3) I installed Automatix2 and installed most common codecs for playing video files. How do I update codecs (add new ones) and are they used only by Movie Player or other applications as well? For example, through Automatix2 I installed MPlayer and, as of now, I didn't manage to find file that can be played.

---

### Post by RomeReactor on 2007-02-11
Hi. Try installing the "ugly" Gstreamer plugins. In a terminal write:

```
sudo apt-get install gstreamer0.10-plugins-ugly
```

Then try using Rhythmbox to play the files. Or, if you're in Kubuntu, use Amarok.

---

### Post by bobetko on 2007-02-11
sorry, forgot to mention... I am using 6.10 Ubuntu

---

### Post by RomeReactor on 2007-02-11
Open Synaptic (System-->Administration-->Synaptic Package Manager) and click on **Settings-->Repositories**; on the first tab (Ubuntu 6.10) check all the boxes and then press the **Reload** button. Then search for **gstreamer** and install the "ugly"plugins (they should be **gstreamer0.10-plugins-ugly** and **gstreamer0.10-plugins-ugly-multiverse**.

Now open Rhythmbox and see if you can play those .wav files now.

---

### Post by RomeReactor on 2007-02-13
> **bobetko said:**
> sorry, forgot to mention... I am using **6.10 Ubuntu**

So am i... Or did you mean **Kubuntu** or **Xubuntu**?

---

