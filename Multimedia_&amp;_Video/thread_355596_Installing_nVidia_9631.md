---
title: "Installing nVidia 9631"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by Tim Butler on 2007-02-07
Hello,

   I'm trying to install Beryl on my system, which is an AMD64 with nVidia 7800 gtx. I find that when I  enable twinview that my beryl shatters (error 11). I read that I should install an older version of the nVidia driver, so I've downloaded

 NVIDIA-Linux-x86_64-1.0-9631-pkg2.run

 from the nVidia website. Of course if I try and run this in X the installer tells me that I can't; however I don't seem to be able to find the necessary runlevel to install this driver which is now sitting on my desktop. I've tried the envy installer but of course this just installs the latest version, which doesn't work for me. I know this is probably a very simple issue but I've been searching in vain for a while now. Any help would be greatly appreciated.

    Thanks a lot,

            Tim

---

### Post by iainmcc on 2007-02-07
Hey Tim

You need to get out of X completely. Hit CTRL-ALT-F1 which gets you to tty1, and log in there.

Then,

```
sudo /etc/init.d/gdm stop
```

(Or kdm if you're running KDE) to kill X.

Or, just follow tseliot's guide for installing nvidia drivers.

Iain.

---

### Post by Tim Butler on 2007-02-08
Ah, thanks a lot Iain - I hadn't realised that you had to stop gdm AFTER ctrl-alt-backspace, wondered why that wasn't working.

   Cheers,

         Tim

---

