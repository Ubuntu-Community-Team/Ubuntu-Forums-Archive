---
title: "SMPlayer / MPlayer"
date: 2013-09-30
forum: Multimedia Software
---

### Post by huxley2 on 2013-09-30
Hi, everybody

I've been looking into downloading SMplayer and there's lot of the talk about it being a great "Front end for MPlayer". Does this mean I also have to d/l MPlayer to make smplayer function properly or will all be taken care of via Synaptic Package Manager?

Regards,

Hux

---

### Post by vasa1 on 2013-09-30
If you run **apt-cache show smplayer** or **apt-get install -s smplayer**, you'll see what else will be installed as *depends* and as *recommends*. Most likely, though, you'll already be having `mplayer`. You can check that using **dpkg --get-selections | grep "mplayer"**.

Synaptic PM, by default, installs recommends as well.

---

### Post by SeijiSensei on 2013-09-30
Installing smplayer brings in mplayer as a dependency if you do not already have it installed.  Just use "sudo apt-get install smplayer" or install it from a package manager.

---

### Post by huxley2 on 2013-09-30
Thanks, Vasa & Seiji. I used synaptic package manager and It's all installed and working fine. Also I looked up what "front-end" means so it's all clear now.

---

