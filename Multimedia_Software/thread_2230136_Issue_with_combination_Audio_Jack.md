---
title: "Issue with combination Audio Jack"
date: 2014-06-17
forum: Multimedia Software
---

### Post by aaroncampbell2 on 2014-06-17
I recently set up Ubuntu 14.04 on a new Asus S400CA laptop. Everything seemed to work great (seriously: wifi, touchscreen, audio, everything...it was SO nice!). Unfortunately, today I plugged in a headset (just earbuds/mic with a single 3.5mm jack...the kind commonly used with all cell phones) and while the sound went through the headphones, it didn't seem to recognize the mic. The laptop uses a single combo-jack for audio/mic, which worked under Windows 8.

I have no idea what info might be needed. In IRC I was asked for this:

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
```

---

### Post by Bucky Ball on 2014-06-17
*Thread moved to **Multimedia & Video**.*

Welcome. Better here. ;)

---

### Post by Yellow Pasque on 2014-06-17
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by aaroncampbell2 on 2014-06-17
Thanks!
[http://www.alsa-project.org/db/?f=be165c9f5ebb9907ebba53db923f44bf762d0894](http://www.alsa-project.org/db/?f=be165c9f5ebb9907ebba53db923f44bf762d0894)

---

### Post by Yellow Pasque on 2014-06-17
When you plug the headset in, do you have an option to select it as input in the audio settings?

---

### Post by aaroncampbell2 on 2014-06-17
When I plug the headset in, the output section of the audio settings switches from speakers to headphones. The input tab doesn't change at all.

---

### Post by Yellow Pasque on 2014-06-17
In that case, I'd file a bug:
```
ubuntu-bug audio
```

Some Asus laptops have a combination jack that supports headphones or mic, but only one at a time. However, this model appears to have a true combination jack.

---

### Post by aaroncampbell2 on 2014-06-19
Thanks - [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1332233](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1332233)

---

### Post by prativasic on 2014-12-30
In my case, this has solved the problem:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32)
> [INDENT]Here is an intermediate workaround:

For those of you who are missing a speaker port, edit /usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf and comment out all lines that start with "required-any".

For those of you who are missing an internal mic port, edit /usr/share/pulseaudio/alsa-mixer/paths/analog-input-internal-mic.conf
 and comment out all lines that start with "required-any".

It is important that you comment out (or remove) all those lines, if you leave one behind, it won't work.

After the change, you can either execute "pulseaudio -k" or reboot for the changes to take effect.[/INDENT]

By the way, I am running Ubuntu 14.04.1 x64 on my Asus S400CA. Skype(v4.3.0.37) also works fine.

---

### Post by jimbo10 on 2015-01-01
> **prativasic said:**
> In my case, this has solved the problem:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32)

By the way, I am running Ubuntu 14.04.1 x64 on my Asus S400CA. Skype(v4.3.0.37) also works fine.

the file is "read only"........can it be edited?

---

### Post by prativasic on 2015-01-01
That's because it's a system file. Use sudo

---

### Post by Bucky Ball on 2015-01-01
*Thread closed. *

Thanks for the input, but this thread is old and has been dormant since last June. Let's leave it that way. ;)

For any new support requests please create a new thread.

---

