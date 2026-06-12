---
title: "[Solved] ATI Radeon X300 Setup"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by dmacdonald111 on 2007-04-02
Hi all.

I've just returned back to Ubuntu after a bit of a break (really, I don't know why!) but I have.

Anyhoo, I thought it might be of interest and some use to some other people who may have the same setup, or similar, to me to know how I got my card working. It's pretty simple really...

1. Went to tseliot's website at: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

2. Clicked on the envy_0.9.1-0ubuntu4_all.deb link and selected 'Open'

3. Let it install everything it required and when presented with the Envy dialogue, selected 'Remove ATI Drivers

4. Once that finished, I selected 'Install ATI Drivers' - This downloads the driver from the ATI website so it may take a while if traffic is particularly slow

5. Once it was all set up, just allow it to reboot the system.

Once I was back in, I opened a terminal and typed;

```
fglrxinfo
```

which displayed;

[PHP]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)
[/PHP]

I then tested my fps;

```
glxgears -printfps
```

and got;

[PHP]9671 frames in 5.0 seconds = 1934.136 FPS
9767 frames in 5.0 seconds = 1953.290 FPS
9771 frames in 5.0 seconds = 1954.177 FPS
9771 frames in 5.0 seconds = 1954.049 FPS
9770 frames in 5.0 seconds = 1953.914 FPS
[/PHP]

Which is a LOT better than the 400 fps that I was getting before it was set up!

Thanks to tseliot for a great script!

Foxy

---

### Post by sdowney717 on 2007-04-02
Envy is so good it should be part of ubuntu natively.
It was the only way I got my ATI radeon 96000 to work in edgy.

Now I am stuck with feisty and no 3d.
Envy I hope he reconfigures to work with feisty soon.

---

### Post by dmacdonald111 on 2007-04-04
I seem to be having some problems (after me thinking all was well and fine).

I am getting the same fps as the last time I was using ubuntu, but for some reason, the screensavers such as antinspect and atunnel are running really slow and jumpy. Is there anyone who can shed some light on this for me? I never used to have problems before once the graphics card was set up.

TIA

Foxy

---

### Post by AlienX on 2007-04-09
After the ATI installation , I choosed yes for X auto-configuration and I restarted the computer , but after that X won't start anymore ... and my display remains black. Any idea on how to fix this ?

---

### Post by redboar on 2007-04-09
Since I'm at work I don't have time to find the exact posts but do a search on x300, find the posts on blacklisting the ati_agp and adding to xorg.conf the load=dri command with the extension to give DRI 0666 permission, then try again.  I had to borrow from a few different posts but with enough tweaking this is an issue that can be solved.  Good luck!

---

### Post by brama on 2007-04-16
> **AlienX said:**
> After the ATI installation , I choosed yes for X auto-configuration and I restarted the computer , but after that X won't start anymore ... and my display remains black. Any idea on how to fix this ?

I am facing the same problem. But I think X starts but Login screen doesnt appear. When I enter the Login name and pwd(Even when the display is blank), the next screen appears properly.:confused:

---

