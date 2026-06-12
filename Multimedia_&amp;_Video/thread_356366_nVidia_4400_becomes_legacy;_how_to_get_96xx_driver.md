---
title: "nVidia 4400 becomes legacy; how to get 96xx driver?"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by jejones3141 on 2007-02-08
I just upgraded, and found that the new nvidia-glx (1.0.9746+2.6.17.7-10.1-9746) no longer supports my nVidia 4400 card. Looking at nvidia's web site, I see that the 4400 is now old and considered legacy; the 96xx driver supports it. Alas, looking at the repository, nvidia-glx-legacy is 7184, which supports the *really* old nvidia cards. uname -a shows that I'm running 2.6.17-10-386 kernel. Do I have an alternative to either upgrading my card (would love to, but...) or living with nv? Thanks.

---

### Post by jejones3141 on 2007-02-08
The answer is on [http://nvidia.limitless.lupine.me.uk/;](http://nvidia.limitless.lupine.me.uk/;) there's a different repository for the 96xx driver, called stable-9631. It might be good to edit the nvidia/beryl instructions to mention this for those of us struggling along with nvidia cards that are kind of old but not ancient. :)

Oops...I just now tried it, and nvidia-glx is still 9746, and nvidia-glx-legacy is 7184. Drat. Spoke too soon.

---

### Post by jmsa on 2007-02-20
I upgraded without a warning to later realize that I cannot load nvida module anymore. My only solution was to download NVIDIA-Linux-x86_64-1.0-9631-pkg2.run from nvidia driver archive.

---

### Post by catanzag on 2007-03-05
You could also try [http://www.albertomilone.com/driver.html](http://www.albertomilone.com/driver.html) instructions; there there are precompiled deb of 9631 for Dapper (which worked fine for me!) and Edgy.

Edit: after a couple of day I updated to Edgy and something has gone wrong as 2.6.17 wasn't installed by default; after installing it manually, I upgraded 9631 to Edgy version but new driver it still worked only with 2.6.15 kernel (!), where it find the correct kernel module, while in 2.6.17 it found only restricted 8774 (and X doesn't start), that is something similar to what jmsa had as in previous post. I had not much time to investigate, I downloaded NVIDIA-Linux-x86-1.0-9631-pkg.run from nvidia driver archive and installed with method 2 as in [tseliot guide]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_2") and it worked fine.

---

### Post by inception on 2007-03-09
I have nVidia 4200 Ti, does this mean I need to run the legacy driver now? And if so, is 9631 the correct one?

[http://nvidia.limitless.lupine.me.uk/](http://nvidia.limitless.lupine.me.uk/) doesn't work for me at all, I tried downloading a driver from there yesterday too, gave me 200b/ps before it disconnected me...

If I do a apt-get install nvidia-glx-legacy i get this (and yeah, I've added the repo catanzag linked to) :
```
Unpacking nvidia-glx-legacy (from .../nvidia-glx-legacy_1.0.7184+2.6.17.12-1_i386.deb) ...
Setting up nvidia-glx-legacy (1.0.7184+2.6.17.12-1) ...

```

I guess that means it fetched the old one, how can I get the 9631 one?
Oh and by the way, Envy doesn't work for me either, if I use it X won't start up anymore :p says it can't compile the kernel...

Sorry if this post seems silly, but I'm not a very experienced user yet. ;)

---

### Post by catanzag on 2007-03-09
Hi inception, I think that you should use 9631 as 4400 is a GeForce 4 series.

I'm not at my Ubuntu box now, by if I well remember with [www.albertomilone.com](www.albertomilone.com) repo the driver is nvidia-glx. I mean after

```
sudo apt-get update
```

in synaptic you'll find the 9631 as an update of nvidia-glx, so you can update as

```
sudo apt-get install nvidia-glx
```

to install it

---

### Post by inception on 2007-03-09
Ah, I've installed the normal nvidia-glx now and force-downgraded it to 9631. I've never done that before, didn't know it could be done. Very handy, thought I had to comment out all the other sources to get the old version, hehe.
Thank you for the quick reply!

Edit: 
To contribute some, I'll describe the exact prob. and how to solve it:
I made a fresh Ubuntu install, and tried to use the normal nvidia-glx package, but it didn't work, and I couldn't boot GUI.
Edited the xorg.conf to use the default driver in order to get back in
```
sudo nano /etc/X11/xorg.conf
```
Searched for "driver" until I reached the correct section, and changed driver = "nvidia" to driver = "nv"

I had the newest drivers, which evidentially aren't compatible with the GeForce 4-series. So, I went to Synaptics Package Manager, searched for "nvidia", found nvidia-glx, nvidia-kernel-source and selected Package=>Force from the menu, selected the 9631 version (must add the earlier mentioned repository), force-downgraded them both, then ran the Envy script, selected "install manually", selected Nvidia and the 9631 driver. 
I ran it, edited my xorg.conf file back from "nv" to "nvidia", rebooted and it worked!

---

### Post by catanzag on 2007-03-09
I'm glad it worked fine for you; I also had edit my previous post as I got a small problem with apt-get in case you have the same and need NVDIA pkg

regards and enjoy ubuntu!!!

---

