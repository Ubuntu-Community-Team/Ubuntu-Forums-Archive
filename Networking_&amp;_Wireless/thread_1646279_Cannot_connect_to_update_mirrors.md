---
title: "Cannot connect to update mirrors"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by A1phaOmega on 2010-12-15
HI,

I recently had to move my hard drive to a new box as the other one was dying. All went well, except that the network was not connecting.
I tried another card, got it on DHCP and then got it back to a static IP. All works well.
But, when trying to ```
sudo apt-get update
``` or ```
sudo apt-get upgrade
```, I get the following error:

 > Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports Release.gpg
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Packages
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/main Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/restricted Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/universe Sources
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-backports/multiverse Sources
  Unable to connect to au.archive.ubuntu.com:http:
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (202.158.214.106). - connect (110: Connection timed out)

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/Release.gpg)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/i18n/Translation-en_AU.bz2)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources.gz)  Unable to connect to au.archive.ubuntu.com:http:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/uni](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/uni)

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/mul](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/mul)

E: Some index files failed to download, they have been ignored, or old ones used


However, I can ping au.archive.ubuntu.com and recieve a reply from the mirrors.
So, I have internet connection, but I cannot access the mirrors when trying to update.

Cheers

---

