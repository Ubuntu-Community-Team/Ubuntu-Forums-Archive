---
title: "VLC, Totem etc very slow frame rate/choppy but Firefox VLC plugin works fine"
date: 2014-12-09
forum: Multimedia Software
---

### Post by db579 on 2014-12-09
I'm running Ubuntu 14.04 on an Acer Aspire V7 (i7 Haswell CPU). Playing any kind of movie file mkv, mp4 etc on VLC or Totem is horribly choppy with very slow frame rate like the computer can't handle it properly. Weirdly though playing the same files in Firefox using the VLC plugin works absolutely fine. What's going on here?

---

### Post by db579 on 2014-12-12
Installing and running the intel-linux-graphics installer solved my problem:

```

wget [https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.7-0intel1_amd64.deb](https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.7-0intel1_amd64.deb)
sudo apt-get install gdebi
sudo gdebi intel-linux-graphics-installer_1.0.7-0intel1_amd64.deb
sudo apt-get -f install
sudo intel-linux-graphics-installer

```

All credit to mchid from AskUbuntu:

[http://askubuntu.com/questions/558831/vlc-totem-etc-very-slow-frame-rate-choppy-but-firefox-vlc-plugin-works-fine](http://askubuntu.com/questions/558831/vlc-totem-etc-very-slow-frame-rate-choppy-but-firefox-vlc-plugin-works-fine)

---

