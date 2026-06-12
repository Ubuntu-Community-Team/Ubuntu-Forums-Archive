---
title: "Stickam Shuffle, Chatroulette and.... VDPAU?"
date: 2011-04-25
forum: Multimedia Software
---

### Post by blenderfox on 2011-04-25
I have a working webcam, that works with Cheese, guvcview, Stickam and Skype (although I have to use the LD_PRELOAD workaround to get it work with Skype. When I go to the Chatroulette or Stickam Shuffle sites, and try to access their broadcast, I see this keep popping up in the console window:

```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
```

So what is a "VDPAU backend" and what do I need to do to enable me to use the webcam on Chatroulette and Shuffle. I should add that I **CAN** use it on "normal" Stickam, and I can use it on other webcam sites, like ustream.tv. It's just these two that seem a bit.... strange.

Any help is appreciated.

---

### Post by blenderfox on 2011-04-28
Still waiting on a response. I've done some research and found a similar issue reported using mplayer. But this is not mplayer I'm having trouble with, it's Chromium and Firefox.... -_-

---

### Post by blenderfox on 2011-05-22
Anybody? How do I fix this libvdpau_nvidia.so error?

---

### Post by Ariakkas on 2011-05-22
google came up with this, hope it helps


[http://vsingleton.blogspot.com/2010/02/failed-to-open-vdpau-backend.html](http://vsingleton.blogspot.com/2010/02/failed-to-open-vdpau-backend.html)

---

### Post by blenderfox on 2011-05-23
Thanks, but this site only talks about mplayer. I'm not talking about mplayer, I'm talking about a website. This is the same site that Stickam's tech support told me to look at, and it's not much help in fixing my problem :(

---

### Post by papibe on 2011-05-23
Do you have it installed? Could you post the result of this?
```
$ dpkg -l | grep vdpau 
```
Regards.

---

### Post by blenderfox on 2011-05-23
it is installed, i checked via synaptic. i noticed there were some NVIDIA VDPAU packages that weren't installed, so i installed them, but now i'm getting an error about /dev/nvidiactl (from NVIDIA driver, i guess). i'll give you the exact error when i get home, but does anyone know what this means? ><

---

### Post by papibe on 2011-05-23
Once something similar happened to me. It was an update that was not marked as "reboot needed".

At this moment it would't be a bad idea to reboot your machine, and see if the error goes away.

Regards.

---

### Post by blenderfox on 2011-05-23
well, I'll check when i get home - that would count as a reboot. let you know in a couple of hours.

---

### Post by blenderfox on 2011-05-23
Okay, I've checked, and chatroulette works, but Stickam Shuffle still doesn't. However, this time, I'm getting a different error. You'll notice I tried the LD_PRELOAD trick, but no matter whether I use it or not, Shuffle won't work becaue of the error, but chatroulette now is fine: 

> yukinom@momoko:~$ more ./startChromium 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so chromium-browser
yukinom@momoko:~$ ./startChromium
[5961:5961:4279639823:ERROR:native_library_linux.cc(32)] dlopen failed when trying to open default_plugin: default_plugin: cannot open shared object file: No such file or directory
[5837:5837:4280640812:ERROR:render_sandbox_host_linux.cc(631)] sendmsg: Connection refused
[5835:5946:4281826976:ERROR:x509_certificate_nss.cc(567)] No EV Policy Tag
libv4l2: warning v4l2 mmap buffers still mapped on close()
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).
libv4l2: warning v4l2 mmap buffers still mapped on close()
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).


---

