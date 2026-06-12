---
title: "Ubuntu 20.04 LTS Kodi 18.6&gt;18.8 PVR Simple IPTV NOK! Help"
date: 2020-10-08
forum: Multimedia Software
---

### Post by donnywood-studio on 2020-10-08
HI Folks

Upgrade from 18.04 LTS- 20.04 LTS was fine and very good for a week now. 

A new Kodi update was installed as normal update today morning from Kodi 18.6 to 18.8 and now PVR Simple IPTV client is missing. 
Kodi 18.8 is working but only the PVR is not going . I have been using Simple IPTV since Ubuntu 16.04LTS and worked until Kodi18.8 under 20.04LTS

Tried install it manually as per Ubuntu Official Site and Kodi Site 
_[COLOR=#0000ff]https://ubuntu.pkgs.org/20.04/ubuntu-universe-amd64/kodi-pvr-iptvsimple_3.9.8-1_amd64.deb.html[/COLOR]_

Go the following [SIZE=4][COLOR=#ff0000]**error **[/COLOR][/SIZE]

ing@wing-Aspire-V3-571G:~$ **[COLOR=#008000]sudo apt-get install kodi-pvr-iptvsimple[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 [B][COLOR=#ff0000]kodi-pvr-iptvsimple : Depends: kodi-api-pvr (= 5.10.3)
E: Unable to correct problems, you have held broken packages.

[/COLOR][/B][SIZE=2]Started to follow the error but just getting into a rabbit hole... 

Any pointers would be much appreciated. 
rgds
Don 
[/SIZE]
[SIZE=2]_**Below What was done . **_[/SIZE][INDENT]wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**sudo apt-get install kodi-api-pvr**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#ff0000]Package kodi-api-pvr is a virtual package provided by:
  kodi 2:18.6+dfsg1-2ubuntu1 [Not candidate version][/COLOR]

E: Package 'kodi-api-pvr' has no installation candidate
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**sudo apt-get install kodi 2:18.6+dfsg1-2ubuntu1**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#ff0000]E: Unable to locate package 2:18.6+dfsg1-2ubuntu1
E: Couldn't find any package by glob '2:18.6+dfsg1-2ubuntu1'
E: Couldn't find any package by regex '2:18.6+dfsg1-2ubuntu1'
wing@wing-Aspire-V3-571G:~$ [/COLOR]

[/INDENT]
[U][B]Checking requirement for Simple IPTV
[/B][/U]ing@wing-Aspire-V3-571G:~$ **[COLOR=#008000]lsb_release -a[/COLOR]**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**uname -a**[/COLOR]
Linux wing-Aspire-V3-571G 5.4.0-48-generic #52-Ubuntu SMP Thu Sep 10 10:58:49 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
wing@wing-Aspire-V3-571G:~$ **[COLOR=#008000]grep kodi dpkg-query-l[/COLOR]**
ii  kodi                                        2:18.8+git20200728.1313-final-0focal all          Kodi Media Center (arch-independent data package)
ii  kodi-inputstream-adaptive                   2.4.5-1~focal                        amd64        adaptive inputstream addon for Kodi
ii  kodi-peripheral-joystick                    1.5.2-1~focal                        amd64        Joystick peripheral addon for Kodi
ii  kodi-visualization-spectrum                 3.0.4-1~focal                        amd64        Spectrum visualizer for Kodi
ii  kodi-x11                                    2:18.8+git20200728.1313-final-0focal amd64        Kodi Media Center for X11 (binary data package)
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**grep libc6 dpkg-query-l**[/COLOR]
ii  libc6:amd64                                 2.31-0ubuntu9.1                      amd64        GNU C Library: Shared libraries
ii  libc6:i386                                  2.31-0ubuntu9.1                      i386         GNU C Library: Shared libraries
ii  libc6-dbg:amd64                             2.31-0ubuntu9.1                      amd64        GNU C Library: detached debugging symbols
ii  libc6-dev:amd64                             2.31-0ubuntu9.1                      amd64        GNU C Library: Development Libraries and Header Files
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**grep libgcc-s1 dpkg-query-l**[/COLOR]
ii  libgcc-s1:amd64                             10.2.0-5ubuntu1~20.04                amd64        GCC support library
ii  libgcc-s1:i386                              10.2.0-5ubuntu1~20.04                i386         GCC support library
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**grep libp8-platform2 dpkg-query-l**[/COLOR]
ii  libp8-platform2:amd64                       2.1.0.1+dfsg1-3build1                amd64        Pulse-Eight's platform support library
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**grep libstdc++6 dpkg-query-l**[/COLOR]
ii  libstdc++6:amd64                            10.2.0-5ubuntu1~20.04                amd64        GNU Standard C++ Library v3
ii  libstdc++6:i386                             10.2.0-5ubuntu1~20.04                i386         GNU Standard C++ Library v3
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**grep zlib1g dpkg-query-l**[/COLOR]
ii  zlib1g:amd64                                1:1.2.11.dfsg-2ubuntu1.1             amd64        compression library - runtime
ii  zlib1g:i386                                 1:1.2.11.dfsg-2ubuntu1.1             i386         compression library - runtime
ii  zlib1g-dev:amd64                            1:1.2.11.dfsg-2ubuntu1.1             amd64        compression library - development
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**sudo apt-get install kodi**[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kodi is already the newest version (2:18.8+git20200728.1313-final-0focal).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**sudo add-apt-repository ppa:team-xbmc/ppa**[/COLOR]
 Official Team Kodi stable releases
 More info: [https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                            
Hit:3 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                                
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                                                                                          
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                          
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease                                      
Hit:7 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) focal InRelease
Reading package lists... Done
wing@wing-Aspire-V3-571G:~$ **[COLOR=#008000]sudo apt-get update[/COLOR]**
Hit:1 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                                
Hit:3 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                                              
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                     
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease                                                                                                 
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease           
Hit:7 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) focal InRelease
Reading package lists... Done
wing@wing-Aspire-V3-571G:~$ **[COLOR=#008000]sudo apt-get install kodi-pvr-iptvsimple[/COLOR]**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kodi-pvr-iptvsimple : Depends: kodi-api-pvr (= 5.10.3)
E: Unable to correct problems, you have held broken packages.

---

### Post by TheFu on 2020-10-09
```
you have held broken packages
```
Fix those.

I think synaptic has a "fix broken packages" button.

In general, those are caused by installed .deb files directly, not through curated Canonical packages.  The fix would be to remove those manually installed .deb files, get the APT system where it doesn't complain, then seek newer versions of the manual .deb file, if they aren't in the repos now.  Keep a list of all manually installed .deb files, so next time this happens, probably in about 6 months, you don't have to hunt them down manually.

IMHO.

I use kodi, but don't use Simple IPTV.  Have Kodi running on 3 systems - 2 r-pis and 1 x64 box.  The version I'm using on the x64 box is 2:18.8+git20200728.1313-final-0xenial. The PPA I use is [https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa) with instructions to install. It appears to be maintained.

For recording TV, I use some custom scripts that only work with HDHR hardware and broadcast TV.

---

### Post by Tadaen_Sylvermane on 2020-10-09
The ppa is the only supported way to run and it is always maintained. Kodi forums won't help if you aren't using ppa or self compiled. Ubuntu packages have modifications that the Kodi people dont use for various reasons.

Normally I'd say stick with Ubuntu repos. In this case though the Kodi ppa is the only way to get exactly what they intended. Using it for years, never an issue.

---

### Post by donnywood-studio on 2020-10-09
Found a solution from launchpad.net and Kodi team

[COLOR=#008000]***sudo apt install kodi-pvr-iptvsimple=3.9.8-1~focal***[/COLOR]

Works perfectly .. 

**Explanation**

*************************
the problem is that ubuntu pulled debians iptvsimple package.
[https://launchpad.net/ubuntu/+source/kod...le/3.9.8-1]("https://launchpad.net/ubuntu/+source/kodi-pvr-iptvsimple/3.9.8-1") is NOT our ppa package, but it's official ubuntu, and the version is "higher" than ours: [https://launchpad.net/~team-xbmc/+archiv...hive-extra]("https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa/+sourcepub/11176238/+listing-archive-extra")

Until we release a newer version, you can install our package like this: apt install kodi-pvr-iptvsimple=3.9.8-1~focal
Obviously, you need our PPA enabled.
***************************************

**OUTPUT AFTER INSTALL**
=====================

wing@wing-Aspire-V3-571G:~$ grep kodi l
ii  kodi                                        2:18.8+git20200728.1313-final-0focal all          Kodi Media Center (arch-independent data package)
ii  kodi-inputstream-adaptive                   2.4.5-1~focal                        amd64        adaptive inputstream addon for Kodi
ii  kodi-peripheral-joystick                    1.5.2-1~focal                        amd64        Joystick peripheral addon for Kodi
ii  kodi-pvr-iptvsimple                         3.9.8-1~focal                        amd64        Simple IPTV PVR for Kodi
ii  kodi-x11                                    2:18.8+git20200728.1313-final-0focal amd64        Kodi Media Center for X11 (binary data package)
wing@wing-Aspire-V3-571G:~$ [COLOR=#008000]**apt-cache policy kodi**[/COLOR]
kodi:
  Installed: 2:18.8+git20200728.1313-final-0focal
  Candidate: 2:18.8+git20200728.1313-final-0focal
  Version table:
 *** 2:18.8+git20200728.1313-final-0focal 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) focal/main amd64 Packages
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) focal/main i386 Packages
        100 /var/lib/dpkg/status
     2:18.6+dfsg1-2ubuntu1 500
        500 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
wing@wing-Aspire-V3-571G:~$ **[COLOR=#008000]apt-cache policy kodi-pvr-iptvsimple[/COLOR]**
kodi-pvr-iptvsimple:
  Installed: 3.9.8-1~focal
  Candidate: 3.9.8-1
  Version table:
     3.9.8-1 500
        500 [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
 *** 3.9.8-1~focal 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) focal/main amd64 Packages
        100 /var/lib/dpkg/status
wing@wing-Aspire-V3-571G:~$ 




cheers

---

