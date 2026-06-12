---
title: "Any fixes for audio yet?"
date: 2009-08-19
forum: Multimedia Software
---

### Post by Mazehero55 on 2009-08-19
I've been looking around and I see lots of people have the same problem with sound being too low on ubuntu. I've done my research and looked in Alsamixer and turned up tracks etc. But my audio seems to be incredibly low on ubuntu. So low I must put my ear right up to the speaker to hear anything. 

I have 2 hdds one with windows and one with ubuntu. I'd say my windows audio is around %200 that of ubuntu. And curiously my mp3 player with rockbox sounds even louder at probably %250 sound compared to ubuntu. 

So what's going on? Is this a bug, I've searched the forum and found many people with the same problem; and there's never a fix. There must be a way to get sound past %100 on ubuntu considering Rockbox is linux as well and gets clear perfect audio. 

I don't know if I sound ticked off in this post, I'm really not. I'm content with listening to music on my mp3 player for now, but I'd like to be able to watch some of my movies eventually. I'm extremely happy with Ubuntu, and have been running it as my main OS for like 3 years now. Just mostly wondering if anyone's gotten any fixes for this yet?

Thanks

---

### Post by ajgreeny on 2009-08-19
This seems to be very much related to the hardware that you are using for sound.  I have an old (well, 4 years old) computer with an ASUS A7N8X-X motherboard and AMD Sempron(tm)   2400+ cpu with 2GB ram and on-board nForce2 AC97 Audio Controler (MCP).  Windows does not use this nearly as well as ubuntu for the sound output, and gives, or gave, as I don't really use it any more, much pooror sound with quite a lot of distortion, however I set the mixer etc etc.

What sound card do you have and what driver is it running, if you know that information.  To find the driver run ```
sudo lshw -C multimedia
```In the output there will be a line starting configuration: with a list including driver.  Perhaps google can search out a better driver, and it is just possible that you may get better sound.

---

### Post by Mazehero55 on 2009-08-19
I believe my sound card is a RealTek ALC883

By the way I've tried the fix here:
[http://ubuntuforums.org/showthread.php?t=373287&page=1](http://ubuntuforums.org/showthread.php?t=373287&page=1)

and it's not working. I also searched here:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

and there's no fix listed for my card. I don't want to try one of the others in case it'll make it worse.

Thanks for the quick reply^^

---

