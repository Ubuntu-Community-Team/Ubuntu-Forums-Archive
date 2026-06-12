---
title: "kodi install fail"
date: 2017-11-11
forum: Multimedia Software
---

### Post by Lloydb39 on 2017-11-11
Had an older version of Kodi and read it had a security problem, so I removed and purged it. Tried to install 17.3 with instructions from the wiki. No go. This was the result:

```
lloyd@linux:~$sudo add-apt-repository ppa:team-xbmc/ppa
[sudo]password for lloyd: 
 
More info: [https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa)
Press[ENTER] to continue or ctrl-c to cancel adding it


gpg:keyring `/tmp/tmpfbq36b0l/secring.gpg' created
gpg:keyring `/tmp/tmpfbq36b0l/pubring.gpg' created
gpg:requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg:/tmp/tmpfbq36b0l/trustdb.gpg: trustdb created
gpg:key 91E7EE5E: public key "Launchpad PPA for XBMC for Linux"imported
gpg:no ultimately trusted keys found
gpg:Total number processed: 1
gpg:              imported: 1  (RSA: 1)
OK
lloyd@linux:~$sudo apt-get update && sudo apt-get install kodi
Hit:1http://us.archive.ubuntu.com/ubuntu xenial InRelease
Ign:3http://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:4http://archive.canonical.com/ubuntu xenial InRelease                    
Ign:5http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Get:2http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]    
Ign:6http://dl.google.com/linux/earth/deb stable InRelease                   
Hit:7http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease          
Get:8http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]   
Ign:9http://dl.google.com/linux/talkplugin/deb stable InRelease              
Hit:10http://dl.google.com/linux/chrome/deb stable Release                   
Hit:11http://dl.google.com/linux/earth/deb stable Release                    
Get:12http://us.archive.ubuntu.com/ubuntu xenial-backports Release [101 kB]
Ign:13http://security.ubuntu.com/ubuntu xenial-security/main Sources         
Err:14http://dl.google.com/linux/chrome/deb stable Release.gpg         
 The following signatures were invalid: BADSIG 1397BC53640DB551 GoogleInc. (Linux Packages Signing Authority)<linux-packages-keymaster@google.com>
Get:15http://us.archive.ubuntu.com/ubuntu xenial-backports Release.gpg [916B]
Hit:16http://dl.google.com/linux/talkplugin/deb stable Release               
Err:17http://dl.google.com/linux/earth/deb stable Release.gpg                
 The following signatures were invalid: BADSIG 1397BC53640DB551 GoogleInc. (Linux Packages Signing Authority)<linux-packages-keymaster@google.com>
Ign:18http://security.ubuntu.com/ubuntu xenial-security/restricted Sources
Ign:19http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64Packages
Ign:20http://security.ubuntu.com/ubuntu xenial-security/universe Sources     
Ign:21http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386Packages
Hit:23http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverseTranslation-en
Get:24http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64DEP-11 Metadata [5,892 B]
Hit:25http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-1164x64 Icons
Ign:26http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64Packages
Ign:23http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverseTranslation-en
Err:25http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-1164x64 Icons
 Hash Sum mismatch
Ign:27http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources   
Ign:28http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages  
Hit:29http://us.archive.ubuntu.com/ubuntu xenial-updates/mainTranslation-en
Ign:30http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11Metadata
Ign:31http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Hit:32http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64Icons
Hit:33http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64Packages
Hit:34http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted i386Packages
Hit:35http://us.archive.ubuntu.com/ubuntu xenial-updates/restrictedTranslation-en
Get:36http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64DEP-11 Metadata [157 B]
Hit:37http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64Packages
Hit:38http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386Packages
Ign:39http://us.archive.ubuntu.com/ubuntu xenial-backports/main Sources      
Ign:40http://us.archive.ubuntu.com/ubuntu xenial-backports/universe Sources  
Ign:41http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages   
Ign:42http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64Packages
Ign:43http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386Packages
Ign:44http://security.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:45http://us.archive.ubuntu.com/ubuntu xenial-backports/mainTranslation-en
Get:46http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64DEP-11 Metadata [3,328 B]
Get:47http://us.archive.ubuntu.com/ubuntu xenial-backports/main DEP-1164x64 Icons [29 B]
Get:48http://us.archive.ubuntu.com/ubuntu xenial-backports/restricted amd64DEP-11 Metadata [194 B]
Ign:49http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64Packages
Get:50http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11Metadata [60.3 kB]
Get:51http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64Icons [57.6 kB]
Ign:52http://security.ubuntu.com/ubuntu xenial-security/restricted amd64Packages
Ign:53http://us.archive.ubuntu.com/ubuntu xenial-backports/universe i386Packages
Ign:54http://security.ubuntu.com/ubuntu xenial-security/restricted i386Packages
Ign:55http://us.archive.ubuntu.com/ubuntu xenial-backports/universeTranslation-en
Get:56http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64DEP-11 Metadata [4,584 B]
Ign:57http://us.archive.ubuntu.com/ubuntu xenial-backports/universe DEP-1164x64 Icons
Ign:58http://security.ubuntu.com/ubuntu xenial-security/restrictedTranslation-en
Ign:59http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64DEP-11 Metadata
Ign:60http://security.ubuntu.com/ubuntu xenial-security/restricted amd64DEP-11 Metadata
Hit:61http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverseDEP-11 64x64 Icons
Ign:39http://us.archive.ubuntu.com/ubuntu xenial-backports/main Sources
Ign:40http://us.archive.ubuntu.com/ubuntu xenial-backports/universe Sources  
Ign:62http://security.ubuntu.com/ubuntu xenial-security/universe amd64Packages
Ign:42http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64Packages
Ign:63http://security.ubuntu.com/ubuntu xenial-security/universe i386Packages
Ign:43http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386Packages 
Ign:45http://us.archive.ubuntu.com/ubuntu xenial-backports/mainTranslation-en
Ign:64http://security.ubuntu.com/ubuntu xenial-security/universeTranslation-en
Ign:49http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64Packages
Ign:53http://us.archive.ubuntu.com/ubuntu xenial-backports/universe i386Packages
Get:65http://security.ubuntu.com/ubuntu xenial-security/universe amd64DEP-11 Metadata [51.3 kB]
Get:66http://security.ubuntu.com/ubuntu xenial-security/universe DEP-1164x64 Icons [85.1 kB]
Ign:67http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64Packages
Ign:55http://us.archive.ubuntu.com/ubuntu xenial-backports/universeTranslation-en
Get:57http://us.archive.ubuntu.com/ubuntu xenial-backports/universe DEP-1164x64 Icons [2,717 B]
Ign:59http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64DEP-11 Metadata
Ign:68http://security.ubuntu.com/ubuntu xenial-security/multiverse i386Packages
Get:39http://us.archive.ubuntu.com/ubuntu xenial-backports/main Sources[3,506 B]
Get:40http://us.archive.ubuntu.com/ubuntu xenial-backports/universe Sources[4,586 B]
Get:42http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64Packages [5,176 B]
Get:43http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386Packages [5,163 B]
Get:45http://us.archive.ubuntu.com/ubuntu xenial-backports/mainTranslation-en [3,234 B]
Get:49http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64Packages [6,354 B]
Ign:53http://us.archive.ubuntu.com/ubuntu xenial-backports/universe i386Packages
Ign:69http://security.ubuntu.com/ubuntu xenial-security/multiverseTranslation-en
Ign:55http://us.archive.ubuntu.com/ubuntu xenial-backports/universeTranslation-en
Hit:59http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64DEP-11 Metadata
Err:53http://us.archive.ubuntu.com/ubuntu xenial-backports/universe i386Packages
 Could not open file/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-i386_Packages.xz- open (13: Permission denied) [IP: 2001:67c:1562::16 80]
Ign:70http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64DEP-11 Metadata
Ign:55http://us.archive.ubuntu.com/ubuntu xenial-backports/universeTranslation-en
Ign:71http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-1164x64 Icons
Ign:13http://security.ubuntu.com/ubuntu xenial-security/main Sources
Ign:18http://security.ubuntu.com/ubuntu xenial-security/restricted Sources
Ign:20http://security.ubuntu.com/ubuntu xenial-security/universe Sources
Ign:27http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources
Ign:31http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:41http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:44http://security.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:52http://security.ubuntu.com/ubuntu xenial-security/restricted amd64Packages
Ign:54http://security.ubuntu.com/ubuntu xenial-security/restricted i386Packages
Ign:58http://security.ubuntu.com/ubuntu xenial-security/restrictedTranslation-en
Ign:60http://security.ubuntu.com/ubuntu xenial-security/restricted amd64DEP-11 Metadata
Ign:62http://security.ubuntu.com/ubuntu xenial-security/universe amd64Packages
Ign:63http://security.ubuntu.com/ubuntu xenial-security/universe i386Packages
Ign:64http://security.ubuntu.com/ubuntu xenial-security/universeTranslation-en
Ign:67http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64Packages
Ign:68http://security.ubuntu.com/ubuntu xenial-security/multiverse i386Packages
Ign:69http://security.ubuntu.com/ubuntu xenial-security/multiverseTranslation-en
Ign:70http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64DEP-11 Metadata
Get:71http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-1164x64 Icons [29 B]
Ign:13http://security.ubuntu.com/ubuntu xenial-security/main Sources         
Get:18http://security.ubuntu.com/ubuntu xenial-security/restricted Sources[2,770 B]
Get:20http://security.ubuntu.com/ubuntu xenial-security/universe Sources[51.1 kB]
Get:27http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources[1,077 B]
Get:31http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages[486 kB]
Ign:41http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages   
Ign:44http://security.ubuntu.com/ubuntu xenial-security/main Translation-en  
Get:52http://security.ubuntu.com/ubuntu xenial-security/restricted amd64Packages [12.9 kB]
Get:54http://security.ubuntu.com/ubuntu xenial-security/restricted i386Packages [13.0 kB]
Get:58http://security.ubuntu.com/ubuntu xenial-security/restrictedTranslation-en [2,479 B]
Err:60http://security.ubuntu.com/ubuntu xenial-security/restricted amd64DEP-11 Metadata
 Could not open file/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz- open (13: Permission denied) [IP: 91.189.91.23 80]
Get:62http://security.ubuntu.com/ubuntu xenial-security/universe amd64Packages [223 kB]
Get:63http://security.ubuntu.com/ubuntu xenial-security/universe i386Packages [192 kB]
Get:64http://security.ubuntu.com/ubuntu xenial-security/universeTranslation-en [121 kB]
Get:67http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64Packages [3,485 B]
Get:68http://security.ubuntu.com/ubuntu xenial-security/multiverse i386Packages [3,676 B]
Ign:69http://security.ubuntu.com/ubuntu xenial-security/multiverseTranslation-en
Hit:70http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64DEP-11 Metadata
Ign:13http://security.ubuntu.com/ubuntu xenial-security/main Sources
Ign:41http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages   
Ign:44http://security.ubuntu.com/ubuntu xenial-security/main Translation-en  
Readingpackage lists... Done                                                 
N:Ignoring file 'google-' in directory '/etc/apt/sources.list.d/' as ithas no filename extension
E:Splitting of file/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_xenial_InReleasefailed as it doesn't contain all expected parts 0 1 0
W:An error occurred during the signature verification. The repositoryis not updated and the previous index files will be used. GPG error:[http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: The followingsignatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (LinuxPackages Signing Authority) <linux-packages-keymaster@google.com>
W:An error occurred during the signature verification. The repositoryis not updated and the previous index files will be used. GPG error:[http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release: The followingsignatures were invalid: BADSIG 1397BC53640DB551 Google Inc. (LinuxPackages Signing Authority) <linux-packages-keymaster@google.com>
lloyd@linux:~$exit
```

