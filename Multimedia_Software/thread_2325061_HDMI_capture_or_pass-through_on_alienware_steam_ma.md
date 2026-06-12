---
title: "HDMI capture or pass-through on alienware steam machine"
date: 2016-05-18
forum: Multimedia Software
---

### Post by CaptSilver on 2016-05-18
I have a steam machine from alienware with a HDMI input. How do I enable a HDMI pass-through or capture? I would prefer capture but there is no /dev/video, nor am I convinced that it supports capture. No idea on how to proceed.

01:00.0 VGA compatible controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)

Ubuntu 16.04
4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Using proprietary NVidia drivers 361.42

---

### Post by efflandt on 2016-06-01
What makes you think you have HDMI "input", you have not listed the device that you think should do that. Your GTX 860M is only video "output" (along with audio output on HDMI). All-in-one computers that have HDMI input is not to the OS, it is to display HDMI input directly to the screen as a monitor (no audio) without running the OS.

---

### Post by zafiros bonitos on 2017-02-04
Sorry to resurrect an old thread, but I'm trying to figure this out. The op did say what model he has, the Alienware Steam Machine, which does have an hdmi in. I connected a blu-ray player, and I'm sure any hdmi device would work. On the steam controller hold the middle button to bring up the menu to turn off controller or the system, switch to desktop mode, etc. If there's something connected to the hdmi in there will be another option: switch to hdmi. To switch back to steam just press the middle button on the controller again. 

Now capturing is another story. I haven't had a lot of time yet. I switched to desktop mode to download and run shotcut (shotcut.org). I couldn't get it to work with shotcut either because the hdmi signal from the blu-ray is protected, I didn't do it right with shotcut, or simply because the hdmi in on the steam machine can't be used to capture. I will keep on at it though.

---

