---
title: "Ubuntu hangs at startup after installing Nvidia drivers"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Spazghost on 2009-04-28
Hi all,

I am running Ubuntu 8.10 and have 2 8800GT's in SLI.

I activated the Nvidia restricted drivers by going to system administration and the hardware drivers option, after first making sure I had the linux headers and source installed.

It seemed to install fine so I rebooted, however upon rebooting it seems to hang at what looks like a commandline prompt, with the last line of text something like "Checking battery", and it doesn't go any further.

I am able to press ctrl-alt-f1 at this point and drop into command line, so I believe it is trying to start X server but is failing to.

I was able to reboot to an older version kernal, and was able to get in fine. Once I was in, it told me the nvidia drivers were activated. However, after restarting again, I am getting the same thing with that version of the kernal as well. Which leads me to believe the problem is with the nvidia drivers.

Is there anyway for me to deactivate the restricted nvidia drivers from command line :confused:, or have I bricked another ubuntu install :(...

Any help would be greatly appreciated, as I'm a bit of a linux noob and am trying to move over to linux to use as a development workstation.

---

### Post by Spazghost on 2009-04-28
Small update.

I was able to determine how to deactivate the nvidia restricted drivers by doing this:

```
sudo aptitude purge nvidia-glx-180
sudo dpkg-reconfigure -phigh xserver-xorg
```

After doing that and rebooting, it no longer hangs at checking battery state, but instead gives me a message like:

kinit: no resume image found, doing normal boot

And from there it drops to the command line login. :confused::confused::confused:

---

### Post by Spazghost on 2009-04-28
Bump

Still having this issue, not sure whether the kinit issue I have now is related or whether I messed something up.

Idk maybe the nvidia restricted driver doesn't like SLI :(

---

### Post by EKwisnek on 2009-04-28
I'm having much of the same problem, just a different system configuration. I have an HP Laptop with an NVIDIA card on board. I had been using the (I believe) the 177 restricted driver with no problems. Last night I updated to the recommended 180 driver. Upon rebooting, the display simply goes black after logging in. I know it's just the video because if I press the power button, which I have configured to prompt me to restart, shut down, hibernate, etc. I can use the arrow and enter keys to select and execute.

So...my question would be how can I "roll back" the driver...to the 177 or even the non-restricted driver prior to boot?

Thanks,
Evan

---

### Post by Spazghost on 2009-04-28
I was able to find a solution.

I reinstalled with 9.0.4, and activated nvidia-glx-180, and had the same issue as before with it hanging on the checking battery status.

I was able to solve it by following [this]("http://ubuntuforums.org/showpost.php?p=7105138&postcount=5")

:)

---

