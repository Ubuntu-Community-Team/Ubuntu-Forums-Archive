---
title: "Getting DVD's to work on 8.04"
date: 2010-11-11
forum: Multimedia Software
---

### Post by Cityscape on 2010-11-11
I have an older computer running Ubuntu 8.04.4 LTS.
I installed Ubuntu-restricted-extras and that seemed to get audio support working well. But how to get DVD support working?

I used the "sudo apt-get install libdvdread4" command which I use to get DVD support working in 10.xx but it returned with "E: Couldn't find package libdvdread4". I'm guessing there is a different way to do this in 8.04?

---

### Post by Cityscape on 2010-11-12
No one knows how to install DVD support?

---

### Post by mc4man on 2010-11-12
Been a while since hardy (and I changed it quite a bit.

For starters vlc would be better for dvd's so run this (1 command, iirc it's libdvdread3

```
sudo apt-get install vlc && \
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Should install vlc and libdvdcss2, if so that's all you need to enable playback, any issues start vlc from a terminal, open a dvd from vlc's menu and post terminal output

Totem-xine is also good, to try (do above command first
```
sudo apt-get install totem-xine libxine1-ffmpeg
```

---

### Post by 73ckn797 on 2010-11-12
Go here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the instructions.

---

