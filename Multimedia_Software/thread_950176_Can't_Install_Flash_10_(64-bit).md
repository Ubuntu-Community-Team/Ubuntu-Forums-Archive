---
title: "Can't Install Flash 10 (64-bit)"
date: 2008-10-16
forum: Multimedia Software
---

### Post by HDTimeshifter on 2008-10-16
I followed these instructions to install Flash:  [http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-3]("http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-3")

Everything looks ok with the 1st command, but the 2nd command fails with:
E: Couldn't find package adobe-flashplugin

---

### Post by aysiu on 2008-10-16
Usually you can just visit a website requiring Flash and then follow the *Install Missing Plugins* prompts as you can see here: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

But if you go to the Adobe website, download the .deb for Ubuntu and just double-click the .deb

---

### Post by HDTimeshifter on 2008-10-17
I'm not familiar with .Deb - that's why I tried to use the APT.

I just tried the .deb for Ubuntu 8.04+, but the package manager gives me the following:  "Error:  Wrong architesture 'i386'  Does Flash not work on 64-bit Ubuntu?

Ok, it took a bit of digging to find out:  "Adobe Flash Player is not supported for playback in a 64-bit browser. However, you can run Flash Player in a 32-bit browser running on a 64-bit operating system."  They had no mention of this in their system requirements specs.

---

### Post by aysiu on 2008-10-17
Didn't realize you were using 64-bit. I've retitled the thread.

---

### Post by HDTimeshifter on 2008-10-17
[Link to thread on how to install 32-bit Firefox in 64-bit Ubuntu]("http://ubuntuforums.org/showthread.php?t=202537")

---

