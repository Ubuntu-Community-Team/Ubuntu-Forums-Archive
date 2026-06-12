---
title: "Video glitch when playing any movie"
date: 2012-05-21
forum: Multimedia Software
---

### Post by PeterTaps on 2012-05-21
Folks,

I am running VLC 1.1.12 on a clean machine with Ubuntu 11.10. It has nVidia GPU card and the latest nVidia drivers.

When I run a movie, what I see is that once every 30 or 40 minutes, for a fraction of a second, the screen splits into two horizontal halves. The upper part stays stationary and the lower part updates to the next frame.

This is not vlc specific problem as we see the same problem when the movie is played through mplayer.

It is also not hardware or movie specific. When the machine is booted into Windows OS and the same movie is played, we don't observe this issue.

I am wondering if could share your thoughts on what we could do to identify the cause.

Thank you in advance for your insight.

Peter

---

### Post by Nutria on 2012-05-21
> **PeterTaps said:**
> Folks,

I am running VLC 1.1.12 on a clean machine with Ubuntu 11.10. It has nVidia GPU card and the latest nVidia drivers.

When I run a movie, what I see is that once every 30 or 40 minutes, for a fraction of a second, the screen splits into two horizontal halves. The upper part stays stationary and the lower part updates to the next frame.

This is not vlc specific problem as we see the same problem when the movie is played through mplayer.

It is also not hardware or movie specific. When the machine is booted into Windows OS and the same movie is played, we don't observe this issue.

I am wondering if could share your thoughts on what we could do to identify the cause.

Thank you in advance for your insight.

Peter

When did this start happening?

I wonder if it could be a heat-related issue, where the Linux driver isn't doing a good enough job at regulating the card's fan speed.

What kind of card do you have, and -- if there's a fan -- does it spin up under Linux?

While watching a movie, run the NVIDIA X Server Settings app and select Thermal Settings so you can monitor the card temp while the movie plays.

---

### Post by PeterTaps on 2012-05-22
Thank you for your help.

The card is nVidia GeForce GTS 450.

I will try to monitor thermal metrics as you suggested.

Regards,
Peter

---

