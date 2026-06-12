---
title: "Mplayer is not installing"
date: 2009-02-04
forum: Multimedia Software
---

### Post by ericeclifford on 2009-02-04
Im customizing my cd and when i do the apt-get install mplayer it saids that 10 of its depends are not installable including the mplayer-skins packge.

---

### Post by wolfen69 on 2009-02-04
go to system>administration>software sources and make sure all repos are checked off. close, then reload when asked to.

---

### Post by ericeclifford on 2009-02-04
reloaded then try to apt-get install mplayer again still same 10 things is not installable.

---

### Post by ericeclifford on 2009-02-04
Btw I am trying to customize a live cd I have it on my normal external HD version of ubuntu 8.04.2 but I cant install it in the customization folder(EDIT).

---

### Post by ericeclifford on 2009-02-04
Does anyone know anything about this or what ? :(:(:(:(:(

---

### Post by wolfen69 on 2009-02-04
can you copy and paste the exact error message you get?

---

### Post by ericeclifford on 2009-02-04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libdvdnav4 (>= 0.1.10) but it is not installable
           Depends: libenca0 (>= 1.9) but it is not installable
           Depends: libfaac0 (>= 1.26) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: libjack0 (>= 0.109.2) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libsvga1 but it is not installable
           Depends: libx264-57 (>= 1:0.svn20071224) but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages
root@ericeclifford:/# 


This is wut I get after I do the apt-get install mplayer

---

### Post by wolfen69 on 2009-02-04
try adding the medibuntu repositories first, then try again. i'm assuming you are using ubuntu 8.10 though.
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by ericeclifford on 2009-02-04
I did that already and I am using hardy 8.04.2

---

