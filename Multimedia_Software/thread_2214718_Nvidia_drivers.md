---
title: "Nvidia drivers"
date: 2014-04-02
forum: Multimedia Software
---

### Post by javierdl on 2014-04-02
Hi all,

I'm back with renewed energy to attempt for the 4th or so time to find the Nvidia drivers that will allow Blender to make use of the video card as its main "Compute Device" (to render).
This time I had to resort to reinstall Ubuntu 13.10 over the mess I had (should you know, I'll make a link to previous threads eventually).
I just installed the Nvidia driver number 304.88 (current), with the help of Synaptic. 
My questions are:
1. Since I used Synaptic to install it, can I safely assume that everything that was needed in terms of supporting files and settings was taken care of by Synaptic? 
1a. Or is there something else I'm supposed to do still?
1b. Am I supposed to restart the pc?
2. Right after installing the drivers, I proceeded to run Blender and see in its Preferences if I can select the video card as a Compute Device. No luck so far. Is this a valid test?
Btw,
3. Am I better off using Software & Updates/Additional Drivers to switch from one driver to another?

Thanks guys,

JDL

---

### Post by steeldriver on 2014-04-03
I think you may need the CUDA toolkit package (nvidia-cuda-toolkit) rather than just the nvidia driver package? 

[http://wiki.blender.org/index.php/Dev:2.6/Source/Render/Cycles/Building](http://wiki.blender.org/index.php/Dev:2.6/Source/Render/Cycles/Building)

---

### Post by javierdl on 2014-04-03
Hi steeldriver,

Thanks for the suggestion. But I already tried this:
[FONT=arial]CUDACasts Episode #5: Install CUDA 5.5 with a Linux Package Manager[/FONT]
[FONT=arial][http://devblogs.nvidia.com/parallelforall/cudacasts-episode-5-install-cuda-55-linux-package-manager/](http://devblogs.nvidia.com/parallelforall/cudacasts-episode-5-install-cuda-55-linux-package-manager/)

 The worst part was that even Bashing-om (!) could not help me [removing it.]("http://ubuntuforums.org/showthread.php?t=2204446") If you know how knowledgable and experienced Bashing-om is then this should give you an idea of how hard it is to remove this kit should you have to. 
The thing is, while installed, it still didn't enable Blender to use my video card :( - Unless of course, I never did install it correctly. At this point only God knows. Days ago I reinstalled Ubuntu to start with a clean slate.

But I can't blame you for thinking it would have helped. I thought the same thing. So thanks anyway :)

Btw, furthermore, I do recall have found the right drivers during my 1st week-try of Ubuntu, without the use of any Cuda kits. If I could only remember which drivers they were :(


JDL

[/FONT]

---

### Post by steeldriver on 2014-04-03
Have you tried installing the version of nvidia-cuda-toolkit from the Saucy repository? It is based on CUDA 5.0 rather than 5.5, but should be compatible with the 304.88 drivers which are also in the repo

[http://packages.ubuntu.com/saucy/nvidia-cuda-toolkit](http://packages.ubuntu.com/saucy/nvidia-cuda-toolkit)

[http://packages.ubuntu.com/saucy/nvidia-current](http://packages.ubuntu.com/saucy/nvidia-current)

---

### Post by javierdl on 2014-04-03
Mmm, interesting! No, I haven't.
I'll have a close look at this! 
Thanks a bunch steeldriver :)

JDL

---

