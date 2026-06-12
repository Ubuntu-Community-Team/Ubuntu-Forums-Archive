---
title: "Medibuntu directory failed!"
date: 2010-04-19
forum: Multimedia Software
---

### Post by Baldrick_NZ on 2010-04-19
Having installed Medibuntu directory, I now find that I get the following message when attempting to get updates:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Followed by:

Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11). - connect (110: Connection timed out)
Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-en_NZ.bz2](http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-en_NZ.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-en_NZ.bz2](http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-en_NZ.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Some index files failed to download, they have been ignored, or old ones used instead.

All was going well until a couple of days back, with no changes made to the directory from this end.

I'm using Lucid 10.04 (so maybe a glitch in the lead-up to it's official launch, but may not be either).

I used the following link to install the directory, and as I said before has worked flawlessly until a couple of days back.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Any ideas as to how to get them to work again? 

Also, just curious, does the Packman repo that Opensuse use work under Ubuntu?

Cheers,
Baldrick.

---

### Post by WinterRain on 2010-04-19
Everyone is having the same issue. It's a problem with the servers that will be fixed soon. And no, you can't use another distro's repo in ubuntu.

---

### Post by Baldrick_NZ on 2010-04-19
> **WinterRain said:**
> Everyone is having the same issue. It's a problem with the servers that will be fixed soon. And no, you can't use another distro's repo in ubuntu.

Phew! Thanks.

---

### Post by Technomouse on 2010-04-19
I have the same problem and i have posted a fix here


[http://ubuntuforums.org/showthread.php?t=1457944&highlight=medibuntu.org](http://ubuntuforums.org/showthread.php?t=1457944&highlight=medibuntu.org)

Essentially i i used the Debian repo's and howto found here

[http://www.linwik.com/wiki/configuring+media+and+dvd+playback+in+debian+gnu+linux+5.0](http://www.linwik.com/wiki/configuring+media+and+dvd+playback+in+debian+gnu+linux+5.0)

---

