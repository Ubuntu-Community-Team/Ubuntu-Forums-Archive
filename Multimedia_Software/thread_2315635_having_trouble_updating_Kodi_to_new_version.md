---
title: "having trouble updating Kodi to new version"
date: 2016-03-01
forum: Multimedia Software
---

### Post by poker master on 2016-03-01
after reading the wiki file for Kodi and typing in the lines below one at a time and then the next. My system tells me that Kodi is 
updated but nothing on the system has changed. Also did not see anything to indicate new software was installed like one would expect on the last
step. never had a problem like this in linux before. any ideas what's going on here.

My Kodi is still like 14.2 latest is like 16.00RC

Ubuntu 12.04 (precise)
  
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
```

```
sudo apt-get install kodi }
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kodi is already the newest version.
The following packages were automatically installed and are no longer required:
  python-imdbpy libxml-namespacesupport-perl libmythtv-perl
  libreoffice-emailmerge libxml-sax-expat-perl libreoffice-writer
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-help-en-gb
  libreoffice-help-en-us mythes-en-au wmctrl python-uno mythes-en-us
  libxml-sax-perl nvidia-settings-304 openoffice.org-hyphenation hyphen-en-us
  libxml-simple-perl libreoffice-math libxml-sax-base-perl libkms1
  libnet-upnp-perl libmyth-python python-urlgrabber
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dan@dan-Aspire-M3970:~$
```

---

### Post by howefield on 2016-03-01
And that would be correct, you have the latest version that is available in the Precise repository.

Head on over to the launchpad PPA and filter by series to see what each repository contains..

[https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa?field.series_filter=precise](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa?field.series_filter=precise)

```
Precise :  kodi	2:14.2~git20150327.1058-final-0precise
Trusty  :  kodi	2:16.0~git20160220.1654-final-0trusty
Wily     :  kodi	2:16.0~git20160220.1654-final-0wily
Xenial  :  kodi	2:16.0~git20160228.1453-final-0xenial
```

---

### Post by poker master on 2016-03-01
The problem is it does not seem to have updated anything or changed anything. Still have like 14.2 and nothing new anywhere......Help

---

### Post by howefield on 2016-03-02
You seem not to be understanding, there are no newer package in that repository for Precise than the one you have on your system.

They have newer packages for Trusty, Wily, and Xenial. It would appear there is no intention of making the new version available for Precise, you could always write to the PPA maintainers and ask.

---

### Post by poker master on 2016-03-02
Thanks i see where your coming from need to run newer version of OS thanks

---

### Post by howefield on 2016-03-02
> **poker master said:**
> Thanks i see where your coming from need to run newer version of OS thanks

You could do that or you could find another PPA for Precise (but probably unlikely to be one). 12.04 has a further year of support so you are likely to need to move to something else reasonably soon in any event. 

Or just run with the Kodi that you have. :)

---

