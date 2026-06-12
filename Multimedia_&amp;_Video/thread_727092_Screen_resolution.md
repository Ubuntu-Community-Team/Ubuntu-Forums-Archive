---
title: "Screen resolution"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by yousillygoose on 2008-03-17
My problem is a fairly random problem.  When I go to the Screen Resoution Preference tool and choose a new resolution it sometimes works (which isn't the problem).  The problem is that it randomly will stop working until I either log out and log back in or restart.  I was wondering how I could possibly fix this problem or a way to go around it without restarting.  Thank you

---

### Post by askreet on 2008-03-17
Your Xorg logs are probably showing xrandr (X Rotate and Resize) errors.  Please post the log files under /var/log/Xorg.0.log

---

### Post by yousillygoose on 2008-03-17
Do you want it all or just this part


(II) NVIDIA(0): Setting mode "DFP-0:1024x768_60@1024x768+0+0"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "DFP-0:1024x768_60@1024x768+0+0"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "DFP-0:1024x768_60@1024x768+0+0"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "DFP-0:1024x768@1024x768+0+0"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "DFP-0:1920x1200@1920x1200+0+0"
(--) NVIDIA(0): No video decoder detected

---

### Post by yousillygoose on 2008-03-17
bump

---

