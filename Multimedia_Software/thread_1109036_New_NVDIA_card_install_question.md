---
title: "New NVDIA card install question"
date: 2009-03-28
forum: Multimedia Software
---

### Post by Gatch on 2009-03-28
I'm running a Heron machine with an onboard Realtek card. The question is: Anything I need to look out for before the install? Driver issues, etc? It is listed in the binary driver list.

I plan to run TwinView with s-video adapter to a crt tv to watch Hulu, streaming, etc. (I know, I'm cheap. I'm a teacher)

My machine has been running flawlessly since FF. This is my first post, so although I've been around Ubuntu for a while I'm still a newb.

Any input would be greatly appreciated.

Gatch

---

### Post by norwoods on 2009-03-28
there will be newer nvidia drivers that are not in the heron repository but if you are happy with what is available, that is not a problem.  
run gksu nvidia-settings in a terminal window to get the gui for twinview setup.

---

### Post by Gatch on 2009-04-09
> **norwoods said:**
> run gksu nvidia-settings in a terminal window to get the gui for twinview setup.

I've installed the driver for the card. But nothing happens when I try to activate the settings. I can activate it in the "hardware driver" section.

The installation guide mentioned it may not work if you manually installed a previous driver. I did that with the Realtek. Could this be the problem?

The guide suggests removing the old driver, but I'm not sure how to do that.

Any ideas?

---

### Post by Gatch on 2009-04-10
I was able to fix it using this thread.

[http://ubuntuforums.org/showthread.php?t=780425&highlight=low+screen+resolution&page=2](http://ubuntuforums.org/showthread.php?t=780425&highlight=low+screen+resolution&page=2)

Apparently there is an issue with the GeForce 6200 card that I bought. But everything is working great now, thanks to the Forum! :p

---

