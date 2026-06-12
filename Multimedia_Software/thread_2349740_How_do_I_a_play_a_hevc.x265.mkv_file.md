---
title: "How do I a play a hevc.x265.mkv file"
date: 2017-01-17
forum: Multimedia Software
---

### Post by jacatone on 2017-01-17
Anyone how to fix VLC or some other player to play a hevc.x265.mkv file. I recall video codecs has always an issue in Linux. Don't have this problem in Win 10.

---

### Post by howefield on 2017-01-18
Install the libde265-0 package ?

```
apt-cache show libde265-0
Package: libde265-0
Priority: optional
Section: universe/libs
Installed-Size: 648
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: libde265
Version: 1.0.2-2
Depends: libc6 (>= 2.14), libgcc1 (>= 1:3.0), libstdc++6 (>= 5.2)
Filename: pool/universe/libd/libde265/libde265-0_1.0.2-2_amd64.deb
Size: 233756
MD5sum: 98ea9a9dfd77250c931aca140bdd4587
SHA1: f6044482b68466139acc35b7077d9ab977c8d30d
SHA256: f8d6bc24c5f0f0d4aa28b7da78b875b3e6e11e51f7c717554572a92f1dce96cf
Description-en: Open H.265 video codec implementation
 libde265 is an open source implementation of the H.265 video codec.
 It is written from scratch in plain C for simplicity and efficiency.
 Its simple API makes it easy to integrate it into other software.
Description-md5: e2595c4a6d2348fa129b67fcf8e11192
Multi-Arch: same
Homepage: https://github.com/strukturag/libde265
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: ubuntustudio-video
```

---

### Post by SeijiSensei on 2017-01-18
Or use SMPlayer with the mpv engine.
```
sudo apt-get install smplayer mpv
```

---

