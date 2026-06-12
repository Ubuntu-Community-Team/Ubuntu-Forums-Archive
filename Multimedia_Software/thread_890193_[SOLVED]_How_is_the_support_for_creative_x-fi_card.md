---
title: "[SOLVED] How is the support for creative x-fi cards on linux`?"
date: 2008-08-14
forum: Multimedia Software
---

### Post by Nitrius on 2008-08-14
In the past, there was no way of getting Creative X-FI soundcard to work in linux, so one could get sound, if i remember right. Has this changed? Will i get sound with my Creative X-FI XtremeMusic in Ubuntu?


Edit: After installing Ubuntu and tried, I've found out that it works, so far only tried with OSS4

---

### Post by redsaz on 2008-08-18
For those that were searching the Internet and came to this page, what helped me (I'm using Hardy 8.04 AMD64) were these links:

[**Thread entry on compiling OSS 4.1**]("http://ubuntuforums.org/showthread.php?p=4893852#post4893852") However, using this link, I wasn't able to get hardware mixing or vmix working with my X-Fi Xtreme Music card, but at least sound works so that is something.

[**HowTo: Creative X-Fi: Ubuntu Forums**]("http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+soundblaster+x-fi+extreme+music")
[**Hardy 8.04 & OSS4 (Alternative to ALSA)**]("http://ubuntuforums.org/showthread.php?t=780961")

To get vmix working (and thus get audio playing from more than just one device) follow the advice from Taladel buried deep in [**this post**]("http://ubuntuforums.org/showthread.php?t=780961&page=33"):
> **Taladel said:**
> What happens is that OSS uses a module called vmix to handle multiple programs making sound at the same time. For some reason, vmix isn't attaching to the output, and at build 1016, the devs didn't include the overrides to make it attach. So instead, let's just do this: 
 
...

```
vmixctl attach /dev/dsp
gksudo gedit /etc/rc.local
```and add 'vmixctl attach /dev/dsp' to the end of the file.

Also, check out [this page]("http://4front-tech.com/forum/viewtopic.php?t=2792") where I try and work through this problem with one of the developers.

---

