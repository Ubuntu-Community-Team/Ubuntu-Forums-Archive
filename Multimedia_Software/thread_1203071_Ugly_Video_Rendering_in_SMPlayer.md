---
title: "Ugly Video Rendering in SMPlayer"
date: 2009-07-02
forum: Multimedia Software
---

### Post by xenogia on 2009-07-02
I have recently installed SMPlayer on my wonderful new Ubuntu 9.04 box and have noticed that video looks a little rough around the edges when going full screen.  Currently I am using the x11 renderer and have compiz enabled.

I am also using a Nvidia Geforce 8800gts 512mb graphics cards and have installed the latest nvidia drivers.  Just wondering what peoples thoughts are, and how to get around this. 

More so has anyone had this issue before?

---

### Post by Arup on 2009-07-02
> **xenogia said:**
> I have recently installed SMPlayer on my wonderful new Ubuntu 9.04 box and have noticed that video looks a little rough around the edges when going full screen.  Currently I am using the x11 renderer and have compiz enabled.

I am also using a Nvidia Geforce 8800gts 512mb graphics cards and have installed the latest nvidia drivers.  Just wondering what peoples thoughts are, and how to get around this. 

More so has anyone had this issue before?

Unfortunately, your particular card doesn't have VDPAU support or else you could have benefited from using latest mplayer with VDPAU and enjoyed full screen HD movies with high quality and minimal CPU usage. Are you using latest nvidia drivers btw or have installed via hardware drivers in Ubuntu.

---

### Post by xenogia on 2009-07-02
> **Arup said:**
> Unfortunately, your particular card doesn't have VDPAU support or else you could have benefited from using latest mplayer with VDPAU and enjoyed full screen HD movies with high quality and minimal CPU usage. Are you using latest nvidia drivers btw or have installed via hardware drivers in Ubuntu.

According to Wiki VDAPU does support my card, it doesn't support the 320mb model.  What is this about VDPAU and mplayer?

---

### Post by Arup on 2009-07-02
> **xenogia said:**
> According to Wiki VDAPU does support my card, it doesn't support the 320mb model.  What is this about VDPAU and mplayer?

In that case remove the existing mplayer and smplayer, add JYA's ppa at [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html) and enjoy your videos with VDPAU enabled mplayer and smplayer. VDPAU puts the whole graphic load on your GPU instead of CPU and improves the quality of video. Also update to latest nvidia drivers which will be there on the repository as well.

---

### Post by xenogia on 2009-07-02
> **Arup said:**
> In that case remove the existing mplayer and smplayer, add JYA's ppa at [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html) and enjoy your videos with VDPAU enabled mplayer and smplayer. VDPAU puts the whole graphic load on your GPU instead of CPU and improves the quality of video. Also update to latest nvidia drivers which will be there on the repository as well.

Thanks Arup, I will try this when I get home.  Thanks for your help :)

---

### Post by Arup on 2009-07-03
> **xenogia said:**
> Thanks Arup, I will try this when I get home.  Thanks for your help :)

You are welcome, keep us updated.

---

