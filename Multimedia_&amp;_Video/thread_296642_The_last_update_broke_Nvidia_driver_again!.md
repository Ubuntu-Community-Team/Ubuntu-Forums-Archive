---
title: "The last update broke Nvidia driver again!"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by slugkilla on 2006-11-09
It seems all my posts concern the Nvidia driver and the many ways that it can break. Too bad it can't be fixed the same way! So here is the deal. I updated a few days ago and restarted today to find that my nvidia driver had broke. I  tried to purge the linux-headers stuff and reinstall the driver from repos and the linux-headers. This did not work. I have Dapper BTW. Can someone tell me the steps I need to take to do this? I'll check back tomorrow night. Thank you

---

### Post by tseliot on 2006-11-10
> **slugkilla said:**
> It seems all my posts concern the Nvidia driver and the many ways that it can break. Too bad it can't be fixed the same way! So here is the deal. I updated a few days ago and restarted today to find that my nvidia driver had broke. I  tried to purge the linux-headers stuff and reinstall the driver from repos and the linux-headers. This did not work. I have Dapper BTW. Can someone tell me the steps I need to take to do this? I'll check back tomorrow night. Thank you

1) can you post the output of this command?
```
uname -r
```

2) how did you install the nvidia driver?

---

### Post by bmt on 2006-11-10
This worked for me:

Boot into recovery mode from GRUB.  Then:

```
sudo dpkg-reconfigure xserver-xorg
```

I selected 'nvidia' for the driver and default for everything else.  Rebooted and all was well.

If that doesn't work, try here: [http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177) for a more comprehensive guide to recovery.

---

### Post by slugkilla on 2006-11-10
uname -r
2.6.15-27-386

I orginally installed the driver from their site, then I figured out how to get rid of it and use the repos. But something went wrong I guess. Thanks for trying to help me out. Any Idea on how to make it work? I'm using the "nv" driver for now.

P.S. The error I'm getting is talking about a missmatch between driver versions. If the repos's updates break it, should I just reinstall with Automatix2?

---

### Post by slugkilla on 2006-11-11
Any ideas?

---

### Post by tseliot on 2006-11-11
Try Envy 0.7.1:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by slugkilla on 2006-11-11
WOW! Tseliot, you are the man. This is a very nice thing you have come up with. It makes things very easy to fix when this kind of thing happens. All I have to do is "sudo envy". The new driver has a really nice splash screen btw. Thanks again

---

