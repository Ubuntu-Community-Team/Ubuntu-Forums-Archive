---
title: "VLC Player Issues"
date: 2011-10-26
forum: Multimedia Software
---

### Post by stevedude on 2011-10-26
Hi all,

After upgrading to Oneric 11.10 64-bit from Natty 11.04 64-bit, I'm experiencing several issues. I'm having issues with VLC Player, specifically, I cannot install VLC Player at all. I get a Message that "vlx-nox" needs to be installed but will not because it will break other packages. "Depends: vlc (>= 0.9.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

mozilla-plugin-vlc: Depends: vlc-nox (= 1.1.12-1~getdeb1) but 1.1.12-1~getdeb1 is to be installed
                    Depends: libc6 (>= 2.3.4) but 2.13-20ubuntu5 is to be installed
                    Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
                    Depends: libstdc++6 (>= 4.1.1) but 4.6.1-9ubuntu3 is to be installed
vlc: Depends: vlc-nox (= 1.1.12-1~getdeb1) but 1.1.12-1~getdeb1 is to be installed
     Depends: libaa1 (>= 1.4p5) but 1.4p5-38build1 is to be installed
     Depends: libavcodec-extra-52 (>= 4:0.6-1~) but 4:0.6.2-1ubuntu2 is to be installed
     Depends: libavutil-extra-50 (>= 4:0.6-1~) but 4:0.6.2-1ubuntu2 is to be installed
     Depends: libc6 (>= 2.8) but 2.13-20ubuntu5 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.4-2ubuntu1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
     Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.4-0ubuntu8 is to be installed
     Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but 1.2.10-2.1 is to be installed
     Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.1ubuntu4 is to be installed
     Depends: libstdc++6 (>= 4.5) but 4.6.1-9ubuntu3 is to be installed
     Depends: libtar but it is not going to be installed
     Depends: libxcb-xv0 (>= 1.2) but 1.7-3 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
vlc-plugin-notify: Depends: vlc-nox (= 1.1.12-1~getdeb1) but 1.1.12-1~getdeb1 is to be installed
                   Depends: libc6 (>= 2.8) but 2.13-20ubuntu5 is to be installed
                   Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
                   Depends: libglib2.0-0 (>= 2.12.0) but 2.30.0-0ubuntu4 is to be installed
                   Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.6-0ubuntu5 is to be installed
                   Depends: libnotify1-gtk2.10 but it is a virtual package
vlc-plugin-pulse: Depends: vlc-nox (= 1.1.12-1~getdeb1) but 1.1.12-1~getdeb1 is to be installed
                  Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is to be installed

There are no broken packages in Synaptic that are listed. I had to uninstall my previous installation of VLC in order for Banshee Player to work. In Natty both co-existed with no issues. I use the Unity desktop.

I tried to install SopCast Player last night and it depends on VLC in order to work so I cannot install that program either. Looking for some help in correcting the issue or is this a major bug?

Thanks in advance.

---

### Post by mc4man on 2011-10-26
You appear to have getdebs enabled in your sources. Either   they don't have oneiric packages yet or your maybe your getdeb source is still set to natty
I'd remove getdebs from your sources, update your sources & install 11.10's vlc which is currently 1.11.

11.10 will be updating to vlc-1.12 shortly, currently in  proposed/testing

---

### Post by stevedude on 2011-10-27
Thanks again mc4man,

When I cam home this evening, I saw a notification that there were Oneiric updates waiting to be installed. One of them was for VLC Player. I installed the updates and now VLC Player is installed and working fine. I appreciate your time to respond.

This thread is "Solved".

---

