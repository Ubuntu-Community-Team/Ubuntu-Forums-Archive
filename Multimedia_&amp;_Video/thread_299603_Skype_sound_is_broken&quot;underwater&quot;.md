---
title: "Skype sound is broken/&quot;underwater&quot;"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by esyu on 2006-11-14
Hi everyone,

Whenever I run Skype 1.3.0.53 on Ubuntu 6.10 Edgy Eft, the sound is extremely broken. It is very much like hearing something underwater. This is not a connection problem. Even under Tools->Options->Sounds, playing the test sounds produces the same effect. It is the same whether I use ALSA or OSS.

However, sound works fine in every other application. Using aplay manually on each sound file in /usr/share/skype/sound is perfect. Skype for Windows works fine too on my computer.

I have had trouble finding any other posts with this exact problem, but if this is a duplicate, please let me know.

Some technical data:

Computer: Asus M6000 laptop
Processor: Intel Pentium M 1.73 GHz
Memory: 512 MB
Sound card: HDA Intel
ALSA version 1.0.11-5ubuntu1 (default version)
Linux image 2.6.17-10.33 (default version)

Thanks for any suggestions!

---

### Post by Ashrael on 2006-11-14
I encountered the same problem, i don't exactly know why, but it's probably just shitty programming on behalf of skype, Look at the version number in windows 2.5 on linux it's 1.3...that might explain, at skype they don't seem to value  their linux customers.....

I am now playing with skype in wine...not hearing my own voice back when call testing...


Ashrael

"The border between the Real and the Unreal is not fixed, but just marks the last place where rival gangs of shamans fought each other to a standstill."

-Robert Anton Wilson

---

### Post by Zhukov on 2006-11-19
Same problem here... :S

---

### Post by Ashrael on 2006-11-20
Well it seems i'm not the only one...I've been looking into this and found a link :  [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

I haven't tried any of this yet, but i'm going to, later...

Ashrael

---

### Post by Zhukov on 2006-11-21
IT WOOOOOOOOOOOOOOOOOOORKS!

Im sorry for the excitement.

BUT I'M EXCITED :D

Ok, seriously now, its quite simple, so simple I'm amazed.

Try this:

sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss

And then run Skype :)

To do it automatically at boot:

sudo echo "snd-pcm-oss snd-mixer-oss" | sudo tee -a /etc/modules 

I guess we should add this to the wiki.

If only it had SMS... :D

---

