---
title: "How to start with monitor off"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by linfidel on 2007-05-22
I've had this problem with several distros and both Nvidia and ATI cards.  I have a GeForce2 MX 400 now.

If I start up with the monitor off or disconnected (it's on a KVM switch), then it will start in low rez VGA mode, and I have to reboot to get it back to hi rez.  I'd like to be able to stop doing this if possible - sometimes when I reboot the linux system, I want to switch to the other one instead of twiddling my thumbs.  

Does anyone know a way to tell it a fixed resolution and not to try to dynamically change it?

Thanks (I hope).

---

### Post by guitarmaniac on 2007-05-22
If you just type Ctrl+Alt+Backspace it will restart X, this has worked for me so it should for you ;)

---

### Post by linfidel on 2007-05-23
> **guitarmaniac said:**
> If you just type Ctrl+Alt+Backspace it will restart X, this has worked for me so it should for you ;)
I haven't tried it, but it doesn't seem like it would work, as the problem arises before I start X; the resolution is low even at the grub startup screen - isn't this before x is run?  

I'm willing to try when I get home - maybe there's a misunderstaning on my part.

Thanks for the reply...

---

### Post by linfidel on 2007-05-23
> **guitarmaniac said:**
> If you just type Ctrl+Alt+Backspace it will restart X, this has worked for me so it should for you ;)
Well, when I got home, I purposely started up without the monitor, and was able to try your suggestion, and it worked.  It was very quick.  I am forever in your debt! :)

Thanks a lot for the suggestion.

---

### Post by guitarmaniac on 2007-05-24
no worries ;)
thats a bit weird that grub is in a low resolution as well...
oh well, at least it worked.

---

