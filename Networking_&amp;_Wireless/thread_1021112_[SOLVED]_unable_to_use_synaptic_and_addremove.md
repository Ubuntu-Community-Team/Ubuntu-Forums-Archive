---
title: "[SOLVED] unable to use synaptic and add/remove"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by thingy87654321 on 2008-12-25
on my toshiba satellite m45-s351 laptop i have ubuntu 8.04 and i cant use synaptic or add/remove on it,
it worked fine about three weeks ago, now it give this error message, 
W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

that is from when it reloads the available applications

but i have a question, it says that it could not connect to localhost:4001
and is it not the default on ubuntu to set it as localhost, so is it trying to connect to my computer and simpliy cant find them on my laptop
or is it more serious,
i dont want to reinstall my operating system again, i am tried of reinstalling it, so if someone know how to fix it without a reinstall i would be ever so grateful.:(

---

### Post by namdung on 2008-12-25
Try the following in terminal

```
sudo apt-get update
```

---

### Post by thingy87654321 on 2008-12-25
i tryed and got this

chris@chris-laptop:~$ sudo apt-get update
sudo: unable to resolve host chris-laptop
[sudo] password for chris: 
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
o o
W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


and so i tried to run apt-get update in the terminal but it just gave a error message

---

### Post by namdung on 2008-12-25
Post the output of

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by thingy87654321 on 2008-12-25
i ran it in the terminal and got these results

chris@chris-laptop:~$ cat /etc/hostname
chris-laptop
chris@chris-laptop:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts
chris@chris-laptop:~$

---

### Post by thingy87654321 on 2008-12-25
not sure if this is helpful but, the update manager cant download updates either, thank namdung

happy holidays

---

### Post by theozzlives on 2008-12-25
Don't blame namdung, post the contents of your /etc/apt/sources.list here.

---

### Post by Ezure on 2008-12-25
I am having the exact same problem but on an Acer Laptop (Aspire 9420)
I don't mean to hijack the thread but here is the content of the files requested earlier.

brett@joe-bloe:~$ cat /etc/hostname
joe-bloe

brett@joe-bloe:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	joe-bloe

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

brett@joe-bloe:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid main restricted
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-updates main restricted
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid universe
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid universe
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-updates universe
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid multiverse
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-updates multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security main restricted
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security main restricted
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security universe
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security universe
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security multiverse
brett@joe-bloe:~$ 


I have tried changing to other servers and have yet to find a solution.
Any help would be appreciated.

Brett

( here is the output from a sudo apt-get update )

brett@joe-bloe:~$ sudo apt-get update
[sudo] password for brett: 
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid/main Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid/restricted Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid/universe Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid/multiverse Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-updates/main Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-updates/restricted Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-updates/universe Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-updates/multiverse Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-security/main Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-security/restricted Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-security/universe Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://ftp.iinet.net.au](http://ftp.iinet.net.au) intrepid-security/multiverse Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_AU
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/Release.gpg](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/main/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/main/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/restricted/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/restricted/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/universe/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/universe/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/Release.gpg](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_AU.bz2](http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/Release.gpg](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/main/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/main/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_AU.bz2](http://ftp.iinet.net.au/pub/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_AU.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by jerome1232 on 2008-12-25
> **thingy87654321 said:**
> i tryed and got this

chris@chris-laptop:~$ sudo apt-get update
sudo: unable to resolve host chris-laptop
[sudo] password for chris: 
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
o o
W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


and so i tried to run apt-get update in the terminal but it just gave a error message


Do you have some sort of proxy setup in System->Prefrences->Network Proxy?

---

### Post by Ezure on 2008-12-26
I have the "Direct Internet Connection" option selected in Network Proxy.
There are 3 listings under Ignored Hosts which are
*.local
localhost
127.0.0.0/8

---

### Post by namdung on 2008-12-26
> **thingy87654321 said:**
> i ran it in the terminal and got these results

chris@chris-laptop:~$ cat /etc/hostname
chris-laptop
chris@chris-laptop:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts
chris@chris-laptop:~$


You have *unable to resolve host* issue, which generally means that your laptop name in the two above mentioned files are different.

The output of ```
cat /etc/hosts
``` should be

```
127.0.0.1	localhost
127.0.1.1	chris-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

If not, copy/paste/save the above code in the file
```
sudo gedit /etc/hosts
```

Now run
```
sudo apt-get update
```

---

### Post by namdung on 2008-12-26
> **Ezure said:**
> I have the "Direct Internet Connection" option selected in Network Proxy.
There are 3 listings under Ignored Hosts which are
*.local
localhost
127.0.0.0/8

If you have installed ***anon-proxy***, remove it from Synaptic Package Manager or
```
sudo apt-get remove anon-proxy
```

---

### Post by theozzlives on 2008-12-26
try  commentimg out the following:
> deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security main restricted
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security main restricted
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security universe
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security universe
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) intrepid-security multiverse

---

### Post by Ezure on 2008-12-26
> **namdung said:**
> If you have installed ***anon-proxy***, remove it from Synaptic Package Manager or
```
sudo apt-get remove anon-proxy
```

That did the trick. Thank you very much!
I hope Chris has some success with your advice also.

---

### Post by thingy87654321 on 2008-12-27
here are the contents of /etc/apt/sources.list

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy main restricted
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates main restricted
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy universe
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy universe
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates universe
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy multiverse
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy multiverse
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates multiverse
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security main restricted
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security main restricted
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security universe
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security universe
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security multiverse
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security multiverse



and i was trying to update amsn, and it said unable to connect localhost:4001 bad port number

---

### Post by thingy87654321 on 2008-12-27
i tried sudo apt-get remove anon-proxy
but it did not help,
i get this error message when trying to use add/remove

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/pool/universe/g/gnusound/gnusound_0.7.4-6build1_i386.deb](http://cudlug.cudenver.edu/ubuntu/pool/universe/g/gnusound/gnusound_0.7.4-6build1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by thingy87654321 on 2008-12-27
namdung, i checked the /etc/hosts file and there was only one line
so i copied and pasted the data using sudo gedit /etc/hosts, tried the the sudo apt-get update command and got this

chris@chris-laptop:~$ cat /etc/hosts

# The following lines are desirable for IPv6 capable hosts
chris@chris-laptop:~$ sudo gedit /etc/hosts
sudo: unable to resolve host chris-laptop
[sudo] password for chris: 
chris@chris-laptop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	chris-laptop


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
chris@chris-laptop:~$ sudo apt-get update
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://cudlug.cudenver.edu/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
chris@chris-laptop:~$

---

### Post by thingy87654321 on 2008-12-27
in my last message it said on the error message to try apt-get updates
i tried it and got this

chris@chris-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
chris@chris-laptop:~$

---

### Post by thingy87654321 on 2008-12-27
namdung, i tried this command like up posted
sudo apt-get remove anon-proxy

it removed anon-proxy

but it still wont work, i am going to restart and go into recovery mode and try the "remove broken packages" option and see if it does any help

---

### Post by thingy87654321 on 2008-12-27
here is the content of the sources.list file

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy main restricted
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates main restricted
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy universe
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy universe
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates universe
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy multiverse
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy multiverse
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates multiverse
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security main restricted
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security main restricted
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security universe
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security universe
deb [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security multiverse
deb-src [http://cudlug.cudenver.edu/ubuntu/](http://cudlug.cudenver.edu/ubuntu/) hardy-security multiverse

---

### Post by thingy87654321 on 2008-12-27
i used the laptop as a battering ram agansit a dog that was trying to bite me, the dog was not harmed by it tho

and now it works perfecly, and no problems with the laptop at all, i think i probaly beat the problems out of it

---

### Post by thingy87654321 on 2008-12-28
i just learned that the aspca was looking for the dog because it bit 3 other people and thoose people had to go to the hospital to get stiches

---

### Post by thingy87654321 on 2008-12-28
thanks namdung and everyone else who helped, happy holidays

---

