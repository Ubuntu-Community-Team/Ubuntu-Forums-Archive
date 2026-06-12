---
title: "High pitched sound by HDMI on Kubuntu 14.04"
date: 2014-05-10
forum: Multimedia Software
---

### Post by soul3 on 2014-05-10
Hello!
I have the problem written in the title.

This is the result of ALSA Information Script.
  [http://paste.debian.net/plainh/4cc082fc](http://paste.debian.net/plainh/4cc082fc)

  I have the same issue as seen in the following thread: [http://ubuntuforums.org/showthread.php?t=2185474](http://ubuntuforums.org/showthread.php?t=2185474)
  Does somebody have a hint? Thanks!

---

### Post by caclratm on 2014-07-12
Hi everyone,

Just to tell  you that I had the same problem with a fresh install of vanilla ubuntu 14.04, and I found a solution here
[URL="https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1256655"]https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1256655
[/URL]

> nb : for other noob like me, that'll save you the "how to" search :

    sudo gedit /etc/default/grub

replace

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

with

    GRUB_CMDLINE_LINUX_DEFAULT="i915.disable_power_well=0 quiet splash"

> after saving,

     sudo update-grub

Then just I just restarted my machine and everything was OK.

Hope this helps

---

