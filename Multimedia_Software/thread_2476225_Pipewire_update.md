---
title: "Pipewire update"
date: 2022-06-20
forum: Multimedia Software
---

### Post by alanpasi on 2022-06-20
Hi, Pipewire is in version 0.3.52 and Ubuntu is in version 0.3.48. When it will be updated in Ubuntu?

---

### Post by Xian on 2022-06-20
It's been included for release in 22.10 --- [https://packages.ubuntu.com/kinetic/pipewire](https://packages.ubuntu.com/kinetic/pipewire)

---

### Post by alanpasi on 2022-06-28
If I choose to stick to Ubuntu 22.04 LTS.

Thank you in advanced.

---

### Post by #&amp;thj^% on 2022-06-28
**Not that I'm recommending this** but have a look: [https://launchpad.net/~pipewire-debian/+archive/ubuntu/pipewire-upstream](https://launchpad.net/~pipewire-debian/+archive/ubuntu/pipewire-upstream)
For me on another OS not* Ubuntu
```
pipewire --version
pipewire
Compiled with libpipewire 0.3.52
Linked with libpipewire 0.3.52

```
No issues on my end but **your** mileage may vary.

---

### Post by iamjiwjr on 2022-06-28
I read this protocol somewhere. It works on 22.04 for me. For the latest packages, you could add the repo below. I added the rest of the install process if anyone wants to try it.

Ubuntu Pipewire Installation 22.04 - enter one instruction at a time in the following order in the terminal:

sudo add-apt-repository ppa:pipewire-debian/pipewire-upstream

sudo apt update

sudo apt install pipewire pipewire-audio-client-libraries

sudo apt install gstreamer1.0-pipewire libpipewire-0.3-{0,dev,modules} libspa-0.2-{bluetooth,dev,jack,modules} pipewire{,-{audio-client-libraries,pulse,media-session,bin,locales,tests}}

systemctl --user daemon-reload

systemctl --user --now disable pulseaudio.service pulseaudio.socket

systemctl --user --now enable pipewire pipewire-pulse

Reboot

pactl info to make sure pipewire is operational.

---

### Post by iamjiwjr on 2022-06-28
The emoticon won't go away. In its place should be  :p

---

