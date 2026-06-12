---
title: "Can't play a .m4v DVD on 18.04"
date: 2019-07-31
forum: Multimedia Software
---

### Post by cearlp2 on 2019-07-31
I have read several posts about VLC not reading dvd's and have tried most of the suggested solutions but nothing has worked so far.
I'm hoping someone can offer or direct me to a solution that actually solves my problem.
I have configured VLC to log so I can see what is happening and what it contains at the end of the file:
-------
main debug: creating demux: access='dvd' demux='any' location='/dev/sr0' file='/dev/sr0'
main debug: looking for access_demux module matching "dvd": 21 candidates
dvdnav warning: cannot open DVD (/dev/sr0)
dvdread error: DVDread cannot open source: /dev/sr0
main debug: no access_demux modules matched
main debug: creating access: dvd:///dev/sr0
main debug: (path: /dev/sr0)
main debug: looking for access module matching "dvd": 26 candidates
main debug: no access modules matched
main debug: dead input
qt debug: IM: Deleting the input
-------
The dvd was created with MACOS and works fine on a DVD player connected to a TV.

---

### Post by uRock on 2019-07-31
Did you install ubuntu-restricted-extras? [Have you followed these instructions?]("https://itsfoss.com/play-dvd-ubuntu-1310/") What else have you done?

---

### Post by mc4man on 2019-07-31
If you instruct vlc to open a disc as a dvd then it has to be a DVD_VIDEO disc. What you have is not that..
Open it as a file or folder.

---

### Post by cearlp2 on 2019-08-05
uRock, I followed all the instructions in the link you suggested, however after downloading the libdvdcss2_1.2.13-0_amd64.deb, running the apt-get returned E: Unable to locate package libdvdread4.

---

### Post by SeijiSensei on 2019-08-05
```
sudo apt install smplayer mpv
```

This combination will play pretty much anything you throw at it.

I've never understood why these programs aren't the default player in Ubuntu.

---

### Post by speartip on 2019-08-14
> **cearlp2 said:**
> uRock, I followed all the instructions in the link you suggested, however after downloading the libdvdcss2_1.2.13-0_amd64.deb, running the apt-get returned E: Unable to locate package libdvdread4.
Did you update apt cache first? libdvdread4 is in the repos! Run these 1 at a time.
```
sudo apt update
```
```
sudo apt install libdvd-pkg
```
```
sudo dpkg-reconfigure libdvd-pkg
```
That should be all you need to do.

---

