---
title: "pulseaudio and skype problems"
date: 2010-10-11
forum: Multimedia Software
---

### Post by przemek35 on 2010-10-11
hi, I ve installed ubuntu 10.10 on hp g62 amd64, but on skype mic doesnt work. I ve tried playing with pulseaudio controller and everything is unmuted as well as in alsamixer. how can I solve it? i think there is some problem with alsa, because when i restart skype mic work by few minutes but after that not. please help me with tha, cheers

---

### Post by malangaman on 2010-10-11
Did your mic work on previous Ubuntu distribution?

---

### Post by przemek35 on 2010-10-12
the mic is mowrking. the problem is when i star talking via skype after few minutes my reciever can not hear me. i ve tried on ubuntu 10.04 and i was the same

---

### Post by chris1379 on 2010-10-12
Try disabling the feature in Skype that automatically adjusts your mic volume. It was problematic for me.

---

### Post by przemek35 on 2010-10-12
> **chris1379 said:**
> Try disabling the feature in Skype that automatically adjusts your mic volume. It was problematic for me.
 
I did it an it was the same. also i unmuted everything in termnal=> alsamixer
 
i tried to remove autospawn in alsa config file, it worked but sound indicator did not work properly, i could not adjust the speakers volume

---

### Post by chamithadealwis on 2011-02-09
I have the same issue. If you were able to find a solution for that, please post, will be a great help. Thanks.

---

### Post by chamithadealwis on 2011-02-09
> **przemek35 said:**
> hi, I ve installed ubuntu 10.10 on hp g62 amd64, but on skype mic doesnt work. I ve tried playing with pulseaudio controller and everything is unmuted as well as in alsamixer. how can I solve it? i think there is some problem with alsa, because when i restart skype mic work by few minutes but after that not. please help me with tha, cheers

found a solution in another thread in the same forum. simply install pulseaudio volume control, go to input devices and unmute and increase the volume to full. now everything here works fine. cheers! :guitar:

---

### Post by Agilar on 2012-10-01
Kubuntu 12.04: Yap -- install pavucontrol package. Follow this: [http://tronprog.blogspot.com/2011/05/making-microphone-work-in-kubuntu-natty.html](http://tronprog.blogspot.com/2011/05/making-microphone-work-in-kubuntu-natty.html)

---

