---
title: "Screen refresh rate messed up"
date: 2008-12-19
forum: Multimedia Software
---

### Post by kratos2488 on 2008-12-19
Finally decided to install Ubuntu 8.10 on a 5 year old machine laying around my parent's house. I planned on hooking it up to my TV in my dorm room, and using it as a media server for my music and movies. However, I am having immense difficulty getting the computer to display properly on my TV (fyi, this is my tv [http://www.nextag.com/Sharp-Aquos-LC-26SH12U-543203081/specs-html](http://www.nextag.com/Sharp-Aquos-LC-26SH12U-543203081/specs-html)). I am pretty sure that the issue has to do with my graphics card. I believe that it is a Geforce 4 MX 440, so it is pretty old. When I first logged in after installation, it was displaying at 800x600, which was not a good enough resolution for me. I tried using the Hardware Drivers option under system management, and that found an Nvidia driver to install. I did that, and it bumped my resolution down to 640x480, which is unusable on my TV. Now, I have deactivated the driver, returning the resolution to 800x600, but when I was looking in the screen resolution window, I managed to change the refresh rate to a setting that my TV doesn't support. So now after login, I get a "No Signal" message on my TV. Is there anyway I can set the resolution without being able to look at the screen? Any advice would be awesome, and thanks in advance.

Note: I have also tried modifying the xorg.conf file, a trick that I learned about in other threads on these forums, and I put in there every compatible resolution with my TV, and none of them worked. I also tried obtaining the Nvidia driver through envyng, but that ran into the same 640x480 issue that I mentioned earlier.

---

### Post by overdrank on 2008-12-20
> **kratos2488 said:**
> Finally decided to install Ubuntu 8.10 on a 5 year old machine laying around my parent's house. I planned on hooking it up to my TV in my dorm room, and using it as a media server for my music and movies. However, I am having immense difficulty getting the computer to display properly on my TV (fyi, this is my tv [http://www.nextag.com/Sharp-Aquos-LC-26SH12U-543203081/specs-html](http://www.nextag.com/Sharp-Aquos-LC-26SH12U-543203081/specs-html)). I am pretty sure that the issue has to do with my graphics card. I believe that it is a Geforce 4 MX 440, so it is pretty old. When I first logged in after installation, it was displaying at 800x600, which was not a good enough resolution for me. I tried using the Hardware Drivers option under system management, and that found an Nvidia driver to install. I did that, and it bumped my resolution down to 640x480, which is unusable on my TV. Now, I have deactivated the driver, returning the resolution to 800x600, but when I was looking in the screen resolution window, I managed to change the refresh rate to a setting that my TV doesn't support. So now after login, I get a "No Signal" message on my TV. Is there anyway I can set the resolution without being able to look at the screen? Any advice would be awesome, and thanks in advance.

Note: I have also tried modifying the xorg.conf file, a trick that I learned about in other threads on these forums, and I put in there every compatible resolution with my TV, and none of them worked. I also tried obtaining the Nvidia driver through envyng, but that ran into the same 640x480 issue that I mentioned earlier.

Hi and welcome, I have seen issued with older nvidia graphic cards in Intrepid. You may try and boot into recovery mode and use the xfix option. Recovery mode is usually the second choice from the grub.
I might also suggest using Hardy 8.04 as the support is longer.

---

