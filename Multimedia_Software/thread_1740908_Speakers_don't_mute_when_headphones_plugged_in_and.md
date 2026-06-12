---
title: "Speakers don't mute when headphones plugged in and other problems. Ubuntu 10.10"
date: 2011-04-27
forum: Multimedia Software
---

### Post by mssnathynats on 2011-04-27
Hello everybody!!...

I'm totally new on this kind of forums but I didn't have other choice more than ask. 

I have issues with my sound board configuration. My speakers don't mute when headphones are plugged in and my mic doesn't work good. 

I have being readed all kinds of forums and I found that the main issue is in that maybe the ALSA is not using the correct model.  I tried modifying the archive
 
/etc/modprobe.d/alsa-base.conf 
with 
options snd-hda-intel model="mymodel"

with different kinds of models but I couldn't found the right one. I tried all the Lenovo ones that I found in 

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

and all the "suggestions" made by google refering to my sound board.

My laptop is a Lenovo G455 and my sound board is an ATI Technologies Inc SBx00 Azalia (Intel HDA)

Please help me, I love Ubuntu but this is bothering me since I upgrade to version 10.10.

---

### Post by lidex on 2011-04-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by marc12polo on 2012-05-01
Hello, i the same problem.
Here is output ==> [http://www.alsa-project.org/db/?f=35522aa09db6ddd13886c762b28cfb8e2b517d8c](http://www.alsa-project.org/db/?f=35522aa09db6ddd13886c762b28cfb8e2b517d8c)

Thank you for any help

---

### Post by shamimdaddy on 2012-07-11
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]
Hi, I apologise in advance if this is the wrong way to do this.  I also have the same problem and you seem to actually know the issue clearer than other posters.  
[http://www.alsa-project.org/db/?f=ecaa4eef85031a08fac3282e5e7e8a03212fd1ae](http://www.alsa-project.org/db/?f=ecaa4eef85031a08fac3282e5e7e8a03212fd1ae)
Thank you I very much appreciate your help.

---

### Post by dmaxel on 2012-07-15
Same issue here under Ubuntu 12.04.

[http://www.alsa-project.org/db/?f=f636e98e65a3090f1b73523e105a082b3fc1c69e](http://www.alsa-project.org/db/?f=f636e98e65a3090f1b73523e105a082b3fc1c69e)

---

### Post by wildmanne39 on 2012-07-17
Hi, this is an old thread without any help being posting in a long time so it has been closed, please start a new thread.
Thanks

---

