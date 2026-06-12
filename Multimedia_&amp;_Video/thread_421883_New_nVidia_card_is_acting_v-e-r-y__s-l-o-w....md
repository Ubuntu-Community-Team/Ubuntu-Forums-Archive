---
title: "New nVidia card is acting v-e-r-y  s-l-o-w..."
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2007-04-24
Hi, all-

Thanks to help from this group, I just installed my new nVidia card (a GeForce 6200) to replace my ATI Radeon 9200.

I'm using the "nv" driver.

Unfortunately, it's acting exactly the same as my un-accelerated ATI.  I guess the system is ignoring the card's processor, because every time I move a window around, it brings my CPU to 100% ("both" CPUs; I have a hyperthreading 3.2GHz Pentium 4). Everything is terribly jerky and slow, 3-D screensavers go at about 1 frame per second, GLXGEARS reports 159 fps (but displays about a frame per second if that, and my old ATI used to register in the 1600-ish range).

Now I know this isn't how my nVidia card is supposed to look... anybody know what I should do to make it work for real? It's only a 6200 with 256MB of RAM, but it should be doing better than this for sure.

Thanks for any help you may have!

-Mark

---

### Post by hardyn on 2007-04-24
NV is an unaccellerated 2d driver, that in my mind isn't very good...

get the binary nvidia driver, there are lots of how-tos

---

### Post by RomeReactor on 2007-04-24
Hi. I also have a GeForce 6200. Feisty asked me to install the restricted drivers when I tried to enable Compiz (System-->Preferences-->Desktop Effects) right after a clean install. If you haven't done so, I recommend it as the easiest way to enable direct rendering on your Ubuntu. If you've already done that and still can't get rendering, then open Synaptic (System-->Administration-->Synaptic Package Manager) and search for **nvidia-glx-new** and install it; after it finishes, open a terminal (Applications-->Accessories-->Terminal) and enter this

```
sudo nvidia-glx-config enable
```

after that finishes, restart your computer and you should have acceleration now.

Note that the **nvidia-glx-new** package will install the 1.0.9755 drivers: The same offered as the latest through the [Nvidia]("http://www.nvidia.com/object/unix.html") site!

---

### Post by mjpatey on 2007-04-24
Thanks, folks!

Rome, I actually happened across this solution just moments after posting.  An amazingly easy way to get the job done!  I do have acceleration now, and the built-in Compiz is working just fine.

So, is this driver the same as the "nVidia proprietary driver" that people here talk about, or is that another animal altogether?

-Mark

---

### Post by hardyn on 2007-04-24
same thing...

you may here it referred to as 

nvidia, nvidia-prorietary, nvidia-blob, nvidia-binary, etc... all the same thing... being they are a closed source driver.

---

