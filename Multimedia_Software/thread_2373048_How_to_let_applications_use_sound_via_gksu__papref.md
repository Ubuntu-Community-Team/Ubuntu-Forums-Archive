---
title: "How to let applications use sound via gksu / paprefs uninstallable"
date: 2017-10-02
forum: Multimedia Software
---

### Post by kevin77v on 2017-10-02
My goal is to be able to run applications with gksu and have them use Pulseaudio.  Currently they are unable to access Pulseaudio, which I assume is a permissions issue. Previously, I believe I achieved this by turning on "Make discoverable PulseAudio network sound device available locally" in the "Network Server" tab of the 'paprefs' program.  However, for reasons I do not understand, I cannot install paprefs.  I get the following message from apt-get:   
[edit: the actually option that enables other users to access sound is ¨Enable network access to local sound devices¨]

```
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
```

```
The following packages have unmet dependencies:  paprefs : Depends: pulseaudio-module-gconf but it is not going to be installed             Depends: pulseaudio-module-zeroconf but it is not going to be install.
```

 Digging deeper, both the -gconf and -zerconf packages give the following dependency problem:

   ```
"The following packages have unmet dependencies:  pulseaudio-module-gconf : Depends: libpulse0 (= 1:8.0-0ubuntu3) but 1:8.0-0ubuntu3.4 is to be installed"   
```

I don't know if it's possible to resolve this.  

I'm using Xubuntu 16.04.    

However, while the paprefs dependency problem is an interesting problem on its own, if I can do manually whatever the "Make discoverable PulseAudio network sound device available locally" option does behind the scenes, I imagine I can get this solved.  Or, getting paprefs to work would do it too.  Can anyone provide me with a way to achieve either getting paprefs installed, or what configuation I need to manually set to achieve what paprefs does?

---

### Post by mc4man on 2017-10-02
Check your sources as there is no reason you can't install paprefs.
Example here (simulation
> $ sudo apt -s install paprefs
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libgconfmm-2.6-1v5 libglade2-0 libglademm-2.4-1v5 libgtkmm-2.4-1v5 pulseaudio-module-gconf pulseaudio-module-zeroconf
The following NEW packages will be installed:
  libgconfmm-2.6-1v5 libglade2-0 libglademm-2.4-1v5 libgtkmm-2.4-1v5 paprefs pulseaudio-module-gconf
  pulseaudio-module-zeroconf
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Inst libglade2-0 (1:2.6.4-2 Ubuntu:16.04/xenial [amd64])
Inst libgconfmm-2.6-1v5 (2.28.3-0ubuntu3 Ubuntu:16.04/xenial [amd64])
Inst libgtkmm-2.4-1v5 (1:2.24.4-2 Ubuntu:16.04/xenial [amd64])
Inst libglademm-2.4-1v5 (2.6.7-5 Ubuntu:16.04/xenial [amd64])
Inst pulseaudio-module-gconf (1:8.0-0ubuntu3.4 Ubuntu:16.04/xenial-updates [amd64])
Inst pulseaudio-module-zeroconf (1:8.0-0ubuntu3.4 Ubuntu:16.04/xenial-updates [amd64])
Inst paprefs (0.9.10-2 Ubuntu:16.04/xenial [amd64])
Conf libglade2-0 (1:2.6.4-2 Ubuntu:16.04/xenial [amd64])
Conf libgconfmm-2.6-1v5 (2.28.3-0ubuntu3 Ubuntu:16.04/xenial [amd64])
Conf libgtkmm-2.4-1v5 (1:2.24.4-2 Ubuntu:16.04/xenial [amd64])
Conf libglademm-2.4-1v5 (2.6.7-5 Ubuntu:16.04/xenial [amd64])
Conf pulseaudio-module-gconf (1:8.0-0ubuntu3.4 Ubuntu:16.04/xenial-updates [amd64])
Conf pulseaudio-module-zeroconf (1:8.0-0ubuntu3.4 Ubuntu:16.04/xenial-updates [amd64])
Conf paprefs (0.9.10-2 Ubuntu:16.04/xenial [amd64])

If need be check some deps, ex.
apt-cache policy pulseaudio-module-gconf

```
$ apt-cache policy pulseaudio-module-gconf 
pulseaudio-module-gconf:
  Installed: (none)
  Candidate: 1:8.0-0ubuntu3.4
  Version table:
     1:8.0-0ubuntu3.4 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     1:8.0-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```

---

### Post by kevin77v on 2017-10-03
That is the switch (-s) I did to create the output there.

In any case, I didn´t solve ëither of the two problems.  Instead, I reinstalled the whole system.  Only, I didn´t install any of the security updates until after I had everything I wanted installed.  I was able to install everything and use paprefs as normal.  As the error messages suggest, I think that the security updates probably broke the packages.

---

