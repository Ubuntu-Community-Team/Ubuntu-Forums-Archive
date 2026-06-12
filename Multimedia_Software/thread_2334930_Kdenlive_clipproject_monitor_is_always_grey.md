---
title: "Kdenlive clip/project monitor is always grey"
date: 2016-08-23
forum: Multimedia Software
---

### Post by ancientcomputer32 on 2016-08-23
When I start up Kdenlive, everything is normal except that the clip and project monitors are grey. If I open and play a clip, the audio plays, but the monitor remains grey. It was working fine on Lubuntu 14.04, but I upgraded to Xenial and it does this now. How do I fix this?

---

### Post by gnowak on 2016-08-27
Use kdenlive 16.04.3 For me it is the latest stable one without the grey screen of death. :-)

---

### Post by ancientcomputer32 on 2016-09-20
How do I install it?

---

### Post by #&amp;thj^% on 2016-09-20
Right now they are at Kdenlive 16.08.1
to install it.
```
sudo add-apt-repository ppa:kdenlive/kdenlive-stable

```
```
sudo apt update && sudo apt upgrade

```

To restore the stock version of Kdenlive in (K)Ubuntu 16.04, run command:

```
sudo apt install ppa-purge && sudo ppa-purge ppa:kdenlive/kdenlive-stable
```
And
 ```
sudo apt full-upgrade
```

---

### Post by ancientcomputer32 on 2016-09-20
Hmm, the monitor's still grey. When I run Kdenlive from the terminal it says this:
```
eric@erics-ibm:~$ kdenlive
Removing cache at "/home/eric/.cache/kdenlive-thumbs.kcache"
QOpenGLShader: could not create shader
QOpenGLShader: could not create shader
QOpenGLShader: could not create shader
QOpenGLShader: could not create shader
QXcbConnection: XCB error: 8 (BadMatch), sequence: 661, resource id: 46137357, major code: 155 (Unknown), minor code: 11
```
The computer is pretty old, and I'm pretty sure the GPU (ATI Mobility Radeon 7500) doesn't support shaders.

---

### Post by #&amp;thj^% on 2016-09-20
I almost hate telling you this: Your Radeon 7500 has Pixel Shader: [B]N/A  :(
[/B]It is kind of fun seeing one still working.

---

### Post by ancientcomputer32 on 2016-09-21
Is there some way I can install the 14.04 version on 16.04? Kdenlive worked fine for me then.

---

### Post by #&amp;thj^% on 2016-09-21
Not sure if that is possible??
There is more involved than just a newer version of Kdenlive.:(
If you have room left on your hardrive you could dual boot 16.04 and 14.04....just a thought.

---

