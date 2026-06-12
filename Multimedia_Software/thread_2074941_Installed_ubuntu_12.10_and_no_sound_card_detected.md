---
title: "Installed ubuntu 12.10 and no sound card detected"
date: 2012-10-22
forum: Multimedia Software
---

### Post by Salvagluque on 2012-10-22
Hi guys,

well, here is the deal. I installed the new ubuntu 12.10. And I think it started when I installed the additional drivers package to use mi nvidia card. And when I went to see the  pulseaudio volume control, the configuration says NO card available to configuration.

So, any help will be appreciated.

-Salvador

---

### Post by pqwoerituytrueiwoq on 2012-10-22
```
aplay -l
``````
lspci | grep Audio
```are you using analog audio on hdmi video?
check *alsamixer*

---

### Post by Salvagluque on 2012-10-22
thanks, but didn't work. Still no device for the configuration.

---

### Post by Salvagluque on 2012-10-22
and no, no analog audio.

---

### Post by Salvagluque on 2012-10-22
thisi s the model

 Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)

---

### Post by Salvagluque on 2012-10-25
Well, at the end the only thing that worked for me was formatting the whole computer and reinstall ubuntu 12.04 (my grub doesn´t catch ubuntu 12.10´s dvd, don´t know why) and then upgaded to ubuntu 12.10. And the sounds work perfectly well now. This problem started when I installed the additional packages for Nvidia videocards (which I don´t even know what its function is), So now I didn´t install it neither anything related to pulse audio, which I suspect was the other responsable of that problem.

-Salvador

---

### Post by Tyrr on 2012-10-26
Hello

Same problem here (no sound), I tried the code abouf, but to no avail.

```
~$ aplay -l
aplay: device_list:252: geen geluidskaarten gevonden...
~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
```

So, no sound cards found. Any suggestions?

thanks
tyrr

---

### Post by Salvagluque on 2012-10-26
HeY Tyrr, well what I was forced to do due to a project was to format the disk with the ubuntu 12.10 Os. And after reinstalling it make sure I didn't install anything related to pulseAudio. And everything works fine.

And eventough I removed the pulseaudio the system kept confused with the nvidia video card. Maybe if you remove anything from pulseaudio and install ALSA maybe you won't have to reinstall the entire os.

Good luck

-Salvador

---

