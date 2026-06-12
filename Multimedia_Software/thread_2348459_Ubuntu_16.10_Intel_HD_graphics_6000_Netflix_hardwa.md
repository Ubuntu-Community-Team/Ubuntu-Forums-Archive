---
title: "Ubuntu 16.10 Intel HD graphics 6000 Netflix hardware acceleration"
date: 2017-01-04
forum: Multimedia Software
---

### Post by jwhitener on 2017-01-04
Goal:  Get Netflix running smoothly in Ubuntu 16.10 using Chrome or Chromium. 


Running Ubuntu 16.04 with the Intel HD 6000 graphics, Netflix ran smoothly using Chrome or Chromium.  After upgrading to 16.10, my hardware acceleration gpu support is now disabled (I am assuming that is the reason that Netflix is running poorly now.  But I do not know for sure, because I did not check chrome://gpu before upgrading to see if acceleration was working).  

So I assumed I should upgrade my Intel Graphics Driver.  On their website they did have a .deb for 16.10.  intel-graphics-update-tool_2.0.3_amd64.deb.     The update tool fails when it attempts to install pipelight.  On the pipelight website, it says that pipelight is disabled, and the last available download is for Ubuntu 16.04.   

Is there a solution that works for Netflix + Ubuntu 16.10? If not, is it hard to downgrade to Ubuntu 16.04?  Is that my only option?

---

### Post by deadflowr on 2017-01-04
Not sure about the gpu, but if you have chrome what do you need pipelight for?

---

### Post by jwhitener on 2017-01-04
Just tried this:  [https://linuxconfig.org/play-netflix-on-linux-with-firefox](https://linuxconfig.org/play-netflix-on-linux-with-firefox)

Video worked.  Sound did not.  Grr.

---

### Post by jwhitener on 2017-01-04
> **deadflowr said:**
> Not sure about the gpu, but if you have chrome what do you need pipelight for?

The intel driver installer .deb tries to install it.  I don't want it, but the 'update tool' won't finish successfully wihtout it.  I assume I need to install a newer intel driver so that Chrome can start using my hardware to accelerate video again.  

[https://01.org/linuxgraphics](https://01.org/linuxgraphics) - I downloaded the update tool.  RELEASED: INTEL(R) GRAPHICS UPDATE TOOL FOR LINUX* OS v2.0.3 , and this installer tried to install pipelight.  

Because after upgrading to Ubuntu 16.10, chrome://gpu/ in Chrome now says that all my hardware acceleration is disabled and Chrome no longer plays Netflix smoothly when in full screen mode.

---

### Post by jwhitener on 2017-01-04
I noticed that the intel driver update tool, the one that tried to install pipelight but failed, also added a source to the 16.10 driver.  But it fails because it has no key.

Fetched 3,650 B in 0s (5,429 B/s)
Reading package lists... Done
W: GPG error: [https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main) yakkety InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
W: The repository 'https://download.01.org/gfx/ubuntu/16.10/main yakkety InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

So now I'm trying to find the key.

---

### Post by jwhitener on 2017-01-04
Ok, found the key.  Installed the driver.  Still didn't work.  

Randomly found these steps for 15.10 (I'm on 16.10) but it worked.

chrome://flags 
Override software rendering list Mac, Windows, Linux, Chrome OS, Android
Overrides the built-in software rendering list and enables GPU-acceleration on unsupported system configurations. #ignore-gpu-blacklist
**Enable**

And lastly, don't ask me why, it only works if you launch Chrome like this:

/usr/bin/google-chrome --single-process

---

### Post by mc4man on 2017-01-04
the Intel updater has nothing to do with pipelight, not even remotely possible.
As far as "Video Decode: Hardware accelerated" in chrome, if you want it enabled then choose Disable in Flags

---

### Post by jwhitener on 2017-01-06
> **mc4man said:**
> the Intel updater has nothing to do with pipelight, not even remotely possible.
As far as "Video Decode: Hardware accelerated" in chrome, if you want it enabled then choose Disable in Flags

The intel updater clearly tried to install pipelight.  I had no options to check/uncheck it.  Download it and try it yourself.  The latest v2 updater does indeed try to install pipelight.  

Maybe it determined I tried to use it in the past and it was trying to update it or something.  I did have pipelight in my repository sources list, so maybe it read that?

So I'm clear, this file intel-graphics-update-tool_2.0.3_amd64.deb was the one I installed and it did try to install pipelight when I ran it.

edit: I re-ran the Intel updater and this time (after removing pipelight from my system completely) it did not complain or attempt to install pipelight.

---

