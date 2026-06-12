---
title: "System Freeze/lock/hang on watching TV AND playing video"
date: 2008-02-02
forum: Mythbuntu
---

### Post by DouglasK on 2008-02-02
First, sorry for the long story, but I'm really not sure where to start.  I've seen this happen before and fixed it with a complete reinstall of MythBuntu 7.10.  I don't want to keep reinstalling it.  So here's the events leading up to the problem:

As soon as I attempt to watch TV or a recorded video my system freezes/locks/hangs.  (caps lock light does not respond)

I can watch TV and recorded video using MythFrontend on my laptop and using VLC on the backend machine.

I was able to watch TV earlier today without issue both from the system with the backend and from my laptop.  

Later, I tried to watch tv on the laptop.  The screen blanked for about 30 seconds and it returned to the menu.

I went to the machine with back/frontends on it and tried tv and it did the same thing, so I rebooted.

After reboot, the backend wasn't running.  Solution: reconfig the backend.  The backend is now running fine, can watch from laptop.

If I try to watch TV on the backend machine or play a full screen video in mythFrontend, the system locks right away.  Waiting 5+ minutes does not see it go back to the menu.


Here's my system specs:
MB: Asus K8N
Ram: 1.5Gb
HD: 80Gb (over 40GB free)
CPU: Athalon64 2800+
Video: ATI Radeon 9600 running Open Source driver
Xserver: xorg
Tuner1:  Hauppage WinTV PVR USB2
Tuner2:  Hauppage WinTV 150
Sound: is on board (lspci shows "00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)"


Any ideas would be greatly appreciated.

Best Regards,
  Douglas

---

