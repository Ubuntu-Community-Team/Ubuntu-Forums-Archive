---
title: "Transcode is Installed, but avimerge does not work"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by navneeth on 2007-10-09
Transcode has been installed, and it is the latest version, but when I try to combine three avi's, I get the following message...

```
The program 'avimerge' is currently not installed.  You can install it by typing:
sudo apt-get install transcode
Make sure you have the 'multiverse' component enabled
bash: avimerge: command not found

```

```
[B]navneeth@ubuntu:~$ transcode
Segmentation fault (core dumped)[/B]
navneeth@ubuntu:~$ sudo apt-get install transcode
Reading package lists... Done
Building dependency tree       
Reading state information... Done
transcode is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Do you think that the info in bold might have anything to do with this?
Please help.

---

### Post by navneeth on 2007-10-09
Never mind...a reinstall worked.

---

