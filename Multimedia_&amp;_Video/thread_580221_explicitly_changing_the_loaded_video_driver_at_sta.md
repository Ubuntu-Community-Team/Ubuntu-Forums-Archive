---
title: "explicitly changing the loaded video driver at startup"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by hosk on 2007-10-18
I've been hunting on the internet for a while, and through a myriad of problems narrowed down my working solution to simply changing the loaded driver at startup from "nvidia" to "nvidia_new".  I have come to this conclusion because X fails at startup but through a simple,
```

sudo rmmod nvidia
sudo modprobe nvidia_new

```

I have a perfectly working X server. Any help would be fantastic, thanks!

---

### Post by nzadLithium on 2007-10-18
I'm assuming your question is how to get it do this automatically??

Ubuntu should load the driver you installed automatically which makes me think for some reason you installed both??

go into synaptic package manager.

uninstall nvidia-glx.

then reinstall nvidia-glx-new

(just incase anything went funny somehow)

See if that gets it to work.

If that fails then a solution which should work no problems but seems a stupid way to do it would be to run (im assuming your using gnome)
gksudo gedit /etc/rc.local

add add your two commands to the bottom of that.

Its a bit stupid to do that way though because it means it will still load the wrong one then it will unload it and load the right one :S

---

### Post by hosk on 2007-10-18
Hey! Thanks!! I used your stupid way as a temp-fix for a while(I just really want it up and running right now).  Now I can work on getting beryl and my DVI port on my video card to work. I'm a glutton for punishment!

---

### Post by hosk on 2007-10-18
Oh damn... I also just realized. nvidia-glx is already uninstalled, I marked it for complete removal but got an error.

---

### Post by nzadLithium on 2007-10-19
y don't u just install it again?

---

