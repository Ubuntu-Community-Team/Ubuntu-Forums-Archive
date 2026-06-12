---
title: "update manager not connected to the internet."
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by neba on 2012-12-09
I'm working with Ubuntu 12.04, I am able to use chrome just fine, but when i try to update my system, I get this error:

Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/Release.gpg)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Unable to connect to 192.168.15.244:22:
, E:Some index files failed to download. They have been ignored, or old ones used instead.




A few weeks ago i ssh my kindle using the 192.168.15.244 ip on port 22 via usb. I believed i change all the settings back, I don't know if i missed something or i really messed things up. 

Thank you in advance,
Branden

---

### Post by neba on 2012-12-14
Also I don't have any luck using the terminal, I just get the same message. Does any one know how to change the ip address 192.168.15.244?

R/S
Branden

---

### Post by ehraaron on 2012-12-14
It almost acts like it is trying to connect to a proxy or it is routing all traffic to that IP instead of looking it up correctly at a valid dns server.

---

