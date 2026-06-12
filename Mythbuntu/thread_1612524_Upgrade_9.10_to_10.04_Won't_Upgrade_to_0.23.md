---
title: "Upgrade 9.10 to 10.04: Won't Upgrade to 0.23"
date: 2010-11-03
forum: Mythbuntu
---

### Post by JWB47 on 2010-11-03
Last night I decided to upgrade my myth box from 9.10 mythtv 0.22 fixes 22862. When it all completed, I was still at 0.22, there were no 0.23 packages installed. 

I then ran mythbuntu-repos, selected 0.23, did a reload and a few 0.23 packages appeared, but no update to a complete 0.23. 

As a note, during the upgrade I responded to a dialog to keep the current DB. Was this the problem?

Anyways, I would appreciate any help in getting this box to a 0.23 version that is consistent.

The following is what is currently installed for mythbuntu.

================
$ dpkg -l | grep myth
ii  gtk2-engines-mythbuntu                     0.4-0ubuntu2
rc  libmyth-0.21-0                             2:0.21.0+fixes-22228-openglvdpau2-0ubuntu0
ii  libmyth-0.22-0                             2:0.22.0-fixes22862-0ubuntu1
ii  libmyth-0.23-0                             0.23.1+fixes26863-0ubuntu0+mythbuntu2
ii  libmyth-perl                               2:0.22.0-fixes22862-0ubuntu1
ii  libmyth-python                             2:0.22.0-fixes22862-0ubuntu1
ii  mytharchive                                2:0.22.0-fixes22864-0ubuntu1
ii  mytharchive-data                           2:0.22.0-fixes22864-0ubuntu1
ii  mythbrowser                                0.23.1+fixes26863-0ubuntu0+mythbuntu2
ii  mythbuntu-3rd-party-frontends              1-0ubuntu1+mythbuntu~lucid
ii  mythbuntu-common                           0.50-0ubuntu1
ii  mythbuntu-control-centre                   0.62-0ubuntu1
ii  mythbuntu-default-settings                 0.96-0ubuntu1
ii  mythbuntu-desktop                          0.59
ii  mythbuntu-gdm-theme                        0.6-0ubuntu1
ii  mythbuntu-lirc-generator                   0.25-0ubuntu1~ppa1
ii  mythbuntu-log-grabber                      0.7-0ubuntu2
ii  mythbuntu-repos                            8.7-0ubuntu0+mythbuntu~auto20101030003223
rc  mythexport                                 2.1.3-0ubuntu1
ii  mythgallery                                2:0.22.0-fixes22864-0ubuntu1
ii  mythmovies                                 2:0.22.0-fixes22864-0ubuntu1
ii  mythmusic                                  2:0.22.0-fixes22864-0ubuntu1
ii  mythnews                                   0.23.1+fixes26863-0ubuntu0+mythbuntu2
ii  mythtv                                     2:0.22.0-fixes22862-0ubuntu1
ii  mythtv-backend                             2:0.22.0-fixes22862-0ubuntu1
ii  mythtv-backend-master                      2:0.22.0-fixes22862-0ubuntu1
ii  mythtv-common                              2:0.22.0-fixes22862-0ubuntu1
ii  mythtv-database                            2:0.22.0-fixes22862-0ubuntu1
ii  mythtv-frontend                            2:0.22.0-fixes22862-0ubuntu1
ii  mythtv-theme-blootube-osd                  2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-blueosd                       2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-childish                      1:0.23.1+fixes26863-0ubuntu0+mythbuntu2
ii  mythtv-theme-graphite                      2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-iulius-osd                    2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-metallurgy                    2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-mono-osd                      2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-mythbuntu                     2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-projectgrayhem-osd            2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-retro-osd                     2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-theme-titivillus-osd                2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-themes                              2:0.22.0-fixes22793-0ubuntu2
ii  mythtv-transcode-utils                     2:0.22.0-fixes22862-0ubuntu1
ii  mythvideo                                  2:0.22.0-fixes22864-0ubuntu1
ii  mythweather                                2:0.22.0-fixes22864-0ubuntu1
ii  mythweb                                    2:0.22.0-fixes22864-0ubuntu1
=============

