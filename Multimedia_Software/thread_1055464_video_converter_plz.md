---
title: "video converter plz"
date: 2009-01-30
forum: Multimedia Software
---

### Post by legendisback on 2009-01-30
Dear users, 

i am new to Ubuntu and i have found everything great, but i 

cannot find a video converter for ipod touch, like a .avi to mp4 converter.

i Tried handbrake but it just wont open. im lost, any help?

---

### Post by mozychan on 2009-01-30
Try WinFF, the GUI for FFMPEG.

-moose

---

### Post by pedja_portugalac on 2009-01-30
> **legendisback said:**
> Dear users, 

i am new to Ubuntu and i have found everything great, but i 

cannot find a video converter for ipod touch, like a .avi to mp4 converter.

i Tried handbrake but it just wont open. im lost, any help?

Avidemux is all you'll need.

---

### Post by mozychan on 2009-01-30
To install WinFF paste the following in the terminal (Applications->Accessories) one by one if you have Ubuntu 8.10:

```
echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list
```

```
wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install avidemux ffmpeg winff
```

This will also install avidemux.

-moose

---

### Post by binbash on 2009-01-31
avidemux , handbrake

---

