---
title: "audacity appimage ffmpeg library not found"
date: 2024-05-22
forum: Multimedia Software
---

### Post by ajgreeny on 2024-05-22
On my Xubuntu-Noble installation I added the audacity-linux-3.5.1-x64 appimage.
It runs very well but it does not find the ffmpeg libraries and even if I tell it where they are in the **Preferences -> Libraries** dialog it still does not show them meaning I can't export files to mp3.

I have ffmpeg 7.6.1.1-3ubuntu5 installed and have pointed Audacity to it but it never shows.

Anyone got an idea why?  I have searched and found nothing so far.

---

### Post by gezzer2 on 2024-05-23
not sure if this is of help but ..

via synaptic you can install the ffmpeg-extra package/libs
this may have the required files you need ..

---

### Post by ajgreeny on 2024-05-23
> **gezzer2 said:**
> not sure if this is of help but ..

via synaptic you can install the ffmpeg-extra package/libs
this may have the required files you need ..
I would love to try but there is no such package available, though having made a search for the package it looks as if it used to be related to chromium browser when it was still a .deb version.

---

### Post by ajgreeny on 2024-05-23
Interestingly, I have just found that export to mp3 is still possible even without the ffmpeg library being found as the lame libraries do the job and lame is something I always install.
I have to admit that I was not aware that would be the situation so I have certainly learned something today.
As a test I have also just enabled the ppa for audacity from [https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity) which gives the same audacity version as the appimage and that successfully finds the ffmpeg libraries so this is at least a workaround.

However, it still does not explain why the appimage can not use the ffmpeg libraries and I would love to know why.  Using the same appimage in 22.04 did not have this problem so I can only assume it is something related to the library versions in 24.04 compared to the versions in 22.04.

---

### Post by gezzer2 on 2024-05-24
sorry about that the package is available in my synaptic that maybe due to me using LMDE.
i apologise ..

---

### Post by ajgreeny on 2024-05-24
> **gezzer2 said:**
> sorry about that the package is available in my synaptic that maybe due to me using LMDE.
i apologise ..
Yes, pretty sure that's why but I don't run LMDE so can't check it out.

---

### Post by gezzer2 on 2024-05-25
not sure if this will help is the ffmpeg direct download page for Ubuntu and Debian ..

[https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)

---

