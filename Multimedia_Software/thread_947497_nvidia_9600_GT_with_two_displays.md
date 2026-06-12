---
title: "nvidia 9600 GT with two displays"
date: 2008-10-14
forum: Multimedia Software
---

### Post by jrothney on 2008-10-14
Hello,

For the past 9 months or so, I have been using an older box successfully with two displays:
- ViewSonic E771-4 (CRT-0) / a crappy old monitor, via VGA out
- TSB-TV (DFP-0) / a 1080i LCD TV, via DVI --> HDMI

I've been using Hardy Heron (32bit) and an NVIDIA GPU GeForce FX 5200 (NV34) (AGP) and the stock nvidia drivers, (169.12).

Last week I put together a new box using Hardy Heron (64bit) with an NVIDIA GPU GeForce 9600 GT (G94) (PCI-E). I have been unable to get the LCD display to be recognized.

I used EnvyNG to install the newer nvidia driver (173.14.12) and then downloaded and installed the latest one (177.80). When using nvidia-settings, the "Detect Display" seems to do nothing.

I modified my xorg.conf to look similar to the one I was having success with on the old box. No luck.

I have attached the xorg.conf and Xorg.0.log from each setup.

Any suggestions on how to debug (and hopefully solve) this problem?

---

### Post by SuperSonic4 on 2008-10-14
what does nvidia-settings say under "Display Configuration". Load it up as root ```
gksudo nvidia-settings
``` and see if their GUI helps. It could be something with the kernel because I can't get mine to work on Mandriva 2009.0 or Intrepid

---

### Post by jrothney on 2008-10-15
OK, I seem to have gotten this to work, at least for the moment.

Following a tip in another thread, I disconnected the DVI cable which feeds the LCD and rebooted.

After the restart, I reconnected the cable, and went to nvidia-settings. The LCD was not listed, but I tried to "Detect Displays". It recognized the LCD as screen 1 and told me I needed to restart X to activate it.

I did a cntl-alt-backspace and sure enough the LCD screen was active.

I have not restarted yet, so I cannot confirm whether this will hold, or whether I'll need to go through disconnect/connect/detect again.

I'll post a follow-up when I have more details. In the meantime, its working and I am relieved.

---

