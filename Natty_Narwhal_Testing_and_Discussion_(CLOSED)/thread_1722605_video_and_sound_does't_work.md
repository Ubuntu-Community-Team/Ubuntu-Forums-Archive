---
title: "video and sound does't work"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by andy08 on 2011-04-06
Hello,
after updating 11.04 today video is only running with high speed and no sound, even not at start up. I tried to restart many times, but no success.
When I go to youtube same problem: high speed ( 4 minutes in 10 seconds ) and no sound.
I can't download two updates that for gstreamer plugins and C++
Any ideas. Thanks in advance.

---

### Post by garvinrick4 on 2011-04-06
When playing music on a media player does sound work then?

---

### Post by andy08 on 2011-04-06
no nothing works, no game, no media player and video is running

Thanks for your reply

---

### Post by garvinrick4 on 2011-04-06
Did you get these updates today:
[UPGRADE] gstreamer0.10-alsa 0.10.32-1ubuntu3 -> 0.10.32-1ubuntu5
[UPGRADE] gstreamer0.10-plugins-bad 0.10.21-1ubuntu8 -> 0.10.21-1ubuntu11
[UPGRADE] gstreamer0.10-plugins-base 0.10.32-1ubuntu3 -> 0.10.32-1ubuntu5
[UPGRADE] gstreamer0.10-plugins-base-apps 0.10.32-1ubuntu3 -> 0.10.32-1ubuntu5
[UPGRADE] gstreamer0.10-plugins-good 0.10.28-0ubuntu4 -> 0.10.28-0ubuntu6
[UPGRADE] gstreamer0.10-plugins-ugly 0.10.17-1 -> 0.10.17-1ubuntu2
[UPGRADE] gstreamer0.10-pulseaudio 0.10.28-0ubuntu4 -> 0.10.28-0ubuntu6
[UPGRADE] gstreamer0.10-tools 0.10.32-3 -> 0.10.32-3ubuntu3
[UPGRADE] gstreamer0.10-x 0.10.32-1ubuntu3 -> 0.10.32-1ubuntu5
##See the settings below custom filters and upgradable see what is in there that can be
installed so you can install through Synaptics log out and back in again.

---

### Post by andy08 on 2011-04-06
Yes, I checked it out. All is upgraded, But this one not:
C++Wrappers for ATK accessibility toolkit (for shared libraries)
libatkmm-1.6-1_2.22.5-0ubuntu1_i386

I tried to download it but it doesn't work. It tells me to check my Internet Connection but that is working fine. The details:

W: Failed to fetch [http://th.archive.ubuntu.com/ubuntu/pool/main/a/atkmm1.6/libatkmm-1.6-1_2.22.5-0ubuntu1_i386.deb](http://th.archive.ubuntu.com/ubuntu/pool/main/a/atkmm1.6/libatkmm-1.6-1_2.22.5-0ubuntu1_i386.deb)
  403  Forbidden

Thanks

---

### Post by garvinrick4 on 2011-04-06
> I tried to download it but it doesn't work. It tells me to check my Internet Connection but that is working fine. The details:

W: Failed to fetch [http://th.archive.ubuntu.com/ubuntu/...untu1_i386.deb]("http://th.archive.ubuntu.com/ubuntu/pool/main/a/atkmm1.6/libatkmm-1.6-1_2.22.5-0ubuntu1_i386.deb")
  403  ForbiddenChange your mirror in Software Sources.
[http://packages.ubuntu.com/natty/i386/libatk1.0-0/download](http://packages.ubuntu.com/natty/i386/libatk1.0-0/download)
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

