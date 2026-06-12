---
title: "Maktrosa files now stutter :("
date: 2008-09-02
forum: Multimedia Software
---

### Post by m1k3uk on 2008-09-02
Hi back when i used to use windows i had a few .mkv files that used to play fine under vlc under windows.  However now ive ported completely to ubuntu and the exact same files now start playing fine but when the screen pans fast or theres a lot of stuff going on the video seems to stutter and not play for a few seconds then catch up and do the same.  Audio plays fine all the way through however.

Ive been googling and searching all day but havent found any working solutions.  Ive tried disabling the option to skip the loop filter for H.264 but it hardly helped.

Does anyone have any other solutions for VLC or any other media player i dont mind using anything as long as i can view these videos properly? i read somewhere about enabling the use of my dualcore processor in a media player but i dont really understand this, anybody shed some light on it??

Thanks

---

### Post by lovinglinux on 2008-09-02
What is the resolution of the videos?

---

### Post by m1k3uk on 2008-09-03
> **lovinglinux said:**
> What is the resolution of the videos?

The resolution of the videos is 1280x720 which i assume is 720p resolution?  Anyway the monitor i use the videos on is 1440x900 so there isnt any scaling going on

---

### Post by lovinglinux on 2008-09-03
> **m1k3uk said:**
> The resolution of the videos is 1280x720 which i assume is 720p resolution?  Anyway the monitor i use the videos on is 1440x900 so there isnt any scaling going on

The problem is not the scaling, but the resolution itself. Matroska is awesome, but with that resolution it can stutter really bad, depending on system specs. My guess is that VLC was outputting the video using DirectX, which probably handled the videos better. (Someone please correct me if I'm wrong).

---