Can anyone tell me how to fix the problem? 
I'm using 16.04 on a homemade AMD64 with plenty of storage and memory

---

### Post by Frogs Hair on 2017-11-11
See the red text below.


[COLOR=#333333][FONT=Ubuntu]For questions and bugs with software in this PPA please contact [/FONT][/COLOR][Kodi]("https://launchpad.net/~team-xbmc")[COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]

```
gpg:keyring `/tmp/tmpfbq36b0l/secring.gpg' created
gpg:keyring `/tmp/tmpfbq36b0l/pubring.gpg' created
gpg:requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg:/tmp/tmpfbq36b0l/trustdb.gpg: trustdb created
gpg:key 91E7EE5E: public key "Launchpad PPA for XBMC for Linux"imported
[COLOR=#ff0000]gpg:no ultimately trusted keys found[/COLOR]
gpg:Total number processed: 1
gpg:              imported: 1  (RSA: 1)
OK
```

---

### Post by mc4man on 2017-11-11
Odds are your issue lies somewhere other than the kodi ppa specifically (that trust deal is common & not that important

Ex. - 
```
$ sudo add-apt-repository ppa:team-xbmc/ppa
[sudo] password for doug: 
 
 More info: https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpm3vdtoos/secring.gpg' created
gpg: keyring `/tmp/tmpm3vdtoos/pubring.gpg' created
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpm3vdtoos/trustdb.gpg: trustdb created
gpg: key 91E7EE5E: public key "Launchpad PPA for XBMC for Linux" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```
```
$ sudo apt update
.....
Get:59 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial/main amd64 Packages [20.0 kB]                      
Get:60 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial/main i386 Packages [20.0 kB]                       
Get:61 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial/main Translation-en [5,796 B]         
......
```
```
$ sudo apt -s install kodi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-26 linux-headers-4.10.0-26-generic linux-image-4.10.0-26-generic linux-image-extra-4.10.0-26-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  kodi-bin libcec4 libcrossguid1 libmicrohttpd10 libmysqlclient20 libnfs8 libp8-platform2 libshairplay0 libtinyxml2.6.2v5
  mysql-common python-bluez python-imaging python-pil
Suggested packages:
  kodi-pvr-mythtv kodi-pvr-vuplus kodi-pvr-vdr-vnsi kodi-pvr-njoy kodi-pvr-nextpvr kodi-pvr-mediaportal-tvserver
  kodi-pvr-tvheadend-hts kodi-pvr-dvbviewer kodi-pvr-argustv kodi-pvr-iptvsimple kodi-audioencoder-vorbis kodi-audioencoder-flac
  kodi-audioencoder-lame python-pil-doc python-pil-dbg
The following NEW packages will be installed:
  kodi kodi-bin libcec4 libcrossguid1 libmicrohttpd10 libmysqlclient20 libnfs8 libp8-platform2 libshairplay0 libtinyxml2.6.2v5
  mysql-common python-bluez python-imaging python-pil
0 upgraded, 14 newly installed, 0 to remove and 57 not upgraded.
Inst libcrossguid1 (0.1~git20150807.8f399e8~xenial Kodi stable:16.04/xenial [amd64])
Inst libmicrohttpd10 (0.9.44+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])
Inst mysql-common (5.7.20-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Inst libmysqlclient20 (5.7.20-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst libtinyxml2.6.2v5 (2.6.2-3 Ubuntu:16.04/xenial [amd64])
Inst kodi-bin (2:17.5+git20171026.2109-final-0xenial Kodi stable:16.04/xenial [amd64])
Inst python-bluez (0.22-1 Ubuntu:16.04/xenial [amd64])
Inst python-pil (3.1.2-0ubuntu1.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst python-imaging (3.1.2-0ubuntu1.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Inst libnfs8 (1.9.8-1 Ubuntu:16.04/xenial [amd64])
Inst libshairplay0 (0.9.0.1-2~xenial Kodi stable:16.04/xenial [amd64])
Inst libp8-platform2 (2.1.0.1~xenial Kodi stable:16.04/xenial [amd64])
Inst libcec4 (4.0.1.1~xenial Kodi stable:16.04/xenial [amd64])
Inst kodi (2:17.5+git20171026.2109-final-0xenial Kodi stable:16.04/xenial [all])
Conf libcrossguid1 (0.1~git20150807.8f399e8~xenial Kodi stable:16.04/xenial [amd64])
Conf libmicrohttpd10 (0.9.44+dfsg-1ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf mysql-common (5.7.20-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Conf libmysqlclient20 (5.7.20-0ubuntu0.16.04.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf libtinyxml2.6.2v5 (2.6.2-3 Ubuntu:16.04/xenial [amd64])
Conf kodi-bin (2:17.5+git20171026.2109-final-0xenial Kodi stable:16.04/xenial [amd64])
Conf python-bluez (0.22-1 Ubuntu:16.04/xenial [amd64])
Conf python-pil (3.1.2-0ubuntu1.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf python-imaging (3.1.2-0ubuntu1.1 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Conf libnfs8 (1.9.8-1 Ubuntu:16.04/xenial [amd64])
Conf libshairplay0 (0.9.0.1-2~xenial Kodi stable:16.04/xenial [amd64])
Conf libp8-platform2 (2.1.0.1~xenial Kodi stable:16.04/xenial [amd64])
Conf libcec4 (4.0.1.1~xenial Kodi stable:16.04/xenial [amd64])
Conf kodi (2:17.5+git20171026.2109-final-0xenial Kodi stable:16.04/xenial [all])
```

---

