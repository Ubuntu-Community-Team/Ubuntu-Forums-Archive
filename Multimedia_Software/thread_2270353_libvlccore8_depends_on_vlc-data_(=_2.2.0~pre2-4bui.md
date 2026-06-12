---
title: "libvlccore8 depends on vlc-data (= 2.2.0~pre2-4build1)"
date: 2015-03-22
forum: Multimedia Software
---

### Post by Niranjan_Shakya on 2015-03-22
here I'm new to ubuntu and i've some dependency problem while installing vlc:
here is the error message:


dpkg: dependency problems prevent configuration of libvlccore8:
 libvlccore8 depends on vlc-data (= 2.2.0~pre2-4build1); however:
  Package vlc-data is not installed.


dpkg: error processing package libvlccore8 (--configure):
 dependency problems - leaving unconfigured
Setting up libshine3:amd64 (3.1.0-2) ...
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on libvlccore8 (>= 2.2.0~pre1); however:
  Package libvlccore8 is not configured yet.


dpkg: error processing package vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on libvlccore8 (>= 2.0.0); however:
  Package libvlccore8 is not configured yet.


dpkg: error processing package vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
Setting up libxcb-xv0:amd64 (1.10-2ubuntu1) ...
Setting up libiso9660-8 (0.83-4.1ubuntu1) ...
Setting up libdvbpsi9:amd64 (1.2.0-1) ...
Setting up libusageenvironment1 (2014.01.13-1) ...
Setting up libmatroska6:amd64 (1.4.1-2) ...
dpkg: dependency problems prevent configuration of libvlc5:
 libvlc5 depends on libvlccore8 (>= 2.2.0~pre1); however:
  Package libvlccore8 is not configured yet.


dpkg: error processing package libvlc5 (--configure):
 dependency problems - leaving unconfigured
Setting up libvcdinfo0 (0.7.24+dfsg-0.2) ...
dpkg: dependency problems prevent configuration of vlc-plugin-samba:
 vlc-plugin-samba depends on libvlccore8 (>= 2.2.0~pre1); however:
  Package libvlccore8 is not configured yet.


dpkg: error processing package vlc-plugin-samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libvlc5 (>= 2.1.0); however:
  Package libvlc5 is not configured yet.
 vlc-nox depends on libvlccore8 (>= 2.2.0~pre1); however:
  Package libvlccore8 is not configured yet.


dpkg: error processing package vlc-nox (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
Errors were encountered while processing:
 libvlccore8
 vlc
 vlc-plugin-notify
 libvlc5
 vlc-plugin-samba
 vlc-nox
                                         
Current status: 1 broken [+1].


i used some of the code
i.e :
$ sudo apt-get install -f
but it didn't work out. while using that code got this message:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vlc-data
The following NEW packages will be installed:
  vlc-data
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
6 not fully installed or removed.
Need to get 0 B/5,127 kB of archives.
After this operation, 32.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 210510 files and directories currently installed.)
Preparing to unpack .../vlc-data_2.2.0~pre2-4build1_all.deb ...
Unpacking vlc-data (2.2.0~pre2-4build1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/vlc-data_2.2.0~pre2-4build1_all.deb (--unpack):
 cannot copy extracted data for './usr/share/doc/vlc-nox/fortunes.txt.gz' to '/usr/share/doc/vlc-nox/fortunes.txt.gz.dpkg-new': unexpected end of file or stream
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/vlc-data_2.2.0~pre2-4build1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dino99 on 2015-03-22
how do you try to install vlc ? it should be done from the ubuntu archive to avoid such issue.
which ubuntu are you using ?

---

### Post by ian-weisser on 2015-03-22
> **Niranjan_Shakya said:**
> Unpacking vlc-data (2.2.0~pre2-4build1) ...
dpkg-deb (subprocess): decompressing archive member: **lzma error: compressed data is corrupt**

Dpkg detected a seemingly corrupted package.
Try:
```
sudo apt-get clean vlc-data        ## Delete the corrupted vlc-data package from your cache
sudo apt-get install vlc           ## Retry the install, automatically re-downloads vlc-data
```


This seems like a package from the Ubuntu repositories:
```
$ rmadison vlc-data
 vlc-data | 1.0.6-1ubuntu1         | lucid/universe            | all
 vlc-data | 1.0.6-1ubuntu1.8       | lucid-security/universe   | all
 vlc-data | 1.0.6-1ubuntu1.8       | lucid-updates/universe    | all
 vlc-data | 2.0.1-4                | precise/universe          | all
 vlc-data | 2.0.8-0ubuntu0.12.04.1 | precise-security/universe | all
 vlc-data | 2.0.8-0ubuntu0.12.04.1 | precise-updates/universe  | all
 vlc-data | 2.1.2-2build2          | trusty/universe           | all
 vlc-data | 2.1.4-0ubuntu14.04.1   | trusty-security/universe  | all
 vlc-data | 2.1.4-0ubuntu14.04.1   | trusty-updates/universe   | all
** vlc-data | 2.2.0~pre2-4build1     | utopic/universe           | all**
 vlc-data | 2.2.0~rc2-2            | vivid/universe            | all

```

---

### Post by Niranjan_Shakya on 2015-03-25
ubuntu 14.10

---

### Post by Niranjan_Shakya on 2015-03-25
> **ian-weisser said:**
> Dpkg detected a seemingly corrupted package.
Try:
```
sudo apt-get clean vlc-data        ## Delete the corrupted vlc-data package from your cache
sudo apt-get install vlc           ## Retry the install, automatically re-downloads vlc-data
```


This seems like a package from the Ubuntu repositories:
```
$ rmadison vlc-data
 vlc-data | 1.0.6-1ubuntu1         | lucid/universe            | all
 vlc-data | 1.0.6-1ubuntu1.8       | lucid-security/universe   | all
 vlc-data | 1.0.6-1ubuntu1.8       | lucid-updates/universe    | all
 vlc-data | 2.0.1-4                | precise/universe          | all
 vlc-data | 2.0.8-0ubuntu0.12.04.1 | precise-security/universe | all
 vlc-data | 2.0.8-0ubuntu0.12.04.1 | precise-updates/universe  | all
 vlc-data | 2.1.2-2build2          | trusty/universe           | all
 vlc-data | 2.1.4-0ubuntu14.04.1   | trusty-security/universe  | all
 vlc-data | 2.1.4-0ubuntu14.04.1   | trusty-updates/universe   | all
** vlc-data | 2.2.0~pre2-4build1     | utopic/universe           | all**
 vlc-data | 2.2.0~rc2-2            | vivid/universe            | all

```


ThankYou it work for me :-):-)

---

