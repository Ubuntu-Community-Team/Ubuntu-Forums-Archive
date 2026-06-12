---
title: "Converting Protected DVDs to Mp4 Format"
date: 2014-11-27
forum: Multimedia Software
---

### Post by tuebinger90 on 2014-11-27
I'd like to convert some old DVDs to mp4s, or similar video format, so I can enjoy them on my computer.  The problem is my computer running ubuntu doesn't even play them.  The DVDs show up in the file manager as 'AUDIO-TS' and 'VDEO_TS' folders, with various files in them, none of them playable.

I don't mean to circumvent copyrights but I just want to be able to play the files on my computer in a digital format. Is there a way to do this?

Thank you for any help you can give me.

---

### Post by SeijiSensei on 2014-11-27
First, follow the steps to install restricted-extras and libdvdcss as described here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Next, install Handbrake from John Stebbins's PPA:
```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk

```
For details on using the program, visit [https://handbrake.fr/](https://handbrake.fr/).

If you want to encode movies with subtitles or multiple language tracks, Matroska (.mkv) is a better container than MP4.

---

### Post by tuebinger90 on 2014-11-29
Thank you.

---

