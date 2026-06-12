---
title: "X60S Intel-HDA ICH7 Sound again!"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Xavi pintant on 2007-07-10
I installed Wine on my Ubuntu Feisty on IBM-lenovo X60s, and
after reboot, sound never worked again.

I tried to activate and to hide modem on the bios. I tried to stop
machine, take off battery, wait 10s, put battery again, and boot
without the power cable connected... and i tried lots of things from
ubuntuforums. I reinstalled feisty and sound doesn't work.

I used alsa-info.sh script, here is the result:

[http://pastebin.ca/610317](http://pastebin.ca/610317)

After a thread on alsa-devel list:

[http://mailman.alsa-project.org/pipermail/alsa-devel/2007-July/001922.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2007-July/001922.html)

They provided me a patch, it worked! now we are talking about if it's something related to my bios or if affects other people. Anyone noticed the same?

[http://mailman.alsa-project.org/pipermail/alsa-devel/2007-July/001939.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2007-July/001939.html)

---

