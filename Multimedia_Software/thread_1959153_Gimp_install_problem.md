---
title: "Gimp install problem"
date: 2012-04-15
forum: Multimedia Software
---

### Post by safetygary on 2012-04-15
Tried installing from package manager as well as from terminal. Same results, any help in what I'm doing wrong?

XXXX@XXXX-Latitude-D810:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
XXXX@XXXX-Latitude-D810:~$

---

### Post by Rodney9 on 2012-04-15
You have to use sudo and your password
```

sudo apt-get install gimp

```

If you want some good plug-ins with Gimp

```
sudo apt-get install gimp-data-extras gimp-dcraw gimp-resynthesizer gimp-plugin-registry gimp-texturize
```

see here for what they do - [http://scottlinux.com/2010/11/23/extra-gimp-packages-you-should-install/](http://scottlinux.com/2010/11/23/extra-gimp-packages-you-should-install/)

Help Guide to Ubuntu Oneiric version 11.10

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

Rodney

---

### Post by safetygary on 2012-04-16
Thank you Rodney, you've made this moran happy!

---

### Post by safetygary on 2012-04-16
Oops - the gimp installation may not be the bigger issue, here is the error message received:

whoopsie -s /bin/false -u 116 whoopsie' returned error code 1. Exiting.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 whoopsie
Error in function: 
Setting up whoopsie (0.1.25) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /nonexistent -g whoopsie -s /bin/false -u 116 whoopsie' returned error code 1. Exiting.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1

Any help appreciated as I love ubuntu, no nothing, but enjoy trying.

---

