---
title: "Video and some pictures will not work"
date: 2013-05-27
forum: Multimedia Software
---

### Post by John Nicholson UK on 2013-05-27
I am running Ubuntu on a PC for my daughter to use, but she is dismayed that it will not show videos from You-tube or some pictures - like Google street view.  It seems to be missing a link or some vital software component.  How can I fix this problem?

---

### Post by sudodus on 2013-05-27
> **John Nicholson UK said:**
> I am running Ubuntu on a PC for my daughter to use, but she is dismayed that it will not show videos from You-tube or some pictures - like Google street view.  It seems to be missing a link or some vital software component.  How can I fix this problem?

I suggest that you install ***ubuntu-restricted-extras*** using the command line

```
sudo apt-get install ubuntu-restricted-extras
```

or ***Synaptic***, where you find the following additional information about the package. You probably need to add some repositories (and 're-read' or 'update' the list of program packages), which can also be done with Synaptic.

> Commonly used restricted packages for Ubuntu
 
This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Flash plugin, LAME (to create compressed audio files), and DVD playback.

Please note that this does not install libdvdcss2, and will not let you play
encrypted DVDs. For more information, see
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Please also note that packages from multiverse are restricted by copyright
or legal issues in some countries. See
[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
for more information.

---

### Post by Silvertones on 2013-05-27
I'm having the same issue even after installing those packages. I turned off the firewall, popup blocker, no script and add block with no success. I'm using 10.04

---

### Post by sudodus on 2013-05-28
> **Silvertones said:**
> I'm having the same issue even after installing those packages. I turned off the firewall, popup blocker, no script and add block with no success. I'm using 10.04

Ubuntu 10.04 desktop has passed end of life, but the server version has two more years to go. The packages for graphics and audio belong to the desktop version, so I suggest that you get a current version.

The current LTS (long time support) version is 12.04.2. This version is maintained with updated packages (due to security, bug fixes and added features), and we are many people who use it and know how to tweak it or add capabiliities.

---

