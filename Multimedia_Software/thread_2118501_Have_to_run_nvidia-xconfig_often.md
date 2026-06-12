---
title: "Have to run nvidia-xconfig often"
date: 2013-02-21
forum: Multimedia Software
---

### Post by RobotJox on 2013-02-21
Hi, I have a weird problem - Often when Ubuntu gets upgraded I have to run this command to get a decent resolution in Ubuntu:

```
sudo nvidia-xconfig --mode=1920x1080
```

followed by a reboot.

Sometimes I even have to run it twice...

I'm guessing it might be a dual-monitor problem (I have 2 monitors)?
Nvidia settings show both my monitors correctly as far as I can see.

My card: Asus Geforce GTX 670
My 2 monitors: Benq G2420HDBL (both the same)

Any ideas on how to fix this or if not maybe just automate this command?

---

### Post by TheFu on 2013-02-21
> **RobotJox said:**
> Any ideas on how to fix this or if not maybe just automate this command?

This explains how to properly setup dual monitors on Ubuntu:
[http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver)

Since it is not using any Ubuntu commands, it should work with newer OS versions.

---

### Post by RobotJox on 2013-02-23
Thanks, but... that doesn't really help me. I have dual monitors set up and working. It is the resolution that fails after most updates. And using nvidia-config - twice sometimes -fixes the problem. Please read my original question. Any good way to troubleshoot this?

---

### Post by TheFu on 2013-02-23
> **RobotJox said:**
> Thanks, but... that doesn't really help me. I have dual monitors set up and working. It is the resolution that fails after most updates. And using nvidia-config - twice sometimes -fixes the problem. Please read my original question. Any good way to troubleshoot this?

The normal troubleshooting methods should work.
* what do the log files show? [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
* what does the config file have inside it? /etc/X11/xorg.conf

If you don't have an xorg.conf file, at every reboot, the driver is tasked with finding the resolution it thinks is best for your setup.  This may not be the resolution that you want.

After any kernel update, the DKMS tools should relink the video driver module to the new kernel, but if you installed that through a download and not through the package manager or a PPA, you have decided to handle that manually going forward.

I've assumed you are using the nvidia drivers, not the F/LOSS versions.

Anyway, I hope this helps in some way.

---

