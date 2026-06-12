---
title: "Ubuntu And Neomagic - There Has To Be A Better Way"
date: 2010-05-02
forum: Multimedia Software
---

### Post by chris1379 on 2010-05-02
I've been using Ubuntu for a few months now and I'm mostly happy and even impressed for a free OS. I've tried Hardy, Karmic, Mint 5 and now Lucid. My idea was to replace Windows 98 or 2000 as the primary OS on this laptop, a Sony PCG-F580K with a Neomagic NM2380 chip. Everything works just as well with Ubuntu with one exception. The video performance is much better in Windows. I'm not talking about 3D or anything complex, just watching DVD, DivX, mp4, etc. I have VLC on Windows 2000 and Ubuntu and I only see one big difference between them. Windows uses DirectX to display the video, while Ubuntu uses XVideo. DirectX doesn't use the CPU but Xvideo uses around 20%.  With a 700 MHz CPU, this can make the difference between smooth video and unwatchable stuttering.

So, is there a Linux equivalent to DirectX? I see there is something called DirectFB but I can't find enough info on it to know if it could work. Is there something I'm missing or am I hopelessly stuck with using Windows to watch video.

---

### Post by WinterRain on 2010-05-02
You really can't compare win2k with the latest ubuntu. Win2k can run on 128mb ram, and is very lightweight, saving resources for other operations. I would go with another distro that is made for older computers, such as [Antix Mepis]("http://antix.mepis.org/index.php/Main_Page"). It's debian based like ubuntu, so the commands are very similar. I highly recommend it. Use the right tool for the right job.

You might also want to try Puppy linux on that machine, which is even lighter than antix.

---

### Post by chris1379 on 2010-05-06
Actually, Ubuntu doesn't use much more memory than Win2K and seems just as fast in everyday tasks like web surfing. Playing video is the only time I have issues. It does work but just uses more CPU than Win2K. I did see that VLC is going to support GPU acceleration in the next release so maybe that's the answer.

The one thing I can't figure out is why the same version of VLC has less CPU usage in PCLinuxOS. They recommend even more RAM and a faster CPU than Ubuntu and it's loaded with everything. While playing a DVD, htop shows the first VLC line in PCLinuxOS as 15-20% but it's 20-35% in Lucid. Since the total usage is 70-80% this could help alot.

Thanks for the suggestions. I'm currently downloading AntiX and plan to try Puppy but I'm afraid that lightweight means less capable. Would you believe I can use Skype with a bluetooth headset in Lucid? Anyway, I'll try the lighter ones. You never know til you try it.

---

