---
title: "How do I convert MP4 files to 3GP or 3GPP files?"
date: 2024-07-16
forum: Multimedia Software
---

### Post by AbleTassie on 2024-07-16
Hello:

How do I convert MP4 files to 3GP or 3GPP files?

I would prefer something as easy as possible. Fine quality and sophisticated bells & whistles are not necessary.

I would also like to add a timer to the video that shows the time elapsed as the video runs. (I also want the audio associated with the video in the MP4 files to be preserved in the 3GP or 3GPP files.)

Thank you,

Able

---

### Post by currentshaft on 2024-07-22
ffmpeg can be used to do all of that. You can ask an LLM for specific arguments or read the man page to get the exact commands.

---

### Post by AbleTassie on 2024-07-23
> **currentshaft said:**
> ffmpeg can be used to do all of that. You can ask an LLM for specific arguments or read the man page to get the exact commands.

Thanks CurrentShaft,

Does ffmpeg come with a GUI? Or can it only be used with commands in Terminal?

Thank you,

A.

---

### Post by #&amp;thj^% on 2024-07-23
> **AbleTassie said:**
> 
Does ffmpeg come with a GUI? Or can it only be used with commands in Terminal?

Thank you,



Source: [https://qwinff.github.io/](https://qwinff.github.io/)
```
apt show qwinff
Package: qwinff
Version: 0.2.1+git20201215-3
Priority: optional
Section: universe/video
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <debian-multimedia@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,176 kB
Depends: libc6 (>= 2.34), libgcc-s1 (>= 3.0), libgl1, libqt5core5t64 (>= 5.15.1), libqt5dbus5t64 (>= 5.14.1), libqt5gui5t64 (>= 5.14.1) | libqt5gui5-gles (>= 5.14.1), libqt5network5t64 (>= 5.0.2), libqt5opengl5t64 (>= 5.0.2), libqt5widgets5t64 (>= 5.0.2), libstdc++6 (>= 5.2), ffmpeg, mpv, sox
Homepage: http://qwinff.github.io/
Download-Size: 546 kB
APT-Sources: http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
Description: GUI for FFmpeg
 This is a free and open source media converter frontend to FFmpeg. FFmpeg
 is a powerful command-line utility to convert audio and video file into
 numerous formats. QWinFF features a rich set of presets to help users use
 FFmpeg easily without having to manually input command-line flags. Average
 users can convert multiple media files in just a few clicks, while advanced
 users can still adjust conversion parameters in detail.
```

It's nice but I still prefer CLI that's just me.

---

### Post by AbleTassie on 2024-08-07
Thank you very much 1fallen.

A.

---

### Post by #&amp;thj^% on 2024-08-07
Happy to help.

---

