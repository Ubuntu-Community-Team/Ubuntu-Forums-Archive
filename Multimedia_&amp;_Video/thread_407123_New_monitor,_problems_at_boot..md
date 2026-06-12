---
title: "New monitor, problems at boot."
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by sevix on 2007-04-11
Hello,

I just got a widescreen monitor, and I updated my xorg.conf to have the correct refresh rates etc for my monitor.  I use Kubuntu and I went into the display properties and set it to 16:9 aspect ratio, and it told me I needed to reboot for it to take effect.  Right as I selected reboot, I noticed that it had selected a screen size and refresh rate for me (I had previously set it to the correct value, this was automatically changed and I can do nothing to change it back now, as I noticed it right as the machine was rebooting)  outside of the range of the monitor.  I do not have a monitor that CAN handle the refresh and resolution that was set.  SO now whenever I boot, my monitor just says that it can not display the resolution and refresh rate that its set to, and I can't do anything.  I safebooted in to the command line, and deleted the resolutions it had added as modelines in my xorg.conf that were incorrect, but how can I change the default resolution and refresh rate from a command line?
I'm kind of a newbie, so please any help would be appreciated, as I can not boot up my main computer anymore because of this, and do NOT want something like this to cause a reinstall, since fiesty is so close now, and would like to wait for the release version of that.

Thanks for any help in advance.

---

### Post by aidanr on 2007-04-11
"sudo dpkg-reconfigure xserver-xorg" should get you up and running again

---

