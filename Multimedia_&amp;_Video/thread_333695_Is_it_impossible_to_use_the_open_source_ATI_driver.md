---
title: "Is it impossible to use the open source ATI driver with Radeon X300 SE??"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by ReyPeste on 2007-01-07
Hello all, I post after several days of browsing this forum for answers...

I know a lot of people have problems with the ATI drivers in Edgy.  The Dell Dimension comes with the integrated Intel 945 graphic card, which worked out of the box with no problems.  But the ATI Radeon X300 was another story.  When I use the default "ati" driver as suggested here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I get the common error "no screens found" and I can't even start X.
When I use the "workaround" (manually changing 'ati' to 'radeon' on xorg.conf) described here:

[https://wiki.kubuntu.org/EdgyKnownIssues](https://wiki.kubuntu.org/EdgyKnownIssues)

then I can start X but without direct rendering, and at startup monitor gives a warning "cannot display current screen resolution" even when I try much lower resolutions than the optimal for my monitor (1280x1024).

Finally I got the propietary driver fglrx (from the repositories) to work by disabling compositing by adding these lines to the end of xorg.conf

```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```

Now I can start X and also have DRI, but I would like to have the open source driver working, as it would allow me AIGLX and compositing.  Also I've been having lock-ups during shutdown and reboot, which may or may not be related to all this.  So if anyone has suffered through this same process (I've been editing and rediting xorg.conf for 3 days now), and has some advice on this, I would be eternally thankful.

---

### Post by Kubunteando on 2007-01-08
It seems that there is support for the X300 on the Open Source drivers (r300 driver).
But it may not be fully stable (as it appears as unstable). Check:

[http://dri.freedesktop.org/wiki/ATIRadeon#head-2f5098616350345fc8b9d26888cb729d63303cf2](http://dri.freedesktop.org/wiki/ATIRadeon#head-2f5098616350345fc8b9d26888cb729d63303cf2)

and

[http://bugzilla.freedesktop.org](http://bugzilla.freedesktop.org)

There are some bugs reported for the X300.

You can give a try and report to them if you find any issues.
They use to answer to the bugs quite nicely.

And you can always come back to the ATI proprietary drivers.
They are working on it, so sooner or later there will be stable support.

---

