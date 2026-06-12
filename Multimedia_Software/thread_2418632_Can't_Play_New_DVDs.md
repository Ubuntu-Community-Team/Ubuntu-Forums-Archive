---
title: "Can't Play New DVDs"
date: 2019-05-09
forum: Multimedia Software
---

### Post by skyesharica on 2019-05-09
Ubuntu 18.04.2 LTS - and plenty of disc space etc.

Hi friends. Can't play a movie on the PC. Videos has never worked and there isn't 'DVD Source' in the Software 'Collection'. See error message - image below. Now even VLC software (usually plays anything) won't play them. They're both new DVDs.  :guitar:

---

### Post by yancek on 2019-05-09
Try the suggestions at the Ubuntu site at the link below.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Holger_Gehrke on 2019-05-09
Video DVDs are partially encrypted using something called Content Scrambling System. This protects the DVD consortium from unauthorized players (hard or software) and doubles as copy protection. How to get players on Linux to work around this has been discussed several times, newest thread I could find on this is [here]("https://ubuntuforums.org/showthread.php?t=2414762").

Holger

---

### Post by skyesharica on 2019-05-10
Thanks for the info but I'd really love it if someone could just tell me how to play a video. In English please? (-:

---

### Post by Frogs Hair on 2019-05-10
Copy and paste the following commands in the terminal in order. This is applicable to the default movie player.

```
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg 
```

```
sudo dpkg-reconfigure libdvd-pkg
```

---

