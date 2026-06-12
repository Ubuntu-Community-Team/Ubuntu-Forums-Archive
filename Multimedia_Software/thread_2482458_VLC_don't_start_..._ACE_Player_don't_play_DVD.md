---
title: "VLC don't start ... ACE Player don't play DVD"
date: 2022-12-31
forum: Multimedia Software
---

### Post by ligustri on 2022-12-31
Hi,

I can't get my Ubuntu play DVD's. When I click VLC icon, nothing happens. My Ubuntu version is 22.04.1 LTS. I've tried to reinstall VLC, but it didn't help. I've installed packages e.g.  libdvdread8, libdvdnav4, dpkg-reconfigure libdvd-pkg and other packages, but these doesn't help.

Help, help, please help! :mad::rolleyes::mad::rolleyes::confused:

---

### Post by ajgreeny on 2023-01-01
Have you followed all the instructions at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for Ubuntu versions later than 15.10 without which commercial DVDs will not play?

Installing the libdvd-pkg is just the start; you then have to run the script which actually installs libdvdcss2.

---

### Post by ligustri on 2023-01-01
Well, Kaffeine was solution. Mplayer didn't help. Thanks.

---

