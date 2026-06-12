---
title: "Unable to Install VLC"
date: 2017-12-15
forum: Multimedia Software
---

### Post by BalaViknesh on 2017-12-15
Am getting below error when trying to install VLC

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libvlc5 : Depends: libvlccore9 (>= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1~) but it is not going to be installed
 vlc : Depends: vlc-bin (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Depends: vlc-l10n (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Depends: vlc-plugin-base (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Depends: vlc-plugin-qt (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Depends: vlc-plugin-video-output (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Recommends: vlc-plugin-samba (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Recommends: vlc-plugin-skins2 (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Recommends: vlc-plugin-video-splitter (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
       Recommends: vlc-plugin-visualization (= 3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



Output of apt-get -f installThe following additional packages will be installed:
  libvlccore9
The following NEW packages will be installed:
  libvlccore9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/472 kB of archives.
After this operation, 1,247 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 359521 files and directories currently installed.)
Preparing to unpack .../libvlccore9_3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1_amd64.deb ...
Unpacking libvlccore9:amd64 (3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libvlccore9_3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libvlccore.so.9.0.0', which is also in package libvlccore8:amd64 3.0.0~~git20171210+r73147+99~ubuntu16.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore9_3.0.0~rc1~~git20171214+r73255+108~ubuntu16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can anyone please help me fix this error and install vlc

---

### Post by &amp;KyT$0P# on 2017-12-15
What version of Ubuntu?
What PPAs have you added?

---

### Post by mc4man on 2017-12-15
They are from the vlc [master ppa ]("https://launchpad.net/~videolan/+archive/ubuntu/master-daily")which *seems* to have started making usable packages again after 6+ months of crap.
Be aware that it'll install a newer version of ffmpeg (shared), those libs can co-exist with 16.04's ffmpeg shared libs but there is only 1 set of devel packages allowed at a time. (- so if you were to build something using ffmpeg shared it probably would use the ppa's version for better or worse.

Based on message I'd - 

Edit. There is an issue with the ppa packages so until fixed you can
1. do without vlc
2. Remove the ppa (ppa-purge) and go back to ubuntu repo version

Edit: see here for further info
[https://ubuntuforums.org/showthread.php?t=2380299&p=13721486&viewfull=1#post13721486](https://ubuntuforums.org/showthread.php?t=2380299&p=13721486&viewfull=1#post13721486)

---

### Post by mc4man on 2017-12-17
Should be fixed now that the master ppa got it's package naming correct

---

