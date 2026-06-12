---
title: "mplayer and amd64"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by carsten on 2006-12-23
Hi
I saw on ubuntuguide,org, that it was possible to install mplayer on amd64 and have it play wmv9 files out of the box, problem is after adding the repo site, it errors out with the following when apt-get install mplayer:

root@lappy:/home/carsten# apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
           Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
           Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
           Depends: libcairo2 (>= 1.2.4) but 1.0.4-0ubuntu1 is to be installed
           Depends: libdirectfb-0.9-24 but it is not installable
           Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
           Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
           Depends: libggi2 (>= 1:2.2.1) but it is not going to be installed
           Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
           Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1 is to be installed
           Depends: libjack0.100.0-0 (>= 0.101.1) but it is not going to be installed
           Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be installed
           Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is to be installed
           Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
E: Broken packages


Any1 who have had luck installing it on amd64??

---

### Post by Bachstelze on 2006-12-23
You're running Dapper and the mplayer you try to install is for Edgy (or newer). Either upgrade to Edgy or try to get a Dapper version of mplayer that does what you want.

---

### Post by carsten on 2006-12-23
ahh ok that makes sense. How do i upgrade to edgy?

---

### Post by Bachstelze on 2006-12-23
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

