---
title: "vdpau-accelerated flash on 64 bit mythbuntu"
date: 2010-12-02
forum: Mythbuntu
---

### Post by ZedThou on 2010-12-02
The flash 10.2 beta linux 32-bit build utilizes VDPAU for hardware-accelerated playback of Stage Video. The 64-bit build does not, so this evening I spend some time trying to find a way to run the 32-bit plugin in firefox, on my Atom 330 / ION frontend. Here are the highlights.

1. install the 32-bit plugin under nspluginwrapper. A method for doing this on mythbuntu is detailed here: [http://ubuntuforums.org/showthread.php?t=1635916](http://ubuntuforums.org/showthread.php?t=1635916)

Of course one would want to make sure no other flash plugins are hanging around. For example, ~/.mozilla/plugins/libflashplayer.so shouldn't exist and the flashplugin-installer package shouldn't be installed.

2. Once the 10.2 beta 32-bit flash works with nspluginwrapper, install the 32-bit libvdpau
```

# download and install getlibs, install the 32-bit libvdpau
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs -p libvdpau1

```3. Hardware acceleration will not kick in for all flash video, only "Stage Video". There are a couple of demos here:
[http://labs.adobe.com/technologies/flashplayer10/stagevideo.html](http://labs.adobe.com/technologies/flashplayer10/stagevideo.html)

Without hardware acceleration, these two 1080p demos ate up about 250% cpu on my frontend as measured by top, and playback was unwatchable. After setting up the plugin as above, CPU usage is now less than 30% and playback is fluid.

I should also mention that while trying to view the embedded HD Harry Potter trailer at [http://www.phoronix.com/scan.php?page=article&item=adobe_linux_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=adobe_linux_vdpau&num=1) it is not hardware-accelerated, but viewing the trailer directly on youtube it is accelerated - [http://www.youtube.com/watch?v=_EC2tmFVNNE](http://www.youtube.com/watch?v=_EC2tmFVNNE)

---

### Post by vipseixas on 2010-12-03
> **ZedThou said:**
> 
```

sudo ln -s /usr/lib32/nvidia-current/vdpau/libvdpau.so.260.19.06 /usr/lib32/libvdpau.so

```This depends on the exact version of the NVIDIA driver which is installed.


I did this and managed to get vdpau working for flash videos (I confirmed  that the libs were loaded using lsof), with a little big problem: it seems that this nvidia's implementation of libvdpau has some bugs and the videos are all having strange rendering problems. If I remove the link (and hence libvdpau stops being used) everything works fine. I think that can be resolved by using the 32 bit version of libvdpau from the repositories.

Do you know how to install a 32 bit lib in a 64 bit system from the repository?

---

### Post by vipseixas on 2010-12-03
> **vipseixas said:**
> 
Do you know how to install a 32 bit lib in a 64 bit system from the repository?

Just found how, first I installed getlibs as explained here:

[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

And then used the command:

```

sudo getlibs -p libvdpau1

```

And now I csn play Youtube videos with 1080p quality!

---

### Post by ZedThou on 2010-12-03
Edit: comment redacted as it wasn't needed, or nearly as satisfying as the already found solution above

---

### Post by ZedThou on 2010-12-03
Thanks vipseixas, I think yours is a better general solution. I don't know why the rendering differences are there, but this isn't the first time I've seen someone mention it. I'll have to update the first post on this page to suggest getlibs instead of the symbolic link.

---

### Post by theophile on 2011-02-08
Is the limitation of "stage" video only because of nspluginwrapper or would that be the case even running it "natively" in a 32-bit browser? In other words, is there a tradeoff for running flash this way rather than just biting the bullet and using a full 32-bit install?

---

### Post by thecapsaicinkid on 2011-02-09
Anyone done the same in Chromium?

---

### Post by ZedThou on 2011-02-09
As for Stage Video, it's up to the content providers to utilize the API. Most flash content doesn't. For instance, I think youtube is moving that way but I really don't know what percentage of their videos do so. My impression is that it's still a very small portion.

---

### Post by thecapsaicinkid on 2011-02-09
Do you have a link, the link for 64bit just redirects back to the 32bit page.

---

### Post by ZedThou on 2011-02-09
> **thecapsaicinkid said:**
> Do you have a link, the link for 64bit just redirects back to the 32bit page.

You're right, the one I got was the 32-bit version rather than 64. I've edited my previous post to remove all the misleading nonsense.

---

