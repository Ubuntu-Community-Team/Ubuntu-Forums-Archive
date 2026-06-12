---
title: "VLC install error"
date: 2011-12-30
forum: Multimedia Software
---

### Post by cozski on 2011-12-30
Hello, I get this when I try to install VLC from terminal:

```
sunonthecross@sunonthecross:~$ sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mozilla-plugin-vlc : Depends: vlc-nox (= 1.1.12-1~getdeb3~oneiric) but 1.1.10-1~getdeb1 is to be installed
 vlc : Depends: vlc-nox (= 1.1.12-1~getdeb3~oneiric) but 1.1.10-1~getdeb1 is to be installed
       Depends: libavcodec53 (>= 4:0.7-1) but it is not installable or
                libavcodec-extra-53 (>= 4:0.7-1) but it is not installable
       Depends: libavutil51 (>= 4:0.7-1) but it is not installable or
                libavutil-extra-51 (>= 4:0.7-1) but it is not installable
       Depends: libstdc++6 (>= 4.6) but 4.5.2-8ubuntu4 is to be installed
       Depends: libtar0 but it is not installable
       Depends: libva-x11-1 (> 1.0.12~) but 1.0.8-3 is to be installed
       Depends: libva1 (> 1.0.12~) but 1.0.8-3 is to be installed
       Depends: libxcb-keysyms1 (>= 0.3.8) but 0.3.6-1build1 is to be installed
       Recommends: vlc-plugin-notify (= 1.1.12-1~getdeb3~oneiric) but 1.1.10-1~getdeb1 is to be installed
 vlc-plugin-pulse : Depends: vlc-nox (= 1.1.12-1~getdeb3~oneiric) but 1.1.10-1~getdeb1 is to be installed
                    Depends: libpulse0 (>= 1:1.0) but 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 is to be installed
E: Broken packages

```

I'm on 11.04 and using a HP Pavillion Desktop PC. Any thoughts? Thanks.

---

### Post by mc4man on 2011-12-30
Well you're using 11.04 & your getdeb source is for 11.10 - that's not going to work.
Switch to the getdeb natty source if there is one.

---

### Post by cozski on 2012-01-01
Thanks... upgraded to 11.10 and installed from Synaptic so all seems fine.

---