Thanks for your Help

John

---

### Post by tgm4883 on 2010-11-03
Thats odd, you do have some 0.23.1 packages installed. What happens if you do an apt-get install mythtv-frontend

---

### Post by JWB47 on 2010-11-03
> **tgm4883 said:**
> Thats odd, you do have some 0.23.1 packages installed. What happens if you do an apt-get install mythtv-frontend
Trying to install mythtv-frontend, I get the following output from apt-get:

================
$ sudo apt-get install mythtv-frontend

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mythtv-frontend is already the newest version.
mythtv-frontend set to manually installed.
The following packages were automatically installed and are no longer required:
  libstdc++5 libxml-rss-perl nvidia-185-kernel-source libproc-pid-file-perl
  liblog-dispatch-perl nvidia-185-modaliases libdatetime-format-w3cdtf-perl
  libproc-daemon-perl libdatetime-format-mail-perl atomicparsley
  libconfig-simple-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
===============

John

---

### Post by tgm4883 on 2010-11-03
> **JWB47 said:**
> Trying to install mythtv-frontend, I get the following output from apt-get:

================
$ sudo apt-get install mythtv-frontend

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mythtv-frontend is already the newest version.
mythtv-frontend set to manually installed.
The following packages were automatically installed and are no longer required:
  libstdc++5 libxml-rss-perl nvidia-185-kernel-source libproc-pid-file-perl
  liblog-dispatch-perl nvidia-185-modaliases libdatetime-format-w3cdtf-perl
  libproc-daemon-perl libdatetime-format-mail-perl atomicparsley
  libconfig-simple-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
===============

John


