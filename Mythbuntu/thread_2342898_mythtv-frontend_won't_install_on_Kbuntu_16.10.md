---
title: "mythtv-frontend won't install on Kbuntu 16.10"
date: 2016-11-11
forum: Mythbuntu
---

### Post by ris2t on 2016-11-11
After upgrading from Kbuntu 16.04 to 16.10 mythtv (specifically mythtv-frontend) has become uninstallable.


```

sudo apt-get install mythtv-frontend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythtv-frontend : Depends: transcode but it is not installable
                   Recommends: libmythtv-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Best I can determine, and from other articles, is that transcode is nolonger available within 16.10. But recent mythtv 0.28 packages still seem to refer to it.

Some details:
```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"

apt-cache policy transcode
transcode:
  Installed: (none)
  Candidate: (none)
  Version table:

```

I've tried the standard repository and ppa:mythbuntu/0.28 to no effect.

Any suggests on cause, debugging, or resolution steps would be appreciated. I've waited a number of weeks attempting to trace the cause or workaround with no luck.

---

### Post by ris2t on 2016-11-11
2:0.28.0+fixes.20161106.1434df8-0ubuntu0mythbuntu2 - is the package version available to me in Yakkety (16.10)

[http://lists.mythtv.org/pipermail/mythtv-commits/2016-October/112831.html]("http://lists.mythtv.org/pipermail/mythtv-commits/2016-October/112831.html") reports the same issue but no resolution that I can find.

---

### Post by howefield on 2016-11-11
> **ris2t said:**
> 2:0.28.0+fixes.20161106.1434df8-0ubuntu0mythbuntu2 - is the package version available to me in Yakkety (16.10)


From a 16.10 install.

```
apt-cache policy mythtv-frontend 
mythtv-frontend:
  Installed: (none)
  Candidate: 2:0.28.0+fixes.20160413.15cf421-0ubuntu2
  Version table:
     2:0.28.0+fixes.20160413.15cf421-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu yakkety/multiverse amd64 Packages
```

---

### Post by ris2t on 2016-11-11
> **howefield said:**
> From a 16.10 install.

```
apt-cache policy mythtv-frontend 
mythtv-frontend:
  Installed: (none)
  Candidate: 2:0.28.0+fixes.20160413.15cf421-0ubuntu2
  Version table:
     2:0.28.0+fixes.20160413.15cf421-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu yakkety/multiverse amd64 Packages
```

Thanks, removed the mythtv 0.28 PPA and tried that version but no luck, same errors. Off chance, what does your apt-cache policy say for transcode?

---

### Post by howefield on 2016-11-11
> **ris2t said:**
> Thanks, removed the mythtv 0.28 PPA and tried that version but no luck, same errors. Off chance, what does your apt-cache policy say for transcode?

```
apt-cache policy transcode
transcode:
  Installed: (none)
  Candidate: (none)
  Version table:
```

Packages can be searched at packages.ubuntu.com

---

### Post by tgm4883 on 2016-11-16
This should be fixed in the 0.28 PPA repo in a few hours.

---

### Post by ris2t on 2016-11-25
Confirmed can now install on 16.10 from the 0.28 PPA. Thanks.

---

