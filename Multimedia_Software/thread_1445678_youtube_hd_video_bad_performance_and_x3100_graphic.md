---
title: "youtube hd video bad performance and x3100 graphics card"
date: 2010-04-02
forum: Multimedia Software
---

### Post by xkalibur on 2010-04-02
I don't understand why HD youtube video has such poor performance in ubuntu. I have flash 10 installed but I am not sure if I am using the correct intel driver.  Video is clear but jittery and slow when 720 or 1080.

My laptop is a lenovo x61-tablet and I didn't have this problem in Vista or Win7.. 

I think it may be a driver issue so any suggestions on improving performance?

---

### Post by TheNerdAL on 2010-04-02
Did you update your drivers?

---

### Post by xkalibur on 2010-04-02
Well I ran apt-get xserver-xorg-video-intel package and it says I already have the newest version.

My question is more on what type of configuration I need to do or something to help improve the jittery performance.

thanks

---

### Post by 2hot6ft2 on 2010-04-02
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")
See the Troubleshooting section

---

### Post by xkalibur on 2010-04-03
> **2hot6ft2 said:**
> [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")
See the Troubleshooting section

I just did and there isn't anything regarding low performance with flash video.  My video plays and I can see it but it gets jittery in higher than standard def.  I should mention that this occurs while running Chrome too..

---

### Post by Riel on 2010-04-07
True. The same issue.

After loading the video (and bar is completedly red), pause it, then go to the /tmp folder and open the .flv file with totem.

It will play smooth.

So problem is in flash player.

---

