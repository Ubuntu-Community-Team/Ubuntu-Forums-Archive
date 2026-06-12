---
title: "BluRay playback issue after fresh installation of Ubuntu 20.04 - lack of AACS file"
date: 2020-04-27
forum: Multimedia Software
---

### Post by adam-przedniczek on 2020-04-27
After switching to **Ubuntu 20.04 Focal Fossa** I've encountered an issue with **Blu Ray** playback in **VLC** - lack of **AACS** configuration file.
Such a problem didn't occur in previous distros (19.10 & 19.04), in which I didn't have to do anything with AACS.

I suppose I installed everything that could be necessary to BluRay/DVD playback.

In ***Software & Updates*** > ***Ubuntu Software*** I've checked: **main**, **universe**, **restricted** and **multiverse**.

Of course I've done **apt install ubuntu-restricted-extras**:
```
ubuntu-restricted-addons/focal,now 26 amd64 [zainstalowany]
ubuntu-restricted-extras/focal,now 67 amd64 [zainstalowany]
```
Additionally, I installed all libraries that could be related to disk playback:
```
libvlc-bin/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
libvlc5/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
libvlccore9/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-bin/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-data/focal,focal,now 3.0.9.2-1 all [zainstalowany,automatycznie]
vlc-l10n/focal,focal,now 3.0.9.2-1 all [zainstalowany,automatycznie]
vlc-plugin-base/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-plugin-notify/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-plugin-qt/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-plugin-samba/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-plugin-skins2/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-plugin-video-output/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-plugin-video-splitter/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc-plugin-visualization/focal,now 3.0.9.2-1 amd64 [zainstalowany,automatycznie]
vlc/focal,now 3.0.9.2-1 amd64 [zainstalowany]

libbluray-bdj/focal,focal,now 1:1.2.0-1 all [zainstalowany]
libbluray-bin/focal,now 1:1.2.0-1 amd64 [zainstalowany]
libbluray-dev/focal,now 1:1.2.0-1 amd64 [zainstalowany]
libbluray-doc/focal,focal,now 1:1.2.0-1 all [zainstalowany]
libbluray2/focal,now 1:1.2.0-1 amd64 [zainstalowany]

libaacs-dev/focal,now 0.9.0-2 amd64 [zainstalowany]
libaacs0/focal,now 0.9.0-2 amd64 [zainstalowany]

libbdplus-dev/focal,now 0.1.2-3 amd64 [zainstalowany]
libbdplus0/focal,now 0.1.2-3 amd64 [zainstalowany]

libdvd-pkg/focal,focal,now 1.4.2-1-1 all [zainstalowany]
libdvdcss-dev/now 1.4.2-1~local amd64 [zainstalowany,lokalny]
libdvdcss2/now 1.4.2-1~local amd64 [zainstalowany,lokalny]
libdvdnav-dev/focal,now 6.0.1-1build1 amd64 [zainstalowany]
libdvdnav-doc/focal,focal,now 6.0.1-1build1 all [zainstalowany]
libdvdnav4/focal,now 6.0.1-1build1 amd64 [zainstalowany]
libdvdread-dev/focal,now 6.1.0+really6.0.2-1 amd64 [zainstalowany]
libdvdread7/focal,now 6.1.0+really6.0.2-1 amd64 [zainstalowany]
```

What should I do to enable BluRay playback?
I tried to download [http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg](http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg) , but I have a major security objections about such workaround.

By the way, on the BluRay disk itself, there're AACS and CERTIFICATE directories - could we use their own content to enable playback?

---

