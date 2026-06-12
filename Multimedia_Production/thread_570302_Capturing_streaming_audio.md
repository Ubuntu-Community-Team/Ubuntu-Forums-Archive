---
title: "Capturing streaming audio"
date: 2007-10-08
forum: Multimedia Production
---

### Post by O__________o on 2007-10-08
I want to capture streaming audio from my browser.
Is there any way to do this in linux?

---

### Post by O__________o on 2007-10-08
Can anyone help me?
:(

---

### Post by eye208 on 2007-10-08
You can use VLC to capture audio streams. Optionally you can also transcode them on the fly.

---

### Post by orange2k on 2007-10-11
Try Streamripper: its a program you have to start in a console.
Its available in the repositories.

Its not very hard to operate - I mostly use it like this:

streamripper <stream_url> -l 1800 -a stream.mp3

To explain: -l 1800 means that you want to rip only 1800 seconds of the stream. -a means you want to create only one file with the name "stream.mp3".

There are many other options that you can use - type only *streamripper* and look for other available commands and explainations...

---

### Post by wrathkeg on 2007-10-11
I have used Audacity to do this, with good results.

WK

---

