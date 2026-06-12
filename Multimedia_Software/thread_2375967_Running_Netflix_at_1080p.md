---
title: "Running Netflix at 1080p?"
date: 2017-10-29
forum: Multimedia Software
---

### Post by timonoj on 2017-10-29
Hi guys,

I'd love not to have to switch to Windows just for getting netflix at 1080p. My TV is rather large, so playback at 720p is noticeably poor. I'd really need to get those 1080p if I'm not to switch back to windows just for that. At this moment I went to the pain of installing Virtualbox with a W10 image with netflix installed. But the framerate with the guest addons installed is still rather bad, somewhat 20fps. I have 2D video acceleration enabled, but doesn't seem to do much. On the host, I have a Core i7 6700 with 16GB of RAM and an Nvidia 1070...so it's not quite the weakest machine just to play netflix at its expected framerate. What could I be doing wrong? How can I get proper framerate on netflix at 1080p? 

Thanks!

---

### Post by TheFu on 2017-10-29
$45 for a media player stick solves your issue, 100%.  Get a roku3 or newer and be happy.  DRM will always get into the way non-Windows systems, though Android does have some pull these days.

If you use KVM and have the proper motherboard and video card, you can run Windows inside a VM using GPU passthru.  It is non-trivial, but gamers are loving it.  

Last spring, I saw an intel virtualmachine GPU sharing demo where different guests had full access to the same GPU.  It hasn't been incorporated into any packages that I know yet, but if you are hardcore on this, you can get the code.  Intel calls it gvt-g. [https://www.phoronix.com/scan.php?page=news_item&px=Intel-GVT-G-Linux-4.10-State](https://www.phoronix.com/scan.php?page=news_item&px=Intel-GVT-G-Linux-4.10-State)  and [https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide](https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide)

If netflix is your "killer app", enough to get you to switch to Windows, I suppose that's fine. Usually people have a killer app that earns them money.

As for tuning virtualbox virtual machines, there are many guides about that on the internet.  Some of the default settings aren't good for performance, but are good for compatibility.
* Don't  allocate too many CPUs.
* Don't allocate too much RAM.
* Always use virtio for disk and network drivers
* enable 2D and 3D GPU access - only after everything else is working.
* Only use sparse storage on SSDs.  For spinning disks, use fully pre-allocated storage.
* Choose the newest chipsets when offered for storage controllers and others.

---

### Post by SeijiSensei on 2017-10-29
Are you using the proprietary NVIDIA driver? I have a GTX 750, and everything looks fine at 1080p.

If not, you can install it with 
```

sudo apt-get update
sudo apt-get install nvidia-current
```

---

### Post by heliosh on 2017-10-29
> **SeijiSensei said:**
> Are you using the proprietary NVIDIA driver? I have a GTX 750, and everything looks fine at 1080p.
You get 1080p on linux? How did you manage that, with which browser? Can you show the status information (Ctrl-Alt-Shift-D while playing)?

---

### Post by timonoj on 2017-10-30
I doubt he meant through the browser, Netflix's official statement is that they block 1080p on purpose on anything non-edge running windows, or safari in mac-os...Or the apps, of course.

I realize now I didn't have 3D acceleration enabled, I'll try that today.

---

### Post by timonoj on 2017-10-30
Ok, 3D acceleration enabled. And I can't confirm the slowness leaves...Because now I get a black screen. It's kind of flickering slowly. Sometimes it refreshes and I can see netflix underneath, but it's mostly all the time black. It might be related with a bug with virtualbox, Nvidia GPUs and Windows 10 guests:
[https://techblog.devlat.eu/2017/04/07/screen-flickering-in-virtualbox-with-3d-enabled/](https://techblog.devlat.eu/2017/04/07/screen-flickering-in-virtualbox-with-3d-enabled/)

I tried installing the patch to no avail. But then again, that library is for an older version, so maybe that's the reason :(

---

### Post by SeijiSensei on 2017-10-31
> **timonoj said:**
> I doubt he meant through the browser, Netflix's official statement is that they block 1080p on purpose on anything non-edge running windows, or safari in mac-os...Or the apps, of course.
Turns out no browser on Linux can stream Netflix at 1080p.  Here's the [current list]("https://www.digitaltrends.com/home-theater/getting-hd-netflix/"):

Google Chrome: up to 720p
Firefox: up to 720p
Opera: up to 720p
Safari: up to 1080p (on Macs running OS X 10.10.3 or greater)
Microsoft Edge: up to 1080p
Internet Explorer: up to 1080p

I assumed it was possible because other video services I use, e.g., Crunchyroll, can stream at 1080p just fine. Amazon is another offender.  Even though I have a video card with HDMI connected to my television through my A/V receiver, Amazon says my hardware/software do not conform to HDCP.  I suspect they are wrong.

I rarely watch any of these services through a computer any more.  I have better success with my PS3, or the built-in apps in my LG TV.

---

### Post by timonoj on 2017-11-01
Yeah. But my Sony's TV decoding quality doesn't look exactly as sharp as the desktop app. I don't know, it feels like there's slightly more noise around the moving objects. It's the netflix embedded app. I can install the Android one, since it came with it, but that one is more touch based, and doesn't work very well with the remote. Not to mention the Sony TV's LAN adapter is a crappy 100Mbps one, that doesn't even get close to the official speeds. Barely reaches 50Mbps on the Netflix connectivity test. Takes considerably longer to reach 1080p when playing. Now that I think of it, maybe that's why it's not as sharp, maybe it's a lower bitrate 1080p due to bandwidth bottleneck on the TV.
I really wanted to have the same quality I get on Windows also in Linux...but seems there's no working alternative yet. VMWare runs much smoother than Virtualbox, but somehow still stutters a bit...maybe it's making 28-29fps, but it's still not as smooth as a real Windows.

---

### Post by timonoj on 2017-11-02
Ah well, what do you know. I updated the APK of the Netflix app, turns out it was rather outdated. This more recent version does no longer have garbage around moving pixels, and on speed tests pulls 95Mbps. Even way too close to the technical limit of the TV's network adapter, so either compression or a bad report are at play here. Either way, this problem has been "solved" for me in the worst possible way (the "don't use Linux" way).

---

### Post by TheFu on 2017-11-02
Netflix streaming won't exceed 15Mbps, so 50+ is more than sufficient.  Usually, it is closer to 2-5Mbps used, so 100 base-tx is way,way, way, overkill.

APKs are for Android, not Ubuntu.

Please mark the thread "solved", if this is solved.  That helps the community.

---

### Post by timonoj on 2017-11-02
Well...yeah. Theory is nice and all, but with the previous version that barely made it to 50Mbps *theoretical in a speed test*, it took netflix its good 20 seconds of streaming to switch from a crappy blurry video to the 1080p "pixels moving around" version. With the newer version version it just starts at 1080p.  And made me wonder several times if I'd ever invest in the 4K Netflix. It would be convenient, but them locking down the system that I know has zero network issues (my PC) and limiting it to the TV with an old 10/100 adapter, will keep me postponing it, at least for another year. Shame, since I have a 4K large TV that would *really* benefit from the 4K, and a 500Mbps symmetrical bandwidth, which wouldn't make an issue. If it wasn't for the crappy TV network adapter. ANd for Netflix's crappy Linux lockdown. Anyway, as mentioned, the issue is solved, but in the worst way of "solved".

---

