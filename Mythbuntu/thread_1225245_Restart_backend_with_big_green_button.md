---
title: "Restart backend with big green button"
date: 2009-07-28
forum: Mythbuntu
---

### Post by My Name on 2009-07-28
Hi Chaps,
I was reading a few threads about setting up buttons on remotes using lirc. One suggestion was to make the big green button stop and restart the fronend. Now that wouldn't be something I would be interested in, but it could be useful to use it to stop and restart the backend. I used to have a few problems with the backend dropping off, which i think I have remedied by using two sata drives instead on a sata and an ide drive.
Would it be possible to right a script to restart the backend and have it activated by the big green button?
If so, how so?

---

### Post by newlinux on 2009-07-28
One way you could do it is to use irexec. The only complicating matter will be root privileges needed to restart the backend. You could run irexec as root or modify your /etc/sudoers file. [http://ubuntuforums.org/showthread.php?p=7637603](http://ubuntuforums.org/showthread.php?p=7637603) gives your more info and you can search around. I use irexec to switch my frontends from running myth to XBMC and vice versa, and a couple of other things...

But if all you want to do is make sure mythbackend gets restarted when stopped, you might be interested in using something like monit:
[http://www.mythtv.org/wiki/StatusMonitoringHowTo](http://www.mythtv.org/wiki/StatusMonitoringHowTo)

I use monit to check a number of services every 30 seconds on all my machines and if they aren't running I have them restart them (and send me emails with status changes). It has other configuration options as well (like how many times to try restarting before giving up).

---

