---
title: "I player streaming"
date: 2009-07-29
forum: Multimedia Software
---

### Post by fidelandche on 2009-07-29
Hi,

   I have followed all instructions I Player in the guide to improve streaming on the BBC I Player but when in full screen the picture freezes for about a second or two before continuing and the picture can be choppy. Is there anything else I can do to improve this?

                     Many thanks

---

### Post by vinutux on 2009-07-29
Are installed ubuntu-restricted-extra, flash player, right graphic driver etc ?

---

### Post by igorzwx on 2009-07-29
I you do not really need IPlayer for some special purposes,
you may better make new installetion of Ubuntu and
other systems installed on your box.
Nobody knows what was installed together with IPlayer.

---

### Post by fidelandche on 2009-07-29
The flash player is installed, Ubuntu has  done a driver check and updated some. As for ubuntu-restricted-extra? what is that? The problems only come when in full screen mode.

---

### Post by AndyCee on 2009-07-29
> **fidelandche said:**
> The flash player is installed, Ubuntu has  done a driver check and updated some. As for ubuntu-restricted-extra? what is that? The problems only come when in full screen mode.

You can find that in the "Add/Remove Programs", or just type:

```
sudo apt-get install ubuntu-restricted-extras
```

in a terminal.

---

### Post by vinutux on 2009-07-29
ok no need to install restricted extras...iplayer is based on flsh

are you have same difficulty in youtube or other sites

---

### Post by jfernyhough on 2009-07-29
Flash is notoriously unreliable in Linux and its performance can depend on many factors.

First check you have the latest versions installed and loaded - type about:plugins into Firefox. If Flash isn't 10.0.27 then you need to check your installation.

You could also try a different browser - Opera works well.

If all else fails you could always install Air and the desktop client and download the episode.

---

### Post by igorzwx on 2009-07-29
This solution works well for me:

1. [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

2. [Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

### Post by issih on 2009-07-29
The main problem seems to be that flash can't use the gpu properly whilst compiz is on:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

Consequently, you are doing all the decoding in cpu, which when you blow up the scaling to require extrapolation to fullscreen can cause skipping if your cpu is a bit weedy and or if you have a big screen.

You could test if this is the problem by dropping to metacity (run "metacity --replace" and "compiz --replace" to return - do both of these in an alt+f2 pop up rather than a terminal) and seeing if things improve, although there are other problems to do with the gpu not being recognised and therefore utilised even in this scenario.

As a workaround, I use the zoom desktop plugin of compiz, to select the non-maximised flash window area and blow it up to fullscreen size using gpu features.

---

### Post by rannable on 2009-07-29
have you tried the iplayer clone for ubuntu? i think softpedia has it...[http://linux.softpedia.com/progDownload/get-iplayer-Download-46788.html](http://linux.softpedia.com/progDownload/get-iplayer-Download-46788.html)

---

### Post by fidelandche on 2009-07-29
I have downloaded the I player clone and installed the package, how do I get it to work?

---

### Post by fidelandche on 2009-07-29
> **vinutux said:**
> ok no need to install restricted extras...iplayer is based on flsh

are you have same difficulty in youtube or other sites

  Having the same problem in youtube as well but only when going to full screen. I have tried to install get-Iplayer but the terminal keeps telling me that errors have been found and it is unable to find the files or packages.

---

