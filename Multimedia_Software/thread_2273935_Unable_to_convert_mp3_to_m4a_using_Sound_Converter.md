---
title: "Unable to convert mp3 to m4a using Sound Converter?"
date: 2015-04-16
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-16
Hello guys
I'm using Ubuntu 12.04. Sound Converter 1.5.4. When I try to convert mp3 to m4a I get the following error:
Gstreamer error when creating pipeline no element "faac".
Any help is much appreciated.

---

### Post by ajgreeny on 2015-04-16
It sounds as if you need to install the codecs needed to encode to m4a.
Try ```
sudo apt-get install **faac** **libfaac0**
```

---

### Post by remmas-sido on 2015-04-17
> **ajgreeny said:**
> It sounds as if you need to install the codecs needed to encode to m4a.
Try ```
sudo apt-get install **faac** **libfaac0**
```
I did exactly what you said, but now I get "ffmux_mp4" error. any suggestions?

---

### Post by andrew.46 on 2015-04-18
Mind you faac is currently almost at the bottom of the heap in terms of audio quality. Have a look at the table on the right:

[http://wiki.hydrogenaud.io/index.php?title=Advanced_Audio_Coding#Encoders_.2F_Decoders_.28Supported_Platforms.29](http://wiki.hydrogenaud.io/index.php?title=Advanced_Audio_Coding#Encoders_.2F_Decoders_.28Supported_Platforms.29)

Franuhofer fdk aac is achievable under Linux through FFmpeg and might be worth chasing up...

---

