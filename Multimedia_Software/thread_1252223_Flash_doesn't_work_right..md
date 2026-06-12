---
title: "Flash doesn't work right."
date: 2009-08-28
forum: Multimedia Software
---

### Post by DanielC on 2009-08-28
Hello. I recently bought a new computer and installed Ubuntu. For some reason Flash works very poorly in this computer (and it didn't in the old one). Video will often lose sound, or the image will freeze while the sound continues, or the image will look like a bunch of squares, etc.

You might recall that when you install new system, the first time you visit a page with flash Firefox offers you a list of possible plugins. I think I made a mistake in choosing the first option, which was the free/open source option. Maybe I should have gotten the proprietary one, I don't know. In any case, I went to Synaptic, I did a search for "flash" and I tried a few different packages that claimed to be a flash plugin. Some worked better than others, but none worked particularly well.

Oh, and another odd thing is that often (not always) when a page has Flash on it, rather than running, the browser shows a grey box with a an arrow for "play". So you have to click on the box to get the Flash running. This isn't how the usual flash plugin behaves and it is slightly annoying.

Long story short, does anyone know which flash and swf plugin(s) I should have installed on my computer to get the best viewing experience?

Thanks.

---

### Post by snowpine on 2009-08-28
Uninstall gnash and install flashplugin-nonfree.

```
sudo apt-get remove gnash && sudo apt-get install flashplugin-nonfree
```

---

### Post by lovinglinux on 2009-08-28
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by DanielC on 2009-08-28
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

Thanks!

I followed the instructions and it seems to have worked. I've only tested on a couple of youtube videos, but they played perfectly. That's the first time since I got this computer that Youtube works correctly. Thanks!

---

