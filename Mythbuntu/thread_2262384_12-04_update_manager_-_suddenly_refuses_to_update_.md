---
title: "12-04 update manager - suddenly refuses to update some packages?"
date: 2015-01-24
forum: Mythbuntu
---

### Post by neutron68 on 2015-01-24
It is refusing to update mondorescue and its mindi component.  I've never had this happen before.
[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/20150119_192643_zpsifn4idmk.jpg]("http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/20150119_192643_zpsifn4idmk.jpg")
[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/20150119_192652_zpslpd3wjkq.jpg]("http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/20150119_192652_zpslpd3wjkq.jpg")

Of note, there is no button or checkbox to say Do it Anyway, only a close button!?

How can we tell it to proceed and download the update?

---

### Post by mörgæs on 2015-01-25
Please reboot and run 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
and after that post the results in CODE tags.

---

### Post by neutron68 on 2015-01-25
Hi mörgæs.  Before you posted a reply, I found a forum post where they urged forcing an apt-get upgrade via command line, as a workaround.

Here's how that went:
```
eric@Mythbuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  mindi
The following packages will be upgraded:
  mindi-busybox mondo
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,092 kB of archives.
After this operation, 84.0 kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mindi-busybox mondo
Install these packages without verification [y/N]? y
Get:1 ftp://ftp.mondorescue.org//ubuntu/ 12.04/contrib mindi-busybox amd64 1.21.1-1 [257 kB]
Get:2 ftp://ftp.mondorescue.org//ubuntu/ 12.04/contrib mondo amd64 3.2.0-1 [834 kB]
Fetched 1,092 kB in 7s (149 kB/s)
(Reading database ... 839739 files and directories currently installed.)
Preparing to replace mindi-busybox 1.18.5-3 (using .../mindi-busybox_1.21.1-1_amd64.deb) ...
Unpacking replacement mindi-busybox ...
Preparing to replace mondo 3.0.4-1 (using .../mondo_3.2.0-1_amd64.deb) ...
Unpacking replacement mondo ...
Processing triggers for man-db ...
Setting up mindi-busybox (1.21.1-1) ...
Setting up mondo (3.2.0-1) ...
```

From this, I can see that there is a way to approve an upgrade even when the sources aren't authenticated.

We need the same ability to approve an upgrade from the Update Manager graphic user interface.

---

### Post by mörgæs on 2015-01-25
It may or may not be an option in 14.04. I don't know because I never update through the GUI.

---

### Post by ian-weisser on 2015-01-25
> **neutron68 said:**
> We need the same ability to approve an upgrade from the Update Manager graphic user interface.

No we don't.

You can install (perhaps) poisoned packages if you wish...it's your system. I wouldn't - that warning is a big red flag.

Signed packages and authenticated repositories are a critical part of the infrastructure that keeps Ubuntu safe. We will not place in users in a position to break their systems by easily (and unknowingly) overriding important protections. That would be poor design and a betrayal of the users' trust.

Users who understand the warning can trivially disable the protection, as you discovered. I value that protection.

---

### Post by neutron68 on 2015-01-27
All that needs to be added to the GUI Update Manager is a question that asks "Are you sure you want to enable this update" (like the command line routine did).  That's plenty of protection for me, and yet gives me the option to update a package that I installed and want to have updated.

---

