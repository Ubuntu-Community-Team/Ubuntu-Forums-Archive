---
title: "Occasional NVidia Graphics Corruption (GeForce 8600 GT)"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by arekmenner on 2007-09-06
Hello! I have a GFX manufactured NVIDIA 8600 GT, and I am running Feisty (7.04). As far as I know, my graphics card is not supported in Feisty, so I manually installed the nVidia drivers from their website. The process went swimmingly (aside from some deal with dual display being cut off from the TV, but that's for a different post).

However, as far as I can tell, beginning from the last kernel upgrade, I have been getting occasional graphics corruption. It is the standard very regular green lines on the terminal and the pretty patterns in other places of odd colors reported by others. It only happens on some boots, and a reboot fixes it. I knew getting in that I would have to reinstall the drivers after every kernel release, which I did. I have a few of questions, however.

[LIST=1]
[*]How, specifically, should I reinstall the drivers after the kernel release? I may have done this step wrong as I simply purged everything that I had installed the first time and reinstalled it (aside from gcc libraries).
[*]Are there any diagnostic tools that I could run while there is graphic corruption to get a proper error message for which I could search for a solution?
[*]People have spoken of deleting all previous linux-image files aside from the most recent. Would this help my problem in any way?
[/LIST]

I would be willing to run any diagnostics and provide any additional information if it would help anyone in any way to fix this or other problems. Thank you.

---

### Post by w4ett on 2007-09-07
I have found the easiest method (for me)  is to use Envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I remove the nvidia driver modules using this from the terminal:

```
sudo envy -t
```

Upgrade to the new kernel, and then reinstall the Nvidia driver.  Envy also gives you the newest drivers available unlike the restricted drivers manager in Feisty.

Good Luck

---

