---
title: "Older nvidia drivers with dapper?"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by Jfoard on 2006-07-02
Hello!

I recently upgraded from Breezy to Dapper and have encountered the following problem:  If I try to restart X, I'll get a black screen and have to hit the reset button, same goes if I try to get out of X with ctrl + alt + Fkey, I can get out but not back, it'll cause another crash.  

I'm pretty sure I've nailed the problem down to the new nvidia drivers that came with the upgrade, changing the 'driver' in xorg.conf from nvidia to nv will fix this, but I'd naturaly I'd rather use the nvidia drivers.

So, I tried to downgrade to my previous drivers (version 1.0.7667) using the older deb packages *but* the old nvidia-glx requires xserver-common, which now appears to be x11-common.  That sounded like the same item to me so I popped open that deb and switched the requirements to point at x11-common (which is probably where things went south).  After that I was able to install both the driver and kernel module packages without any trouble.

Upon trying to start X however, I get an error stating that the nvidia module does not exist.  I assume the root of the problem is back at the dependencies not being met, but I'm stumped.  I'll post relevant logs below.

Thanks!

[nvidia-bug-report.log]("http://www.mtwebsmiths.com/nvidia-bug-report.log")
[Xorg.0.log]("http://www.mtwebsmiths.com/Xorg.0.log")

---

### Post by gborzi on 2006-07-02
I have a similar problem on my amd64, where breezy worked (almost) fine but dapper is not working with the nvidia drivers. Using my laptop to login in the amd64, I discovered that with nvidia drivers, Xorg eats the cpu (almost 100% CPU is taken by Xorg) and doesn't display anything. If I kill it the screen becames black with some white stripes. I have come to a different conclusion on the reason of this misbehaviour: it's not the driver version but the new xorg. Why I say so ? Well, with the default breezy kernel (2.6.12) DMA didn't worked, so I compiled a 2.6.15 kernel and then installed the nvidia drivers 8178, and it worked fine. When I tried the same driver version in dapper, they gave the same problem of the prepackaged ones. Then I came to the conclusion that xorg it's guilty, or at least is seriously under suspicion, because it's the only software that changed from my previous installation (kernel: 2.6.15 on both, nvidia drivers 8178 on both).

---

