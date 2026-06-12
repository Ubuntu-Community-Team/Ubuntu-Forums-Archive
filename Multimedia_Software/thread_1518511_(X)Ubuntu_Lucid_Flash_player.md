---
title: "(X)Ubuntu Lucid Flash player"
date: 2010-06-26
forum: Multimedia Software
---

### Post by elfarto on 2010-06-26
Hi,

I'm having a proble with my flash player, it's eating my cpu: when i use the "top"-command, i can see that my google chrome or firefox is using MORE than 100% of my cpu just playing a youtube video.
I've been googling for some days to find a solution and tried many different versions of adobe's flash player.
I know I can use downloadhelper or watch the videos from my tmp-folder, but it's really the only thing which is bothering me about (X)Ubuntu.
I tried to update my kernel, I'm now on version 2.6.35-rc3
I'm on a eee pc 1000H using Xubuntu or Ubuntu lucid (I'm having the same problem in both of them) which has a Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03).
I'm currently using the standard i915 driver, I tried looking for different drivers, but I don't think they are causing the problem, I think it's only related to adobe's flash player.

Could anybody please help me?

---

### Post by lovinglinux on 2010-06-27
See my [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) tutorial.

For more Firefox tweaks and tips see [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)
For additional support see [Firefox Optimization and Troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by elfarto on 2010-06-30
Thanks for you reply.
I tried everything (more than once :s), except changing the x.org-file, because it opens an empty file (if I'm not mistaken I read they changed it in lucid?)
Maybe it's a video driver issue? I'm on a eeepc 1000H. For youtube I use the awesome greasemonkey scripts but I'm using a lot of different flash websites so it's not really a solution.
Any ideas are always welcome, I'm quite desperate, I love ubuntu, but this flashthing is really killing me!

---

### Post by lovinglinux on 2010-06-30
> **elfarto said:**
> Thanks for you reply.
I tried everything (more than once :s), except changing the x.org-file, because it opens an empty file (if I'm not mistaken I read they changed it in lucid?)
Maybe it's a video driver issue? I'm on a eeepc 1000H. For youtube I use the awesome greasemonkey scripts but I'm using a lot of different flash websites so it's not really a solution.
Any ideas are always welcome, I'm quite desperate, I love ubuntu, but this flashthing is really killing me!

[FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/161869). Still support only 3 sites, but I will add more soon.

---

### Post by Yellow Pasque on 2010-06-30
You might want to try the latest intel driver, though I wouldn't hold my breath expecting it to make Flash fast (it's still slow on my RadeonHD4550 with open-source driver): [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
You can always revert the change using ppa-purge package from that repo.

---

### Post by elfarto on 2010-06-30
Thanks to both for your input.
I installed the ( [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")) intel-drivers (not the bleeding-edge ones, I prefer my netbook in one piece),
but when i put the lshw -c display command, my driver still seems to be the i915-one.
How can I set it to the driver I just installed?
Thanks in advance!
__

---

### Post by Yellow Pasque on 2010-06-30
It's the same driver, just an updated version.

---

