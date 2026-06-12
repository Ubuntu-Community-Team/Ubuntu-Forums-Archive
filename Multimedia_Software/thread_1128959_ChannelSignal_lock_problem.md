---
title: "Channel/Signal lock problem"
date: 2009-04-18
forum: Multimedia Software
---

### Post by Chris_Smith on 2009-04-18
Hi Guys,

I have a problem when compiling a new kernel for ubuntu 8.04. The new kernel has had all support for unnecessary drivers and file systems removed, and boots up, and the system as a whole seems to run ok. However, when I try to run MythTV, I can't get a channel/signal lock. Also, xine_ui hangs when I select dvb. All the video drivers are present and correct, and udev has created /dev/dvb/adapter0 with all the required hooks. I have tested the video using tzap, and have found that by using tzap -r "channelname" in a tty, followed by cat /dev/dvb/adapter0/dvr0 > /root/tmp/tmpfile.mpg in another tty, that the resulting mpg file is faultless, and can be played using xine_ui. Also, mythfilldatabase runs, and updates the database with the latest EPG data. By trial and error, I have found that if the File Systems > Inotify > Inotify in userspace option is deselected in the kernel both xine_ui and MythTV then work normally! So, it looks as if I have made an error when recompiling the kernel, and have deselected something that Inotify is dependent upon. The Inotify help doc doesn’t refer to any dependencies, so I am at a loss as to know what additional kernel option(s) need to be selected in order to get the system running correctly with support for Inotify in userspace. Please note that this problem is not related to any particular kernel version, as I have tried several, including the current v2.6.29.1.

CS.

---

