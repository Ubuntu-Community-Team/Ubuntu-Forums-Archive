---
title: "Video buffering problem"
date: 2009-10-20
forum: Multimedia Software
---

### Post by akand074 on 2009-10-20
Hello,
A few days ago I decided to give Opera a try, after installing it I had the first freeze up I have ever gotten in my history of using Ubuntu where I had to hold the power button to shut down. After that it seemed to work fine and then it got very buggy and other stuff started having problems. So I uninstalled opera and went back to Firefox, I just thought the speed dial was kind of neat. Anyways moral of the story ever since then no videos seem to buffer for me on ubuntu. Youtube always buffers 6 seconds exactly and then stops regardless of the video and other sites seem to start for a bit and it looks like its buffering and then the progress bar just jumps back and it stops. I don't see how the installation of opera really had anything to do with it, maybe the unsafe shut down. Either way, does anyone know what the problem could be? My desktop needs a clean up anyways so I was thinking I would reformat and reinstall ubuntu perhaps sometime soon, but in the mean time. Any help would be appreciated!
Thank you very much.

---

### Post by lovinglinux on 2009-10-21
You can get [Speed Dial](https://addons.mozilla.org/en-US/firefox/addon/4810) or [Fast Dial](https://addons.mozilla.org/en-US/firefox/addon/5721) extensions for Firefox. I have used Fast Dial for a long time, but now I consider Speed Dial the best option.

I think you could try to re-install Flash. Re-installing Firefox probably won't help, since most FF issues are related to corrupted user profiles. Nevertheless, since you were using Opera when the system crashed, it's unlikely to be a Firefox issue, unless Firefox was also open when you hard reset the machine. If this is the case, then you could try to create a new Firefox profile and test it.

Anyway, to reinstall flash run the commands below on a terminal:

```
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Also check the Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by akand074 on 2009-10-21
Thanks for the reply!
I tried both reinstalling flash and making a new profile and neither worked. I doubt its a firefox problem because I use Firefox 3.5 but I also have firefox 3.0 and the problem exists using either browser, and using opera before I removed it. When I play something using my laptop or my virtualization of windows it works fine. I wonder what it could be. Some file must have become corrupt but I wouldn't know where to start looking and if its even worth it. Thanks for the speed dial hint though! That makes things easier. And that optimization for firefox looks great I'll deffinately try to go through that soon. So I guess my best option would be to reinstall ubuntu?
Thank you very much for the help.

---

### Post by lovinglinux on 2009-10-21
> **akand074 said:**
> Thanks for the reply!
I tried both reinstalling flash and making a new profile and neither worked. I doubt its a firefox problem because I use Firefox 3.5 but I also have firefox 3.0 and the problem exists using either browser, and using opera before I removed it. When I play something using my laptop or my virtualization of windows it works fine. I wonder what it could be. Some file must have become corrupt but I wouldn't know where to start looking and if its even worth it. Thanks for the speed dial hint though! That makes things easier. And that optimization for firefox looks great I'll deffinately try to go through that soon. So I guess my best option would be to reinstall ubuntu?
Thank you very much for the help.

Well, re-installing Ubuntu will probably solve the problem. Do you have a separate home partition?

---

### Post by akand074 on 2009-10-21
Yes, I have a separate storage partition for all my data files and another partition for windows which I have not booted into in almost a year. So it is not that big of a problem, the only hassle is having to reinstall all the software, add the repositories find their keys again, repersonalizing everything which may take some time. I'll leave it for when I have time. I just wonder what had caused it. Oh well, not the worst problem I've faced haha, its just been annoying having to watch videos in my virtual machine where I can't even full screen. Thanks for all the help!

---

### Post by lovinglinux on 2009-10-21
> **akand074 said:**
> Yes, I have a separate storage partition for all my data files and another partition for windows which I have not booted into in almost a year. So it is not that big of a problem, the only hassle is having to reinstall all the software, add the repositories find their keys again, repersonalizing everything which may take some time. I'll leave it for when I have time. I just wonder what had caused it. Oh well, not the worst problem I've faced haha, its just been annoying having to watch videos in my virtual machine where I can't even full screen. Thanks for all the help!

You can [download/install all current applications at once](http://ubuntuforums.org/showpost.php?p=8113316&postcount=3). Since you have a separate home, then most of your personalizations will be preserved.

---

### Post by akand074 on 2009-10-21
Oh man. Linux continues to impress me! If only I had known the the past 3 or 4 times I reinstalled it. This simplifies everything quite a bit! Thanks a lot!

---

### Post by lovinglinux on 2009-10-21
> **akand074 said:**
> Oh man. Linux continues to impress me! If only I had known the the past 3 or 4 times I reinstalled it. This simplifies everything quite a bit! Thanks a lot!

Yep, that is really handy ;)

---

### Post by akand074 on 2009-10-22
New kernel in the updates today fixed the problem!! Looks like I don't need to reinstall linux. Though I learned some new things like optimizing firefox more then I already have and the whole backup of all your installed software so they can all reinstall at once. Haha I still wonder what the problem was, I bet it was the bad shutdown and the new updates fixed it.

---

