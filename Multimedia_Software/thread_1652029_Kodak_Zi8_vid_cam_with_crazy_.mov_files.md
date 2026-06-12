---
title: "Kodak Zi8 vid cam with crazy .mov files"
date: 2010-12-24
forum: Multimedia Software
---

### Post by [censored] on 2010-12-24
Hi. 

Just purchased a Kodak Zi8 vidcamera. 

[http://store.kodak.com/store/ekconsus/en_US/pd/Zi8_Pocket_Video_Camera/productID.156585800](http://store.kodak.com/store/ekconsus/en_US/pd/Zi8_Pocket_Video_Camera/productID.156585800)

It works great, but for some reason ubuntu 10.10 has a terrible time with the particular .mov files it uses as its format. 

I've tried editing these files with avidemux,  unfortunately the audio comes out completely screwed up somehow. Whenever I save the vid, the audio seems to be moving at double speed for some reason.

Is there some special new audio codec I need to install in order to avoid these problems? 

Otherwise, I suppose I could try converting the .mov to some other format using mencoder before I edit. Can anyone recommend a format that would be relatively lossless?

---

### Post by amsterdamharu on 2010-12-24
You could try converting it to mpg with ffmpeg and then edit it with avidemux.

To install ffmpeg and winff (the gui for easy use) you can give the following commands.
Note: it installs non free codecs, these have software patents in US and Japan and you are not allowed to use them if you live there.

# add medibuntu to sources list
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install non-free-codecs ffmpeg winff

```

When that's done you can press alt + F2 and type winff then click run.

For some reason ffmpeg sometimes encodes better and sometimes avidemux is better (if you need to increase sound for example)

---

### Post by [censored] on 2010-12-26
Hi. Someone put me onto kdenlive, and that can handle the .mov files ok.

It's a fairly sophisticated video editor too. Though I find the audio is a bit choppy while I'm editing it.

---

