---
title: "help with dhcp server"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by DFord425 on 2009-02-07
Im trying to turn an old computer into a router. I am following this tutorial  [http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)
and im at the point where i run this command:
```
sudo apt-get install dhcp3-server
```
But i get an error message saying the packages are broken. do i have to add something to the sources.list file?

---

### Post by DFord425 on 2009-02-08
Anyone have any ideas?

---

### Post by superprash2003 on 2009-02-08
im not sure which one of these is required for dhcp server.. but not harm in adding them all..just add these to the sources.list file

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse

---

### Post by DFord425 on 2009-02-08
thanks for the help, but non of those worked. When i try to install it again i get this error message:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dhcp3-server: Depends: dhcp3-common (= 3.0.6.dfsg-1ubuntu9) but 3.1.1-1ubuntu2 is to be installed
E: Broken packages
```

---

### Post by FishRCynic on 2009-02-08
sudo apt-get update
sudo apt-get upgrade

and try again

---

### Post by DFord425 on 2009-02-08
sudo apt-get upgrade works, sudo apt-get update works but gives me this message at the end:
```
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems

```
and i still get the broken packages error when i run sudo apt-get install dhcp3-server.

---

### Post by bukwirm on 2009-02-08
Can you post the contents of your sources.list?

---

### Post by DFord425 on 2009-02-08
here is my sources.list file:
```

#
# deb cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/ hardy main restricted

# deb cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
#added for Xbox Media Center
deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
#added 2009-02-08
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner
deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

```

---

### Post by FishRCynic on 2009-02-08
go into software sources

mouse to


system -> administration -> Software Sources

go to Updates tab 
uncheck proposed

Close

in terminal now
sudo apt-get update

"you will get the google error until you add its key"

see if the dhcp packages work now

---

### Post by DFord425 on 2009-02-09
> **FishRCynic said:**
> go into software sources

mouse to


system -> administration -> Software Sources

go to Updates tab 
uncheck proposed

Close

in terminal now
sudo apt-get update

"you will get the google error until you add its key"

see if the dhcp packages work now

This is the server edition, how would i make the change in Software Sources?

---

### Post by FishRCynic on 2009-02-09
brilliantly stupid i am.

before we do that, just to be sure.

you are running hardy server

(packages listed above in one comment were for ibex)

did you manage to install any of the ibex packages?

---

### Post by DFord425 on 2009-02-09
im running ibex server, 8.10

---

### Post by FishRCynic on 2009-02-09
eureka

in your sources.list file you have all sorts of hardy listed


edit the file and change the hardy to intrepid

then
sudo apt-get update
sudo apt-get upgrade

and install dhcp

---

### Post by DFord425 on 2009-02-09
> **FishRCynic said:**
> eureka

in your sources.list file you have all sorts of hardy listed


edit the file and change the hardy to intrepid

then
sudo apt-get update
sudo apt-get upgrade

and install dhcp

Wow, thats good to know. This happened because i took the sources.list file from my hardy desktop and transfered it to my server, im an idiot. Thanks for your help.

---

