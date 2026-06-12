---
title: "Gainward GeForce 6200 Issues"
date: 2005-12-27
forum: Multimedia &amp; Video
---

### Post by Havoc on 2005-12-27
Hello,

I recently bought a Gainward Pro/1460 (Or, In laymen terms, a Geforce 6200 128 MB DDR2 :p ), and after some trial and error, I got it to to work, first with Breezy's "nvidia-glx" 1.0.7667 drivers, and then with Nvidia's 1.0.8178 drivers (That work nicely).

Now, I'm having some issues with my graphics card, that I thought would be resolved with the newest drivers, but I was wrong.

To make a long story short, I'm having performance issues.Here's what "glxgears" reports:

```
4277 frames in 5.0 seconds = 855.400 FPS
4280 frames in 5.0 seconds = 855.975 FPS
4282 frames in 5.0 seconds = 856.284 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

These are the last three frame counts, an amount of frames I consider VERY lowly.My TNT2 32MB managed to pull about 1700 frames, and the TNT2 is 5 years old...

I know that glxgears is not to be considered as a "benchmark", but performance issues are seen elsewere as well.For instance, Doom 3 just barely manages to cope, even with the most conservative settings...

I'm not sure what causes these issues, and I'd be grateful if people could give me some possible pointers.

These are the last lines of "lspci":

```
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:02:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0221 (rev a1)

```

It seems that Breezy cannot identify the Graphics Card, even though "nvidia-settings" seems to work ok...I'm afraid that's the source of all my problems.

Also, I've enabled "glx" at "xorg.conf".

If there is anything you could suggest, please do it...I beg of you.... :( 

Thanks anyways. ;)

---

