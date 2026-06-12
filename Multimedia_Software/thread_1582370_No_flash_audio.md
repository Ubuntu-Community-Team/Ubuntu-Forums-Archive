---
title: "No flash audio"
date: 2010-09-26
forum: Multimedia Software
---

### Post by not_online_now on 2010-09-26
Hello,

I recently installed Ubuntu 10.10 AMD64 beta. After installing the flash player, everything worked fine. I installed a few updates, as well as Ubuntu Stuido from the synaptic package manager, and when I rebooted, I can't hear any sound from flash content displayed in Fire Fox. All other sounds work fine, and I made another user account as a test, and that account has full audio functionality, including flash...  Any thoughts?

Thanks,
Steve

---

### Post by recallfx on 2010-09-26
Hi Steve,
I had the same problem as you, after some updates the sound from flash was gone. But you gave me some idea how to solve this.

I have deleted these folders from my user home directory to solve this:
.gstreamer-0.10
.pulse
.macromedia
.adobe
And these files:
.pulse-cookie
.cache/event-sound-cache.tdb.c10180bf1331982950b7a99700000011.x86_64-pc-linux-gnu

---

### Post by gavinschoch on 2010-09-26
I am having the same problem. I don't think deleting those files would help as it is not limited to one user account. Does this have anything to do with Adobe's new flash player 64 bit plugin. I am running 10.10 desktop beta. HTML5 audio and audio in all other applications works except for flash-based ones. This means it is not a problem with firefox or chromium, so therefore it is a problem with flash.

---

### Post by not_online_now on 2010-09-26
Okay, I'd first like to say that I can't believe how fast I got a reply! Secondly, it worked! I only have two more questions... First, what went wrong, and how did you figure out how to fix it?

Thanks again,
Steve

---

### Post by Yellow Pasque on 2010-09-26
If you've messed with the default audio configuration, you may need to do this: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by wojox on 2010-09-26
Check out [URL="http://flash-aid-extension.blogspot.com/"]FLASH-AID extension for firefox by lovinglinux
[/URL]

---

