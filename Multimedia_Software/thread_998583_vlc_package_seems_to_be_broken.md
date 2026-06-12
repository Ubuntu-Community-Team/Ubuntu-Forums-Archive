---
title: "vlc package seems to be broken"
date: 2008-11-30
forum: Multimedia Software
---

### Post by sweetbrett on 2008-11-30
I upgraded from 8.04 to 8.10 and it seems that my vlc package got broken along the way.  I had it installed fine on 8.04, but i eventually had to remove it to complete the upgrade to 8.10 and now I cannot reinstall it.  here's my output when i try to install vlc:

```
$ sudo apt-get install vlc
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
  vlc: Depends: vlc-nox (= 0.9.4-1ubuntu3) but it is not going to be installed
       Depends: libass1 but it is not installable
E: Broken packages

```

I've been searching around the net for a while and i'm thinking it's just me that is having this problem so any ideas on how to fix this would be great.  thanks

---

### Post by cariboo on 2008-12-01
Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages. This should repair the problem and allow you to install vlc.

Jim

---

### Post by sweetbrett on 2008-12-02
ok so since I'm in kubuntu, how do I use adept or apt to repair packages?

---

### Post by binbash on 2008-12-02
sudo apt-get purge vlc-nox && sudo apt-get autoremove && sudo apt-get install vlc

---

### Post by sweetbrett on 2008-12-02
didn't work

```

$ sudo apt-get purge vlc-nox && sudo apt-get autoremove && sudo apt-get install vlc                                                             
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
Package vlc-nox is not installed, so not removed                                
The following packages were automatically installed and are no longer required: 
  libkexiv2-3 libexiv2-2 libkdcraw3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkexiv2-3 libexiv2-2 libkdcraw3
The following packages will be REMOVED:
  libexiv2-2 libkdcraw3 libkexiv2-3
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
After this operation, 2175kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127602 files and directories currently installed.)
Removing libkexiv2-3 ...
Removing libexiv2-2 ...
Removing libkdcraw3 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
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
  vlc: Depends: vlc-nox (= 0.9.4-1ubuntu3) but it is not going to be installed
       Depends: libass1 but it is not installable
E: Broken packages
```

---

### Post by binbash on 2008-12-02
fix : 

sudo apt-get purge vlc && sudo apt-get autoremove && sudo apt-get install vlc

---

### Post by sweetbrett on 2008-12-02
still didn't work

```
$ sudo apt-get purge vlc && sudo apt-get autoremove && sudo apt-get install vlc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package vlc is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
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
  vlc: Depends: vlc-nox (= 0.9.4-1ubuntu3) but it is not going to be installed
       Depends: libass1 but it is not installable
E: Broken packages
```

---

### Post by mc4man on 2008-12-02
I'm running 8.04 and don't use vlc 0.8.6 so this is a bit of a guess.

Try this in konsole and see what comes up, (if it's there let it be removed

```
sudo apt-get remove liblame0
```

Otherwise try and see if it gives you some options to satisfy the install

```
sudo aptitude install vlc
```

---

### Post by sweetbrett on 2008-12-02
liblame0 removed mplayer and a few other autoinstalled things, but vlc still gives me the same error.

sorry forgot the code:
```

$ sudo aptitude install vlc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  libvcdinfo0 vlc vlc-nox
The following NEW packages will be installed:
  libcdio7{a} libdvbpsi4{a} libebml0{a} liblua5.1-0{a} libmatroska0{a}
  libnotify1{a} libschroedinger-1.0-0{a} libsdl-image1.2{a} libsexy2{a}
  libswscale0{a} libtar{a} libtwolame0{a} libvlc2{a} libvlccore0{a}
  notification-daemon{a} vlc-data{a}
0 packages upgraded, 19 newly installed, 0 to remove and 1 not upgraded.
Need to get 11.0MB of archives. After unpacking 29.9MB will be used.
The following packages have unmet dependencies:
  vlc-nox: Depends: libdca0 which is a virtual package.
           Depends: libdvdnav4 (>= 4.1.2) but it is not installable
  vlc: Depends: libass1 which is a virtual package.
  libvcdinfo0: Depends: libiso9660-5 but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libvcdinfo0 [Not Installed]
vlc [Not Installed]
vlc-nox [Not Installed]

Score is -9863
```

---

### Post by sweetbrett on 2008-12-14
anyone have any other ideas?  i'd still like to get vlc installed.

---

### Post by mc4man on 2008-12-14
Actually I meant libvlc0, confused with mplayer and liblame0

You may want to install synaptic, easier to work with than adept
```

sudo apt-get install synaptic
```

See if libvlc0 is still installed, easiest way would be to try to remove it.(or search in synaptic, adept

```
sudo apt-get remove libvlc0
```

If you install synaptic see what it says about broken packages, also it should be easier to track down what's preventing the install

maybe also post your sources

cat /etc/apt/sources.list

---

### Post by sweetbrett on 2008-12-14
when i installed synaptic, i saw that universe wasn't enabled.  once i enabled that, vlc installed perfectly.  simple solutions like that always bug me because I swear adept showed 'universe' was enabled.  oh well, solved.  thanks for the help.

---

