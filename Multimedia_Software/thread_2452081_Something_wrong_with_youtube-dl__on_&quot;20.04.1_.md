---
title: "Something wrong with youtube-dl  on &quot;20.04.1 LTS (Focal Fossa)&quot;"
date: 2020-10-16
forum: Multimedia Software
---

### Post by nnn1308 on 2020-10-16
Something wrong with youtube-dl on "20.04.1 LTS (Focal Fossa)"

$ grep VERSION /etc/os-release 
VERSION="20.04.1 LTS (Focal Fossa)"
VERSION_ID="20.04"
VERSION_CODENAME=focal


$ sudo apt  install youtube-dl  # version 2020.03.24-1
No apt package "youtube-dl", but there is a snap with that name.
Try "snap install youtube-dl"

$ sudo snap install youtube-dl
    # I can install, but something wrong with youtube-dl -o  option. (unable to open for writing: [Errno 13] Permission denied)
$ sudo snap remove youtube-dl

Download from
[http://launchpadlibrarian.net/497570427/youtube-dl_2020.09.14-1_all.deb](http://launchpadlibrarian.net/497570427/youtube-dl_2020.09.14-1_all.deb)

Click the "deb", and install.

youtube-dl -o  option problem was fixed.

---

### Post by coffeecat on 2020-10-16
Closed. [https://ubuntuforums.org/showthread.php?t=2439118](https://ubuntuforums.org/showthread.php?t=2439118)

---

