---
title: "Can't record sound after updates"
date: 2011-09-24
forum: Multimedia Software
---

### Post by k.p.odoherty on 2011-09-24
Hi,
After installing a number of updates yesterday (unfortunately I can't remember which) I am unable to record sound using Sound recorder or Audacity. My assumption is that one of the updates messed with this.
I tried changing the settings in PulseAudio Volume control but to no avail.
I'm running 11.04 on a PackardBell laptop.
Please let me know what other information I need to provide to find out where the problem might be.

Many thanks,
Peter

ps. is it not a bit strange that Ubuntu should force me to install updates which directly affect the usability of certain programmes?

---

### Post by ajgreeny on 2011-09-24
If you can't remember what the updates were run the command ```
grep -w upgrade /var/log/dpkg.log
```which will list everything with date, time, package name and the old and new version numbers.

That might give a clue to what caused the problem.

---

### Post by k.p.odoherty on 2011-09-24
Thanks a lot for that.

This is the output. I can't see anything that is relevant to the problem though. Can you?


2011-09-20 16:53:25 upgrade dpkg 1.16.0~ubuntu7 1.16.0~ubuntu7.1
2011-09-20 16:53:41 upgrade tzdata 2011g-0ubuntu0.11.04 2011j-0ubuntu0.11.04
2011-09-20 16:53:47 upgrade dpkg-dev 1.16.0~ubuntu7 1.16.0~ubuntu7.1
2011-09-20 16:53:49 upgrade libdpkg-perl 1.16.0~ubuntu7 1.16.0~ubuntu7.1
2011-09-20 16:53:51 upgrade libavutil50 4:0.6.2-1ubuntu1 4:0.6.2-1ubuntu1.1
2011-09-20 16:53:52 upgrade libavcodec52 4:0.6.2-1ubuntu1 4:0.6.2-1ubuntu1.1
2011-09-20 16:53:54 upgrade libavformat52 4:0.6.2-1ubuntu1 4:0.6.2-1ubuntu1.1
2011-09-20 16:53:55 upgrade libpostproc51 4:0.6.2-1ubuntu1 4:0.6.2-1ubuntu1.1
2011-09-20 16:53:56 upgrade libswscale0 4:0.6.2-1ubuntu1 4:0.6.2-1ubuntu1.1
2011-09-21 18:37:48 upgrade linux-image-2.6.38-11-generic 2.6.38-11.48 2.6.38-11.50
2011-09-21 18:38:03 upgrade linux-image-2.6.38-11-generic-pae 2.6.38-11.48 2.6.38-11.50
2011-09-21 18:38:16 upgrade python-problem-report 1.20.1-0ubuntu5 1.20.1-0ubuntu5.1
2011-09-21 18:38:18 upgrade python-apport 1.20.1-0ubuntu5 1.20.1-0ubuntu5.1
2011-09-21 18:38:19 upgrade apport 1.20.1-0ubuntu5 1.20.1-0ubuntu5.1
2011-09-21 18:38:22 upgrade apport-gtk 1.20.1-0ubuntu5 1.20.1-0ubuntu5.1
2011-09-21 18:38:23 upgrade linux-headers-2.6.38-11 2.6.38-11.48 2.6.38-11.50
2011-09-21 18:38:41 upgrade linux-headers-2.6.38-11-generic 2.6.38-11.48 2.6.38-11.50
2011-09-21 18:38:49 upgrade linux-libc-dev 2.6.38-11.48 2.6.38-11.50
2011-09-23 18:59:37 upgrade nvidia-common 0.2.30 0.2.30.1
2011-09-23 18:59:39 upgrade apt 0.8.13.2ubuntu4.1 0.8.13.2ubuntu4.2
2011-09-23 18:59:51 upgrade apt-utils 0.8.13.2ubuntu4.1 0.8.13.2ubuntu4.2
2011-09-23 18:59:52 upgrade apt-transport-https 0.8.13.2ubuntu4.1 0.8.13.2ubuntu4.2
2011-09-23 18:59:54 upgrade flashplugin-installer 10.3.183.7ubuntu0.11.04.1 10.3.183.10ubuntu0.11.04.1
2011-09-23 18:59:56 upgrade libqtgui4 4:4.7.2-0ubuntu6.2 4:4.7.2-0ubuntu6.3
2011-09-23 18:59:58 upgrade libqt4-dbus 4:4.7.2-0ubuntu6.2 4:4.7.2-0ubuntu6.3
2011-09-23 19:00:00 upgrade libqt4-xml 4:4.7.2-0ubuntu6.2 4:4.7.2-0ubuntu6.3
2011-09-23 19:00:01 upgrade libqtcore4 4:4.7.2-0ubuntu6.2 4:4.7.2-0ubuntu6.3

---

### Post by .... on 2011-09-24
Kernel update probably did it. Boot into the old kernel and see if that works.

---

### Post by k.p.odoherty on 2011-09-24
Thanks. Can you tell me how to boot into the old kernel?

---

### Post by .... on 2011-09-24
Hold shift when you start booting to get to the GRUB menu.

---

