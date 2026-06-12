---
title: "Audio / Video problems / Nvidia"
date: 2012-12-08
forum: Multimedia Software
---

### Post by Joe 1 on 2012-12-08
Hi there,

I've installed Ubuntu 12.10 a month ago and I'm experiencing Audio / Video issues all the time. Once a week I have no ability to play music, videos and Skype won't synchronized as well. Every time what solves the problem is to reinstall the driver for the graphic card and restart the computer. I've also noticed that the open source driver doesn't perform very well. The movies don't play smoothly so I have to use the proprietary driver from Nvidia. Voice is crackling on the VLC player. My graphic card is: NVIDIA GF119 [GeForce GT 520] (rev a1)and the Mother Board: Gigabyte 880GMA

I've searched but couldn't find an answer to this problem.

Thank you,

Joe

---

### Post by AstroLlama on 2012-12-09
did you install the latest driver released by nvidia?
[http://www.nvidia.com/object/linux-display-ia32-304.60-driver.html](http://www.nvidia.com/object/linux-display-ia32-304.60-driver.html)

install instructions: [http://www.unixmen.com/nvidia-304-64-has-been-released-a-look-at-new-features-and-instalation-instructions-for-ubuntu-fedora-and-linuxmint-debian/](http://www.unixmen.com/nvidia-304-64-has-been-released-a-look-at-new-features-and-instalation-instructions-for-ubuntu-fedora-and-linuxmint-debian/)

Crackling voice in vlc might be because of incorrect bitrate settings either in vlc OR the sound settings.

---

### Post by Joe 1 on 2012-12-09
> **AstroLlama said:**
> did you install the latest driver released by nvidia?
[http://www.nvidia.com/object/linux-display-ia32-304.60-driver.html](http://www.nvidia.com/object/linux-display-ia32-304.60-driver.html)

install instructions: [http://www.unixmen.com/nvidia-304-64-has-been-released-a-look-at-new-features-and-instalation-instructions-for-ubuntu-fedora-and-linuxmint-debian/](http://www.unixmen.com/nvidia-304-64-has-been-released-a-look-at-new-features-and-instalation-instructions-for-ubuntu-fedora-and-linuxmint-debian/)

Crackling voice in vlc might be because of incorrect bitrate settings either in vlc OR the sound settings.

Thank you for this. I've followed the instructions and installed that driver. I've got the following error after sudo apt-get update ```
Ign http://ca.archive.ubuntu.com quantal-proposed/universe Translation-en_CA
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/source/Sources  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en_CA  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

After the first boot nothing worked again. After another restart everything is working fine except one strange thing. When clicking on Install updates from the system dialogue box I get an error message "Failed to download repository information. Check your Internet connection." I am connected to the Internet.

---

### Post by Joe 1 on 2012-12-23
still having same problems. Once in a while no video, audio and Skype. As well as no system updates available due to failure in internet connection. There is nothing wrong with my Internet connection.

---

### Post by Joe 1 on 2013-03-30
Now restart and reinstall the driver doesn't help. Can't play video / Audio and Skype at all.

---

### Post by Joe 1 on 2013-03-31
I've reinstalled the OS and now it works.

---

### Post by Joe 1 on 2013-04-21
Again same problem. Reinstalling doesn't help either. I guess I'll have to go back to Windows OS.
Any ideas?
Thank you.

---

