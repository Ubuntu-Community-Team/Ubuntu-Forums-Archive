---
title: "AVIF support in Ubuntu 20.04 ?"
date: 2024-01-08
forum: Multimedia Software
---

### Post by raj0012 on 2024-01-08
Hello,
this is a question in reference to an old thread I found here: [https://ubuntuforums.org/showthread.php?t=2468023](https://ubuntuforums.org/showthread.php?t=2468023)
It was written in that thread that one can install gThumb from Ubuntu Handbook PPA and it should support AVIF files. It was even written "*Just updating with that PPA, not bothering to install anything new,   fixed AVIF for existing apps such as Image Viewer and Nautilus.*"
However, that's not the case for me. I added that PPA to my system and updated gThumb (it also updated several other packages, below is the log from apt), but neither gThumb nor any other programs still don't recognize the AVIF files. What's interesting, gThumb can **save**  image (opened as another format) as AVIF, but it cannot reopen that  file again. The same applies eg. for Image Viewer - it displays an error  message about "unrecognized file type".

Here's the apt log for the packages installed/updated from PPA:

Install: libx265-192:amd64 (3.4-0sergeyd3.2~20.04.1, automatic),  libjxl:amd64 (0.6.1~ppa1~focal, automatic), libaom3:amd64  (3.4.0-1~ppa1~focal2, automatic), libdav1d5:amd64 (0.8.1-0build1~20.04,  automatic)
Upgrade: gthumb:amd64 (3:3.8.0-2.1ubuntu0.1, 3:3.12.4-0focal1),  gthumb-data:amd64 (3:3.8.0-2.1ubuntu0.1, 3:3.12.4-0focal1),  libheif1:amd64 (1.6.1-1build1, 1.11.0-0build5~focal), libde265-0:amd64  (1.0.4-1build1, 1.0.8-0build1~20.04)                 

Just today I got another update, but this didn't fix the problem:

Install: libheif-plugin-libde265:amd64 (1.16.2-0ubuntu2~focal, automatic), libheif-plugin-dav1d:amd64 (1.16.2-0ubuntu2~focal, automatic), libheif-plugin-x265:amd64 (1.16.2-0ubuntu2~focal, automatic), libheif-plugin-aomenc:amd64 (1.16.2-0ubuntu2~focal, automatic), libdav1d6:amd64 (1.2.1-0build1~focal, automatic)
Upgrade: gthumb:amd64 (3:3.12.4-0focal1, 3:3.12.4-0focal2), gthumb-data:amd64 (3:3.12.4-0focal1, 3:3.12.4-0focal2), libheif1:amd64 (1.11.0-0build5~focal, 1.16.2-0ubuntu2~focal)

What can I do to make it work?

---

