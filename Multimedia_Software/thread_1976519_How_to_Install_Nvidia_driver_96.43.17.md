---
title: "How to Install Nvidia driver 96.43.17"
date: 2012-05-08
forum: Multimedia Software
---

### Post by jbocean on 2012-05-08
I upgraded from 10.04 to 12.04.

My graphics card is GeForce4 MX 420 
It worked ok in lucid and I was able to run Compiz.

But when I went to Synapse to install the driver [ Nvidia 96.43.17 ] for 12.04, I got a message that the package was broken. 

So I downloaded the driver from another website.
I extracted the driver to a folder I created in the Home file system.

[B]How do I install the driver and get 'Additional Drivers' to recognize and enable it.
[/B]

I want to be able to use Unity in 3-D.

Thanks - J

---

### Post by Tech226 on 2012-05-08
I recommend installing from the ubuntu repositories as follows:

```
sudo apt-get install nvidia-current
```

Then reboot, unless you need the subject driver for a particular reason...?

---

### Post by Yellow Pasque on 2012-05-09
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)

---

