---
title: "No video at startup Ubuntu 9.10"
date: 2010-05-24
forum: Multimedia Software
---

### Post by GROwen on 2010-05-24
Hi all,

I've run into a problem with the video not displaying after the Ubuntu logo screen. 

I installed Boxee which had a few dependencies that I needed to install, for some weird reason they were pkgs that had more recent updates already installed but I figured it better to use the pkgs Boxee was suggesting. I installed these and had no issues using the system with Boxee until I went and installed the suggested updates via the update manager, which I think included the superseded pkgs that I'd replaced with the earlier versions (round and round we go).

I was using a tv as a primary output which worked fine up until that point.

On restart there was no video from when the splash screen/login screen appears. I restarted with another monitor attached and it worked ok, then I looked at settings for the monitors, saw that the TV was disabled, enabled it as separate, shut down, unplugged the monitor, started up, same problem. Plugged the monitor back in and now it's suffering the same problem.

Disappointingly I didn't take note of what the updates were. Now I have no idea how I can try and correct the issue without doing a complete reinstall.

Hope someone can help from this ramble.

Thanks in advance.

---

### Post by frozonecom on 2010-05-24
try doing this:

```
System>>Administration>>Synaptic Package Manager
```

then go to:

```
Edit>>Fix Broken Packages
```

then go to terminal and type this.

```
sudo shutdown -r 0
```  
--that code is for reboot.

see if anything changed after reboot.

---

### Post by GROwen on 2010-05-24
Thanks for the tip Frozonecom but no video is displayed after the initial Ubuntu logo splash screen. Once it fades out there's no signal input to either monitor (monitor or tv) so I can't interact with the machine at all.

Is there a way to get it to boot into command line, and issue commands to start the Fix Broken Packages program?

---

