---
title: "Unable to ppa:purge"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by GreenRaccoon on 2011-04-30
I've got Natty Narwhal.  I just installed ppa:nvidia-vdpau/ppa.  However, I tried to sudo apt-get update and I got this:

```
W: Failed to fetch http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I figured it was just a faulty ppa so I tried a "ppa:purge" (that's supposed to be ": p" without the space in between) but I get the same error.  At the end it says:

```
Warning:  apt-get update failed for some reason
PPA to be removed: nvidia-vdpau ppa
Warning:  Could not find package list for PPA: nvidia-vdpau ppa
```

I double-checked my /etc/apt/apt.conf file and it looks fine.  It reads:

```
Acquire::http::proxy "false";
```

I'm out of ideas.  Anyone else have one?

---

### Post by GreenRaccoon on 2011-04-30
Never mind, I got it all figured out.  Apparently the ppa I installed was just for older versions of Ubuntu, so I installed the newer one.

As for removing the faulty ppa, I still couldn't use ppa:purge, so I used Ubuntu Tweak.  For reference, here's a link to show how to install and use it:

[http://www.howtogeek.com/howto/29584/safely-remove-ppas-and-roll-back-to-stable-versions-in-ubuntu/]("http://www.howtogeek.com/howto/29584/safely-remove-ppas-and-roll-back-to-stable-versions-in-ubuntu/")

---

