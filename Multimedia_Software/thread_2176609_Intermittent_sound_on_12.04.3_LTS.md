---
title: "Intermittent sound on 12.04.3 LTS"
date: 2013-09-25
forum: Multimedia Software
---

### Post by Macamba on 2013-09-25
Hi,

Last week I had to reinstall Ubuntu. As a result I'm now running 12.04.3 LTS. I have troubles with my sound. When I startup Amarok I sometimes have no sound. I found out the sound strength was on zero. The next day I had no sound playing Amarok and had to twiddle a bit to get it working (from digital to analog I think). And let's not talk about Internet radio, I do not know whether that has worked at all. Today I can not get it to work. So, what are my options? 

Macamba

PS. The output from
```

wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
[http://www.alsa-project.org/db/?f=e1cf293187cfb7fae497cfcfb203729b6545ce97](http://www.alsa-project.org/db/?f=e1cf293187cfb7fae497cfcfb203729b6545ce97)

---

### Post by Yellow Pasque on 2013-09-25
Try to use the latest kernel that comes with Precise:
```
sudo apt-get install linux-generic-lts-raring xserver-xorg-lts-raring
```
Reboot after install.

---

### Post by Macamba on 2013-09-26
Before I updated I had sound. Probably dependent on the wind direction or time of day. After the update I saw I went from
linux-headers-3.5.0-40/
to
linux-headers-3.8.0-30/

Isn't that a big jump in version numbers?

Strange. I had a live CD (actually a DVD) 'Ubuntu-12.04.2-desktop=amd64'. However, when I installed I installed from the Internet. And not the latest version. Strange. :confused:

Hope it helped. Thanks for the help.

---

