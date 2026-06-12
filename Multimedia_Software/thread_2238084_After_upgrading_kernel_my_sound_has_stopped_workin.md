---
title: "After upgrading kernel my sound has stopped working"
date: 2014-08-05
forum: Multimedia Software
---

### Post by yoesh on 2014-08-05
Hello there. I am not exactly a power user but I have done some searching and tried a few thing, including removing and reinstalling the pulseaudio and alsa packages. In gnome's sound settings I have only dummy output listed and no hardware is listed on that tab. All previous kernel versions on my computer have the same problem when I boot into them.

Here is my lspci output:

*** 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

So the hardware is recognized. It's almost like the driver just disappeared. When I run sudo aplay -l the output is:

*** aplay: device_list:252: no soundcards found...

I also made sure that /etc/default/speech-dispatcher was set to "NO" and it already was. In another forum I saw someone talking about drivers being blacklisted. Can someone tell me more?

Thanks so much for everyone's time and efforts here. I really appreciate the open source community. OSS is the future!

Mike

---

### Post by yoesh on 2014-08-05
Sorry for being a newb, I am working through the troubleshooting guide stickied at the top of this forum now. The output I get from alsa-info.sh is here: [http://www.alsa-project.org/db/?f=094fb4a76b6c4b3ab6858971678b1b43ab24a400](http://www.alsa-project.org/db/?f=094fb4a76b6c4b3ab6858971678b1b43ab24a400)

Obviously there is no sound driver. I will continue with the guide and update as necessary. Thank you for your patience.

---

