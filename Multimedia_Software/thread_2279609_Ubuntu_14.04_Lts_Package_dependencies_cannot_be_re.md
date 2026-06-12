---
title: "Ubuntu 14.04 Lts Package dependencies cannot be resolved."
date: 2015-05-24
forum: Multimedia Software
---

### Post by chris382 on 2015-05-24
I'm trying to watch a movie i downloaded but when i try to open it up in Videos it says i need to install extra multimedia plugins and gives me this error "Package dependencies cannot be resolvedThis error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."The following packages have unmet dependencies:gstreamer1.0-libav: Depends: libavcodec-extra-54 (>= 6:9.13) but 6:9.18-0ubuntu0.14.04.1 is to be installed                    Depends: libavformat54 (>= 6:9.1-1) but 6:9.18-0ubuntu0.14.04.1 is to be installed                    Depends: libavutil52 (>= 6:9.1-1) but 6:9.18-0ubuntu0.14.04.1 is to be installed                    Depends: libc6 (>= 2.14) but 2.19-0ubuntu6.6 is to be installed                    Depends: libglib2.0-0 (>= 2.37.3) but 2.40.2-0ubuntu1 is to be installed

---

### Post by mc4man on 2015-05-24
There is occasionally some issues with the extra packages, particularly the libavformat one which is really just a dummy/transitional one.

Maybe start with  - 
Open Software & Updates > Updates tab & make sure 1st 2 options are enabled (Important.. & Recommended..
Then close & run 
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
When that is done run & post
```
apt-cache policy gstreamer1.0-libav
```

---

### Post by chris382 on 2015-08-23
gstreamer1.0-libav:
  Installed: (none)
  Candidate: 1.2.4-1~ubuntu1
  Version table:
     1.2.4-1~ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe amd64 Packages
     1.2.3-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages

---

### Post by mc4man on 2015-08-23
Well then try to install the plugin & see what happens
```
sudo apt-get install gstreamer1.0-libav
```

---

### Post by Bucky Ball on 2015-08-24
Are you watching in VLC? That drags in a lot of codecs. You may need to enable the Canonical Partners repository in 'Software and Updates'.

---

### Post by diegoabib1 on 2015-10-04
I resolved this problem removing some packages and installing it again with this commands: 


sudo apt-get remove gstreamer1.0-libav:i386


sudo apt-get install gstreamer1.0-libav

Diego Abib.

---

