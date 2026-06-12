---
title: "Waves MaxxAudio Pro Driver for Ubuntu 16.04"
date: 2019-04-23
forum: Multimedia Software
---

### Post by valarsundarlis on 2019-04-23
Alright, I followed the steps in this link: [https://askubuntu.com/questions/246684/do-i-need-any-extra-drivers-for-the-realtek-waves-maxx-audio-on-my-dell-xps-17](https://askubuntu.com/questions/246684/do-i-need-any-extra-drivers-for-the-realtek-waves-maxx-audio-on-my-dell-xps-17)
I also followed the 'sound troubleshooting procedure' thread in this forum, in vain.

But I could hardly get 30-40% of the audio quality I get when I'm on Windows 10 (I use a Dell Inspiron 7378)
And my laptop usage is 98% ubuntu, so...

Is there any other solution to this? Can someone tell me if Realtek has drivers for Ubuntu? I can't find any.

---

### Post by Yellow Pasque on 2019-04-24
> Can someone tell me if Realtek has drivers for Ubuntu?

They're included in the kernel (or you wouldn't be hearing any sound). Realtek used to have custom Linux audio drivers, but they stopped maintaining them years ago because the kernel drivers made them unnecessary.

> Is there any other solution to this?

Google a program called pulseeffects. It does similar things to proprietary audio enhancement software. I can't say if it's a complete replacement without knowing exactly what "Maxx Audio" does.

---

