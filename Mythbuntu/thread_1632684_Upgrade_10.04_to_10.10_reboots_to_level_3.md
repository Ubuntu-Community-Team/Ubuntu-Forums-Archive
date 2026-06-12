---
title: "Upgrade 10.04 to 10.10 reboots to level 3"
date: 2010-11-28
forum: Mythbuntu
---

### Post by lviperz on 2010-11-28
I just finished upgrading to 10.10 from 10.04 via the update manager. Once the system rebooted all I get is a login prompt. I can log in but X does not start, all I get is a prompt.
 
I'm not sure what I need to do. It looks like the backend is running as I can get to mythweb.

---

### Post by lviperz on 2010-11-28
Update. I deleted my xorg.conf file and restarted gdm. Now X starts as does the frontend. Problem now is resolution. I have an nvidia card installed but without the nvidia driver loading in the xorg.conf I can't set the 1280x720 resolution. I only have the option for 640x480, 800x600 or 1024x768.

---

### Post by thatguruguy on 2010-11-28
which nvidea card are you using?  Is it supported by the newest drivers?

You may need to remove the noveau drivers in order to get nvidea's proprietary drivers to work.

---

### Post by lviperz on 2010-11-29
Thanks, I found a post talking about my exact problem with same hardware. I have an old nvidia mx440 in a dimension 8300 and it was my problem.

For now I just backed up to 10.04 until I find the time to finish me new system with more recent hardware.

---

