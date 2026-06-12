---
title: "Mic Problem on my IBM X61 Tablet. Please Help . No Skype"
date: 2011-03-11
forum: Multimedia Software
---

### Post by atentik on 2011-03-11
My Microphone does not work. I tried using Skype but there is no input sound. I tried the gnome-sound-recorder but there is no sound after pressing the record button...only white noise. Please help resolve this problem. Even the video for my usb camera using cheese does not work.

Thanks.

---

### Post by cmckdub on 2011-03-12
I think we need some more information to help you. Is the microphone plugged into the microphone socket or is it a USB microphone with the camera? If so, what model of camera is it? Have you checked that it is supported?

---

### Post by atentik on 2011-03-12
> **cmckdub said:**
> I think we need some more information to help you. Is the microphone plugged into the microphone socket or is it a USB microphone with the camera? If so, what model of camera is it? Have you checked that it is supported?

Thanks. The webcam comes with mic and it is a usb Creative USB webcam. I don't know the exact model but I know it worked when I had Ubuntu 10.04 but after upgrading to 10.10, the webcam mic stopped working. The internal mic, though, never worked.

---

### Post by coldraven on 2011-03-12
I don't know if this will help but I had a problem with Skype distorting sound so that I could not be heard.
I had reduced the levels in the Sound Prefs menu but still no good.
So I opened a terminal and typed ```
alsamixer
```
I noticed that the Master level was in the red, so I reduced it to 75.
Press F4 for Capture, use the L/R arrow keys to go to Internal Mic Boost.
It was set to zero so I increased it with the up/down arrow keys to 33.
Skype is working fine now.

---