Hmm, ok, whats the output of

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list
```

---

### Post by JWB47 on 2010-11-03
> **tgm4883 said:**
> Hmm, ok, whats the output of

```
cat /etc/apt/sources.list.d/mythbuntu-repos.list
```
The output requested is:

===============
cat /etc/apt/sources.list.d/mythbuntu-repos.list

deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
deb-src [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
===============

I forgot to mention on the earlier reply, that as a part of my trying to figure things out last night, I set mythbuntu-repos to 023.1, the packages indicated were the only ones installed.

John

---

### Post by tgm4883 on 2010-11-03
> **JWB47 said:**
> The output requested is:

===============
cat /etc/apt/sources.list.d/mythbuntu-repos.list

deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
deb-src [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23/ubuntu) lucid main
===============

I forgot to mention on the earlier reply, that as a part of my trying to figure things out last night, I set mythbuntu-repos to 023.1, the packages indicated were the only ones installed.

John

Hmm ok, your sources show 0.23.0, not 0.23.1 is selected, you may want to check that. 

Did you do a apt-get update after you activated the 0.23.1 repo before you did an apt-get upgrade?

---

### Post by JWB47 on 2010-11-03
> **tgm4883 said:**
> Hmm ok, your sources show 0.23.0, not 0.23.1 is selected, you may want to check that. 

Did you do a apt-get update after you activated the 0.23.1 repo before you did an apt-get upgrade?
OK, I set the version to 0.23.1: here is the sources list.

==================
$ cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu) lucid main
deb-src [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main
===================

I ran apt-get update and then apt-get upgrade. Here is the result.

=================
sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/mythbuntu/repos/ubuntu/](http://ppa.launchpad.net/mythbuntu/repos/ubuntu/) lucid/main Translation-en_CA
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Get:2 [http://us.autobuilds.mythbuntu.org](http://us.autobuilds.mythbuntu.org) lucid Release.gpg [316B]              
Ign [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu/](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu/) lucid/main Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   

...

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release                         

...

Get:6 [http://us.autobuilds.mythbuntu.org](http://us.autobuilds.mythbuntu.org) lucid/main Sources [2,277B]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [2,660B]                  
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources [1,856B]                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 130kB in 1s (97.5kB/s)                
Reading package lists... Done
jwb@phoenix:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
=================

I removed some lines from the update download report to save space. As you can see, it doesn't want to do anything.

Trying out apt-get install mythtv-frontend as earlier, no longer says "mythtv-frontend set to manual install". The rest of the output is the same as in post #3.

John

---

### Post by JWB47 on 2010-11-04
> **JWB47 said:**
> OK, I set the version to 0.23.1: here is the sources list.

==================
$ cat /etc/apt/sources.list.d/mythbuntu-repos.list
deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) lucid main
deb [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu) lucid main
deb-src [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu) lucid main
deb [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/mythbuntu/testing/ubuntu](http://ppa.launchpad.net/mythbuntu/testing/ubuntu) lucid main
===================

I ran apt-get update and then apt-get upgrade. Here is the result.

=================
sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/mythbuntu/repos/ubuntu/](http://ppa.launchpad.net/mythbuntu/repos/ubuntu/) lucid/main Translation-en_CA
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Get:2 [http://us.autobuilds.mythbuntu.org](http://us.autobuilds.mythbuntu.org) lucid Release.gpg [316B]              
Ign [http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu/](http://us.autobuilds.mythbuntu.org/mythbuntu/0.23.1/ubuntu/) lucid/main Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   

...

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release                         

...

Get:6 [http://us.autobuilds.mythbuntu.org](http://us.autobuilds.mythbuntu.org) lucid/main Sources [2,277B]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [2,660B]                  
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources [1,856B]                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 130kB in 1s (97.5kB/s)                
Reading package lists... Done
jwb@phoenix:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
=================

I removed some lines from the update download report to save space. As you can see, it doesn't want to do anything.

Trying out apt-get install mythtv-frontend as earlier, no longer says "mythtv-frontend set to manual install". The rest of the output is the same as in post #3.

John
tgm4883:

I have continued to look at this problem and have discovered an oddity that may be a clue. 

Since trying to just install mythtv-frontend, just said it was already at the current release, I tried the install with a forced version. See output below. It seems apt-get now wants to DOWNGRADE mythtv-frontend to install the 0.23.1 version. Odd!

Somewhere in the system, it must think a different version is installed.

I hope this helps.

John

========================
sudo apt-get install mythtv-frontend=0.23.1+fixes26863-0ubuntu0+mythbuntu2
[sudo] password for jwb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 libxml-rss-perl nvidia-185-kernel-source libproc-pid-file-perl
  liblog-dispatch-perl nvidia-185-modaliases libdatetime-format-w3cdtf-perl
  libproc-daemon-perl libdatetime-format-mail-perl atomicparsley
  libconfig-simple-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mythgame
The following packages will be REMOVED:
  mythtv
The following packages will be DOWNGRADED:
  mythtv-frontend
0 upgraded, 0 newly installed, 1 downgraded, 1 to remove and 0 not upgraded.
Need to get 3,964kB of archives.
After this operation, 3,301kB of additional disk space will be used.
===============
John

---

### Post by tgm4883 on 2010-11-04
Ah I see it now after looking more closely at your installed packages

```
mythtv-frontend 2:0.22.0-fixes22862-0ubuntu1
```

You had JYA's packages installed didn't you. From the standpoint of packaging 2:0.22.0 is newer than 0.23.1.

You will need to remove those other packages in order to get this installed

---

### Post by JWB47 on 2010-11-04
> **tgm4883 said:**
> Ah I see it now after looking more closely at your installed packages

```
mythtv-frontend 2:0.22.0-fixes22862-0ubuntu1
```You had JYA's packages installed didn't you. From the standpoint of packaging 2:0.22.0 is newer than 0.23.1.

You will need to remove those other packages in order to get this installed
Thanks tgm4883:

I was thinking that was what I had to do. 

I had the jya repositories enabled when I had originally installed  mythbuntu on this system to get the ION graphics running. I had  forgotten that it was there.

I am now reviewing everything to ensure the system is functioning correctly.

Again, thanks for your help.

John

---

