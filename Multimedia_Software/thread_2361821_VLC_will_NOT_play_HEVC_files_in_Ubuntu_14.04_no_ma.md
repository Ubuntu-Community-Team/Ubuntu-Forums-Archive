---
title: "VLC will NOT play HEVC files in Ubuntu 14.04 no matter what I do"
date: 2017-05-21
forum: Multimedia Software
---

### Post by davy jones on 2017-05-21
So far I have tried almost every single method out there to get VLC to play HEVC files in Ubuntu 14.04. I first tried to install VLC 2.2.4 from this repository ppa:jonathonf/vlc. But I could not install the libde265 plugin because it said I have unmet dependencies (libvlccore7 was needed, but it was not going to be installed).

I also tried this:

    ```
sudo add-apt-repository ppa:mc3man/trusty-media  
sudo apt-get update  
sudo apt-get dist-upgrade
```

Followed by:

    ```
sudo apt-add-repository ppa:strukturag/libde265  
sudo apt-get update  
sudo apt-get install vlc-plugin-libde265
```

For some time after this, I was able to play HEVC files. But somewhere along the way (after some update which I cannot recall), HEVC files stopped playing again. So I purged all of these repositories and installed VLC 2.1.6 (already available in Ubuntu 14.04), and then installed libde265. It did not work. So I updated VLC in the same manner described above (using ppa:mc3man/trusty-media) but IT STILL DOES NOT WORK.


I also installed gstreamer1.0-libde265 and HEVC files play perfectly well on Videos. But VLC just doesn't play them! What the hell is happening? Can anyone please help me?

---

### Post by mc4man on 2017-05-21
I no longer use vlc much nor that version in the multimedia ppa. (find mpv much better.
 But to test removed a 'higher' ppa I have for 14.04, removed vlc **completely** (sudo apt-get purge vlc-data).
Then I installed the multimedia ppa version (2.2.1~trusty2) & installed the ppa's vlc-plugin-libde265 package (0.1.7-1ppa1~trusty1.1)
After removing ~/.config/vlc folder then I played back a hevc file with no issue, i.e. screen
(- note that on the multimedia ppa description it says - 
> Vlc: after upgrading please remove ~/.config/vlc folder to ensure proper runnning

So you need to have those specific packages installed & start with a fresh ~/.config/vlc, you can't use the strukturag ppa package with vlc 2.2.1..

If you didn't want to have to use the plugin then read here carefully [https://launchpad.net/~mc3man/+archive/ubuntu/testing6](https://launchpad.net/~mc3man/+archive/ubuntu/testing6), meant to be used with the multimedia ppa

---

### Post by davy jones on 2017-05-21
Hi, thanks for the reply. I followed these instructions, but it's still not working. I can't play HEVC files. These are the VLC related packages I currently have installed, in case that is relevant.

[ATTACH=CONFIG]275212[/ATTACH][ATTACH=CONFIG]275213[/ATTACH]

---

### Post by mc4man on 2017-05-21
If you can supply me a sample I'll test. In addition I made a small sample, dl & test,
```
wget https://0x0.st/E-k.mp4
```

---

### Post by davy jones on 2017-05-22
Strangely, this file plays just fine. But the files I have are mkv files, and they're not playing only in VLC. Totem is able to play them, and so is Plex.

---

### Post by mc4man on 2017-05-22
> **davy jones said:**
> Strangely, this file plays just fine. But the files I have are mkv files, and they're not playing only in VLC. Totem is able to play them, and so is Plex.
vlc historically can have issues with mkv in general, what determines which mkv work vs. which don't  i'm not up on.
You could try a newer vlc version or just use other players on problem files.

---

