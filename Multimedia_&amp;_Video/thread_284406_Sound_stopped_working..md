---
title: "Sound stopped working."
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by yellow beard on 2006-10-25
I don't know how this happened, but all of a sudden im getting a red x on my volume control in the panel. When i click it it says:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I have a onboard SIS SI7012 sound card. The last thing I can think of that might of caused this is switching from the alsa driver to oss.

---

### Post by Kateikyoushi on 2006-10-25
What is the output of this ?
```
aplay -l
```

---

### Post by yellow beard on 2006-10-26
> **Kateikyoushi said:**
> What is the output of this ?
```
aplay -l
```

It says:

> aplay: device_list:221: no soundcards found...

---

### Post by Kateikyoushi on 2006-10-26
Seems the modules for your soundcard are not loaded.

Try to load them with this command and see if it works.
```
modprobe snd-intel8x0;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
```

To make the permanent add them to the /etc/modules

```
sudo nano /etc/modules
```

Check this guide for more info. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---

