---
title: "How to upgrade OpenShot"
date: 2023-11-28
forum: Multimedia Software
---

### Post by satimis on 2023-11-28
I have OpenShot
Version:3.1.0
libopenshot: 0.3.1

running on Ubuntu 22.04 for long time and I couldn't recall how it was installed.  Whether it came with Ubuntu 22.04 as default?

I'm going to upgrade it to ‘OpenShot-v3.1.1-x86_64.AppImage’

$ apt policy openshot-qt```

openshot-qt:
  Installed: (none)
  Candidate: 2.5.1+dfsg1-2
  Version table:
     2.5.1+dfsg1-2 500
        500 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy/universe i386 Packages

```
This package is not installed.

$ apt policy openshot```

openshot:
  Installed: (none)
  Candidate: (none)
  Version table:

```

Neither I could recall whether it was installed on OpenShop .appimage

sudo find ./ OpenShot-v3.1.0-x86_64.AppImage```

.....
.....
find: ‘OpenShot-v3.1.0-x86_64.AppImage’: No such file or directory

```

I couldn't find ‘OpenShot-v3.1.0-x86_64.AppImage’ package on the PC.

Please advise how to remove this old version.  I have ‘OpenShot-v3.1.1-x86_64.AppImage’ download.

Thanks in advance

Regards

---

### Post by TheFu on 2023-11-28
Don't be so exact with your find search.  I wouldn't be case sensitive and I wouldn't search from the CWD down, I'd look from /.   

And if you have **locate**, I'd use that instead, since it updates daily, automatically, and is 10000x faster than scanning a file system.

```
$ locate -i openshot
```

---

### Post by satimis on 2023-11-28
> **TheFu said:**
> Don't be so exact with your find search.  I wouldn't be case sensitive and I wouldn't search from the CWD down, I'd look from /.   

And if you have **locate**, I'd use that instead, since it updates daily, automatically, and is 10000x faster than scanning a file system.

```
$ locate -i openshot
```
Hi,

Thanks for your advice.

I tried it before
$ locate -i openshot
no output

---

### Post by satimis on 2023-11-28
Hi TheFu,

Again

I found my old posting on March 2022

How to upgrade Openshot to latest version
[https://ubuntuforums.org/showthread.php?t=2472902](https://ubuntuforums.org/showthread.php?t=2472902)

OpenShot was installed running flatpak.

I'll uninstall openshot old version and use its AppImage latest version.

I'll come back later after testing.

Regards

---

### Post by deadflowr on 2023-11-29
Flatpak is the same version.
Unless you've never updated it.

Running
```
flatpak update
```
will update it to the latest version available.
Along with any other installed flatpak packages.

---

### Post by ajgreeny on 2023-11-29
If its any comfort to you, I use the appimage of openshot and it works brilliantly; I've never used the flatpack system so can't comment usefully about that.

---

### Post by satimis on 2023-11-29
> **deadflowr said:**
> Flatpak is the same version.
Unless you've never updated it.

Running
```
flatpak update
```
will update it to the latest version available.
Along with any other installed flatpak packages.
Hi,

I haven't run OpenShot for quite long time, using Kdenlive instead with more features.  If download OpenShot-v3.1.1-x86_64.AppImage to Downloads folder and run it here, it will remind me that the package was installed on Flatpak.  Not like this time it took me long time to discover it.

Upgrade to OpenShot-v3.1.1 running flatpak

steps:-

1)
On Terminal
$ flatpak uninstall openshot (to remove its old version)
-> Yes
-> Yes

2) Run Flatpak to install OpenShot

$ sudo apt install gnome-software-plugin-flatpak

$ flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)

$ flatpak install flathub org.openshot.OpenShot
-> Yes
-> Yes

(remark: it took a while to finish)

$ flatpak run org.openshot.OpenShot

Now OpenShot starts, adding to Favorite automatically. 

$ sudo nano /home/satimis/.local/share/applications/gearlever_openshotvideoeditor.desktop
```

[Desktop Entry]
Name=OpenShot Video Editor
GenericName=Video Editor
X-GNOME-FullName=OpenShot Video Editor
Comment=Create and edit amazing videos and movies
Exec=/home/satimis/AppImages/gearlever_openshotvideoeditor_897937.appimage
Terminal=false
Type=Application
Icon=/home/satimis/AppImages/.icons/gearlever_openshotvideoeditor
Categories=GNOME;GTK;AudioVideo;Video;AudioVideoEditing;
MimeType=application/vnd.openshot-qt-project;
X-AppInstall-Package=openshot-qt
X-AppImage-Version=897937

```

Regards

---

### Post by ajgreeny on 2023-11-29
Having said in post #6 that I was using an appimage I now see I have the official ppa for openshot enabled with version 3.1.1.

See [https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa](https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa)

---

