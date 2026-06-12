---
title: "Need a program to show live video with sound from Lifecam Hd 5000"
date: 2012-03-15
forum: Multimedia Software
---

### Post by leovn on 2012-03-15
[SIZE=3]Somebody helps  me please. I really need a program to show me live video with sound  from my Webcam. I tried Cheese, camorama, guvcview and VCL player. Some  worked but only when I hit on the button "capture video" then I had a  video with sound. But the program I need is to show me video with sound  when I just open it. Please suggest me one.

Thanks in advance.[/SIZE]

---

### Post by papibe on 2012-03-16
Hi leovn.

When capturing video from VLC, you'll notice that the video window has a special title. In my case is v4l2:// (it very usual name for a video device).

If you run VLC from the command line with that as a parameter, it will open immediately the feed from the cam (no pressing buttons needed):
```
vlc v4l2://
```
Hope that helps.
Regards.

---

### Post by leovn on 2012-03-16
Thank you, papibe,
I ran the command line and the VLC player got started and showed me video from my cam, but there's still no sound. 'Cause my boss needs a program that can capture and show live video & sound at the same time. But I still could not find one.

---

### Post by CaptainJack55 on 2012-03-16
thank you

---

