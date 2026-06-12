---
title: "No Graphics Driver (Neither nouveau nor official)"
date: 2010-07-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by HalfEmptyHero on 2010-07-20
Right now I am unable to test Maverick since I can't get a graphics driver to work. With nouveau, I can't login; instead of the login screen a bunch of different colors, mostly green and purple, are spread out all over the screen. The proprietary driver also does not work, but I think that's a common problem right now.

My card is a GeForce GTS 360M. Anything I can try to do in order to get the nouveau driver to work?

---

### Post by ranch hand on 2010-07-20
You could try the xorg.edgers ppa.  You get a newer version of the OSS drivers from them.  They seem to be pretty good even if considered unstable.   I have to use them for the Unity desktop (10.10).

They make it possible for me to boot 10.04 with splash enabled (in about 62 seconds).

Might be worth a shot.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by HalfEmptyHero on 2010-07-20
Just tried it, but it didn't work. After rebooting I got the following message during the boot:

Conflicting fb hw usage Nouveaufb vs VESA VGA Removing generic driver

I got the same sort of messed up screen after that.

---

### Post by ranch hand on 2010-07-20
Bummer.  Beats me.

---

### Post by jppr on 2010-07-21
> **HalfEmptyHero said:**
> Just tried it, but it didn't work. After rebooting I got the following message during the boot:

Conflicting fb hw usage Nouveaufb vs VESA VGA Removing generic driver

I got the same sort of messed up screen after that.

I have that same. Nouveau has been broken almost 2 weeks. I have installed Nvidia-current and system works fine. I find this bug... [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614) This Nouveau problem start when grub2 updated last time

---

### Post by gacb on 2010-07-21
I get pretty much the same message while booting Maverick. but all that happens is that I need to re-enable desktop effects.

I have an onboard Intel driver on the laptop.

[   16.473164] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver

I also have a GeForce graphic card on my desktop and don't even bother testing Alphas anymore, as it's been an issue since Intrepid Alphas and every one since.

---

### Post by HalfEmptyHero on 2010-07-21
> **jppr said:**
> I have that same. Nouveau has been broken almost 2 weeks. I have installed Nvidia-current and system works fine. I find this bug... [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/605614) This Nouveau problem start when grub2 updated last time

The nvidia driver doesn't work either, it boots me into low resolution.

@gacb I am unable to enable the desktop effects because I can't log in graphically. The only thing I can do is go into safemode and log into the commandline. The problem with this is, ethernet doesn't work either (didn't work in Lucid, so not a Maverick problem) so it's very difficult to fix problems.

Also, my problem didn't start with any update, I am unable to even use the livecd. I am forced to install lucid and then upgrade to maverick.

---

### Post by cariboo on 2010-07-21
You should have to do this, but after you have installed the restricted nvidia drivers, open a terminal and type:

```
sudo nvidia-xconfig
```

the above command creates an /etc/X11/xorg.conf file. I,ve had to use it on a couple of my systems.

---

### Post by plun on 2010-07-21
```
sudo apt-get install --reinstall nvidia-current
```

is also a good way for removing the Nouveau crap.....;)

---

### Post by cariboo on 2010-07-21
When you install the restricted driver, it should blacklist the nouveau driver, so no need to remove it.

---

### Post by HalfEmptyHero on 2010-07-21
I did run nvidia-xconfig beforehand, and it still didn't work. I have had a little progress though, I removed the two packages xserver-xorg-video-nouveau and xserver-xorg-video-all. When I rebooted I got the low resolution error, but I'm actually running full 1920x1080 resolution now with the nouveau drivers. I can't enable desktop effects, but I'm okay with that for now until I can find a better fix.

---

### Post by jppr on 2010-07-21
> **HalfEmptyHero said:**
> I did run nvidia-xconfig beforehand, and it still didn't work. I have had a little progress though, I removed the two packages xserver-xorg-video-nouveau and xserver-xorg-video-all. When I rebooted I got the low resolution error, but I'm actually running full 1920x1080 resolution now with the nouveau drivers. I can't enable desktop effects, but I'm okay with that for now until I can find a better fix.

You don´t need remove those packages. I can´t understand why people do something first and ask after that. ASK FIRST AND DO THEN SOMETHING WHAT MUST TO DO

---

### Post by HalfEmptyHero on 2010-07-21
If you had read the thread, I did ask. I told them about my issues, but unfortunately the things they suggested did not work. So I removed those two packages, purely by accident really, and then was able to login. If you have any better suggestions, please feel free to tell me. But not only can I reinstall those packages at any time, I also turned an unusable system into a usable system. To me, that's a plus. Was it the best way to do it, probably not. Did it work, not completely but enough for me to actually use the system to attempt to fix it completely.

---

