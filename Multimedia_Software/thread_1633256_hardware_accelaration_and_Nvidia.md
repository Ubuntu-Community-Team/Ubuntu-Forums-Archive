---
title: "hardware accelaration and Nvidia"
date: 2010-11-29
forum: Multimedia Software
---

### Post by beew on 2010-11-29
Hi,

I am wondering if there is a way to use hardware accelaration with a Nividia Gforce G 105M video card in Ubuntu.

Thanks.

---

### Post by cchhrriiss121212 on 2010-11-29
What for: video, 3d stuff?
Do you have the proprietary driver installed?

---

### Post by beew on 2010-11-29
I have the nividia driver installed. I want to watch hd videos, it works fine but the cpu usage seems kind of high (around 50%~60%) I have removed Windows from this machine but I seem to remember cpu usage was lower in Windows, I think the reason is gpu accelaration not being supported or not being activated.

---

### Post by cchhrriiss121212 on 2010-11-29
Try installing smplayer, then select vdpau video output from the preferences menu. Playback should then only take up around 10% cpu max.

---

### Post by beew on 2010-11-29
I installed mplayer and set the output to vdpau and then there was no sound. I am not sure whether I did something wrong or the card doesn't support vdpau. I also installed the vdpau-va-driver.

---

### Post by beew on 2010-11-29
Oh! It actually works! CPU usage drops to ~10%. I probably forgot to reboot before.

Thanks man!

---

