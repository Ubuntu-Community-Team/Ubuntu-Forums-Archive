---
title: "Fglrx, black screen of death."
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by llano on 2007-03-23
Hey all,

First of I'd like to say hello to everyone here on the Ubuntu forums. I've found these forums to be a great source of information for solving my problems as I undergo my first linux experience (down with Windows!).

My problem lies with getting my video card properly configured, or rather working as I would like. I was previously using the open source ati driver that comes with a vanilla Ubuntu installation. Everyone was running correctly, however, I was experiencing video lag whenever I moved, scaled, tabbed, or scrolled through open windows. As a previous Windows user and avid gamer, I'm used to having extremely smooth framerates and the video lag was driving me insane.

So I set out to get the closed source ATI drivers for my card. I followed the directions on [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) for manually installing the latest ATI fglrx driver. No problems with the installation, driver is running great, video lag problem I was experiencing is gone. Woot!

***BUT, I can no longer logout, switch to tty's, or restart the x server without getting a black screen of death ("check source and connection"). I'm completely clueless on where to begin solving this problem so I'm turning to the wise sages of Ubuntu for some help. Where do I begin?

Some info that might help diagnos the problem:
Distro: Ubuntu 6.10 x86_64
Kernel: 2.6.17-11-generic
Video: display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT
OpenGL version string: 2.0.6334 (8.34.8)

Any help is appreciated!

---

### Post by crispy_420 on 2007-03-23
I think as of right no there is no fix and it is a known bug with ATI's linux drivers. I have the same issue and if you ever find a fix let me know. I have done some searching for the solution, but all failed to work.

---

