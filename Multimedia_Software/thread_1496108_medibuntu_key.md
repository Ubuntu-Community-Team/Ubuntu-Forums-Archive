---
title: "medibuntu key"
date: 2010-05-28
forum: Multimedia Software
---

### Post by newbiefly on 2010-05-28
I'm having trouble getting the key for the medibuntu repository.  i tried instructions here [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") as well as a few other tutorials.  got libdvdcss2 installed anyway with this [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") but still need medibuntu for w32.  anyone else with similar experience?  thanks in advance for your input.

```
fly@fly-laptop:~$ wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
[sudo] password for fly: 
gpg: no valid OpenPGP data found.
fly@fly-laptop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-05-28 20:15:47--  http://www.medibuntu.org/sources.list.d/lucid.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-05-28 20:15:48 (22.4 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Err http://medibuntu.sos-sts.com lucid Release.gpg
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com/repo/ lucid/free Translation-en_US
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US
Err http://medibuntu.sos-sts.com/repo/ lucid/non-free Translation-en_US
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Get:2 http://dl.google.com stable Release [2,544B]
Ign http://medibuntu.sos-sts.com lucid Release
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://medibuntu.sos-sts.com lucid/free Packages
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Get:3 http://dl.google.com stable/main Packages [1,082B]
Ign http://medibuntu.sos-sts.com lucid/non-free Packages
Get:4 http://packages.medibuntu.org lucid Release.gpg [197B]
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US
Hit http://archive.canonical.com lucid Release
Ign http://medibuntu.sos-sts.com lucid/free Sources
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://medibuntu.sos-sts.com lucid/non-free Sources
Hit http://us.archive.ubuntu.com lucid Release
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Ign http://medibuntu.sos-sts.com lucid/free Packages
Get:5 http://packages.medibuntu.org lucid Release [6,854B]
Ign http://packages.medibuntu.org lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://security.ubuntu.com lucid-security/main Packages
Ign http://medibuntu.sos-sts.com lucid/non-free Packages
Ign http://medibuntu.sos-sts.com lucid/free Sources
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://archive.canonical.com lucid/partner Sources
Ign http://medibuntu.sos-sts.com lucid/non-free Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Err http://medibuntu.sos-sts.com lucid/free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Err http://medibuntu.sos-sts.com lucid/non-free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Err http://medibuntu.sos-sts.com lucid/free Sources
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com lucid/non-free Sources
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 4,013B in 1s (3,788B/s)
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/Release.gpg  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/source/Sources.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/source/Sources.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
fly@fly-laptop:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apport-hooks-medibuntu is already the newest version.
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  app-install-data-medibuntu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5kB of archives.
After this operation, 102kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  app-install-data-medibuntu
E: There are problems and -y was used without --force-yes
```

---

### Post by WinterRain on 2010-05-28
Just run this again, if you havn't already. It is supposed to add the key automatically.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
I hope you copy and pasted it in the terminal. I never had a problem with it.

---

### Post by newbiefly on 2010-05-28
```
fly@fly-laptop:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apport-hooks-medibuntu is already the newest version.
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  app-install-data-medibuntu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5kB of archives.
After this operation, 102kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  app-install-data-medibuntu
E: There are problems and -y was used without --force-yes
fly@fly-laptop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for fly: 
--2010-05-28 21:05:13--  http://www.medibuntu.org/sources.list.d/lucid.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[===================================================================================================================>] 268         --.-K/s   in 0s      

2010-05-28 21:05:13 (22.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Err http://medibuntu.sos-sts.com lucid Release.gpg
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com/repo/ lucid/free Translation-en_US
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com/repo/ lucid/non-free Translation-en_US
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US
Ign http://medibuntu.sos-sts.com lucid Release
Get:2 http://dl.google.com stable Release [2,544B]
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://medibuntu.sos-sts.com lucid/free Packages
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Get:3 http://dl.google.com stable/main Packages [1,082B]
Ign http://medibuntu.sos-sts.com lucid/non-free Packages
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://medibuntu.sos-sts.com lucid/free Sources
Hit http://archive.canonical.com lucid Release
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Get:4 http://packages.medibuntu.org lucid Release.gpg [197B]
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US
Ign http://medibuntu.sos-sts.com lucid/non-free Sources
Ign http://medibuntu.sos-sts.com lucid/free Packages
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://medibuntu.sos-sts.com lucid/non-free Packages
Hit http://archive.canonical.com lucid/partner Packages
Hit http://us.archive.ubuntu.com lucid Release
Hit http://security.ubuntu.com lucid-security/main Packages
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Get:5 http://packages.medibuntu.org lucid Release [6,854B]
Ign http://packages.medibuntu.org lucid Release
Ign http://medibuntu.sos-sts.com lucid/free Sources
Ign http://medibuntu.sos-sts.com lucid/non-free Sources
Hit http://archive.canonical.com lucid/partner Sources
Err http://medibuntu.sos-sts.com lucid/free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://packages.medibuntu.org lucid/free Packages
Err http://medibuntu.sos-sts.com lucid/non-free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com lucid/free Sources
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Err http://medibuntu.sos-sts.com lucid/non-free Sources
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 4,013B in 1s (3,319B/s)
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/Release.gpg  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/source/Sources.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/source/Sources.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by WinterRain on 2010-05-28
You did:
```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```
I'm not sure what you are trying to accomplish, but it wasn't the command that I posted. Please do what I posted and report back. You don't need to run any special commands to add the key.

---

### Post by newbiefly on 2010-05-29
sorry copy and paste error i get this
```
fly@fly-laptop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-05-29 07:34:56--  http://www.medibuntu.org/sources.list.d/lucid.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-05-29 07:34:56 (21.0 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Err http://medibuntu.sos-sts.com lucid Release.gpg
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com/repo/ lucid/free Translation-en_US
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US
Get:2 http://dl.google.com stable Release [2,544B]
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Get:3 http://packages.medibuntu.org lucid Release.gpg [197B]
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Err http://medibuntu.sos-sts.com/repo/ lucid/non-free Translation-en_US
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Get:4 http://dl.google.com stable/main Packages [1,082B]
Ign http://medibuntu.sos-sts.com lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Get:5 http://packages.medibuntu.org lucid Release [6,854B]
Hit http://archive.canonical.com lucid Release
Hit http://us.archive.ubuntu.com lucid Release
Ign http://packages.medibuntu.org lucid Release
Ign http://medibuntu.sos-sts.com lucid/free Packages
Ign http://medibuntu.sos-sts.com lucid/non-free Packages
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://archive.canonical.com lucid/partner Packages
Ign http://medibuntu.sos-sts.com lucid/free Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://archive.canonical.com lucid/partner Sources
Ign http://medibuntu.sos-sts.com lucid/non-free Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://medibuntu.sos-sts.com lucid/free Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://medibuntu.sos-sts.com lucid/non-free Packages
Ign http://medibuntu.sos-sts.com lucid/free Sources
Ign http://medibuntu.sos-sts.com lucid/non-free Sources
Err http://medibuntu.sos-sts.com lucid/free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com lucid/non-free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com lucid/free Sources
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com lucid/non-free Sources
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Fetched 4,013B in 9s (422B/s)
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/Release.gpg  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/i18n/Translation-en_US.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/source/Sources.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/source/Sources.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
when i look at System --> Administration --> Software Sources i see Medibuntu an a source but have no Medibuntu key on my ring so when i install updates i get an untrusted source warning

---

### Post by bangbong on 2010-07-14
I just got it working without error.... Thanks

---

