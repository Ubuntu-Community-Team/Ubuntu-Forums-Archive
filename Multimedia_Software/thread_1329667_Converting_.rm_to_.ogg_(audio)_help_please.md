---
title: "Converting .rm to .ogg (audio) help please"
date: 2009-11-17
forum: Multimedia Software
---

### Post by miggerish on 2009-11-17
Can someone please tell me how to convert .rm (real media file) to .ogg? I use latest version of ubuntu.

---

### Post by HappyFeet on 2009-11-17
Try soundconverter. You may need the gstreamer codecs as well.

---

### Post by miggerish on 2009-11-17
> **HappyFeet said:**
> Try soundconverter. You may need the gstreamer codecs as well.

What are "gstreamer codecs" and how do I get them?

---

### Post by andrew.46 on 2009-11-17
Hi miggerish,

> **miggerish said:**
> Can someone please tell me how to convert .rm (real media file) to .ogg? I use latest version of ubuntu.

If you don't mind the commandline there is a slightly ugly method that first converts the file to wav:

```
mplayer **[COLOR="Red"]input.rm[/COLOR]** -vc null -vo null -ao pcm:fast:waveheader:file=output.wav
```

and then use oggenc to trancode to ogg:

```
oggenc -q 6 output.wav -o final_file.ogg
```

I suspect that most gui programs will use a similar technique but shield you from the ugly details :). 

Andrew

---

### Post by HappyFeet on 2009-11-17
> **miggerish said:**
> What are "gstreamer codecs" and how do I get them?

I would add the medibuntu repos : You can add the following all at once
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
Then
```
sudo apt-get install non-free-codecs
```

---

