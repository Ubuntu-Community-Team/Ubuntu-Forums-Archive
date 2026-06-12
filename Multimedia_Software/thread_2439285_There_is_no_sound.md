---
title: "There is no sound"
date: 2020-03-25
forum: Multimedia Software
---

### Post by alexelroki on 2020-03-25
I have sound problems. Nothing sounds.
I installed pavucontrol and it shows that there is sound but the computer does not sound, the headphones do not sound, the bluetooth device does not sound.
Maybe this will help:
[ATTACH=CONFIG]285319[/ATTACH]

---

### Post by MimziM on 2020-03-26
Have you tried

```
sudo alsa force-reload
```

Otherwise try purging and reinstalling 

```
sudo apt-get remove --purge alsa-base pulseaudio
```
```
sudo apt-get install alsa-base pulseaudio
```

And then do

```
sudo alsa force-reload
```

again

---

### Post by tea for one on 2020-03-26
Have you explored the settings in **pavucontrol**?

Pulse Audio > Configuration > The drop-down triangle (to the right of Profile)

---

### Post by alexelroki on 2020-03-26
I just have tried all your sugestions but nothing works...

---

### Post by tea for one on 2020-03-26
Is your computer a laptop or desktop?

---

### Post by alexelroki on 2020-03-26
Laptop

---

### Post by tea for one on 2020-03-27
It would be helpful if you could provide full details of your laptop, so that other forum members with same/similar devices may be able to offer advice.

Make?
Exact Model?
How old is the laptop?

You can get details by opening a terminal and installing inxi

```
sudo apt install inxi
```

Then you can run the utility with

```
inxi -Fz
```

Please post the terminal output inside code tags

---

