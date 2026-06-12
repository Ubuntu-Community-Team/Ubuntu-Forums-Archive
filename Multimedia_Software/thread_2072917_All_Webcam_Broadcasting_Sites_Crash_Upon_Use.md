---
title: "All Webcam Broadcasting Sites Crash Upon Use"
date: 2012-10-18
forum: Multimedia Software
---

### Post by kyisonfire on 2012-10-18
I got webcam studio and ever since I can't get on anything like Omegle or Chatroulette. I want to share videos on omegle and chatroulette using webcam studio. That is not working either. I have Lucid Lynx. Really stuck and frustrated.

---

### Post by kyisonfire on 2012-10-21
bump

---

### Post by kyisonfire on 2012-10-25
bump

---

### Post by sir.sargento on 2012-10-26
Are you getting any errors? Trying running the browser from terminal and post error output? That might help us start somewhere. Not saying I can fix it but can at least gather information from there.

---

### Post by Stonecold1995 on 2012-10-28
I'm having this exact same problem.  Any web pages that use Flash to access the webcam cause the plugin to crash.

Running firefox in terminal got me this (the webpage loaded but flash crashed):
```
alex@kubuntu:~$ firefox www.testwebcam.com
2.4+ kernel w/o ELF notes? -- report this
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
```

However, libvdpau_nvidia.so appears to be present.
```
alex@kubuntu:~$ locate libvdpau_nvidia.so
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.1
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.304.43
/usr/lib/nvidia-current-new/vdpau/libvdpau_nvidia.so
/usr/lib/nvidia-current-new/vdpau/libvdpau_nvidia.so.1
/usr/lib/nvidia-current-new/vdpau/libvdpau_nvidia.so.295.59
/usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so
/usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1
```

This is especially frustrating for me because I can't access any video sites through Linux, and VirtualBox doesn't have access to the webcam hardware so I can't run it in Windows either, and I'm not willing to duel boot just for webcam access.

[[IMG]http://www.pictureshack.us/thumbs/47618_crash.png[/IMG]](http://www.pictureshack.us/images/47618_crash.png)

I'm using Chromium 23.0.1271.1 Ubuntu 12.10 and Mozilla Firefox 16.0.2 with Shockwave Flash 11.2 r202 on Kubuntu 12.10.

---

