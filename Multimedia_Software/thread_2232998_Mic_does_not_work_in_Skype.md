---
title: "Mic does not work in Skype"
date: 2014-07-05
forum: Multimedia Software
---

### Post by Lloydb39 on 2014-07-05
Using 12.04 on homebuilt AMD. Skype calls, connects, I can hear/see them, they can see me but can't hear me. Skype test call does not show input. However, Ubuntu sound settings show blips on the bar when I am testing. I am using a Logitech webcam for video and audio. Pulse Audio shows "rear microphone" setting but I changed to front and line in and neither of them works either. How can I troubleshoot or fix?

---

### Post by merlinus on 2014-07-05
You might have a look at Options/Sound Devices in the skype software.

---

### Post by Lloydb39 on 2014-07-05
Fixed by calling alsamixer in terminal window, finding front mic and turning up the volume (for anyone else with this problem)

---

