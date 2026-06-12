---
title: "MythTV broken"
date: 2008-05-05
forum: Mythbuntu
---

### Post by rllacey on 2008-05-05
I was running mythtv fine until I did a restart and now mythbackend/frontend won't start. My recording directories still exist, but everything else is gone. I tried the following with no luck:

```

sudo apt-get install mythtv
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
  mythtv: Depends: mythtv-frontend (= 0.21.0-0ubuntu2~gutsy1) but it is not going to be installed
          Depends: mythtv-backend (= 0.21.0-0ubuntu2~gutsy1) but it is not going to be installed
E: Broken packages



```

My /etc/apt/sources.list is the following:

```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse


```

Someone please help. This is racking my brains. :)

---

### Post by superm1 on 2008-05-06
> **rllacey said:**
> I was running mythtv fine until I did a restart and now mythbackend/frontend won't start. My recording directories still exist, but everything else is gone. I tried the following with no luck:

```

sudo apt-get install mythtv
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
  mythtv: Depends: mythtv-frontend (= 0.21.0-0ubuntu2~gutsy1) but it is not going to be installed
          Depends: mythtv-backend (= 0.21.0-0ubuntu2~gutsy1) but it is not going to be installed
E: Broken packages



```My /etc/apt/sources.list is the following:

```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse


```Someone please help. This is racking my brains. :)
Try opening up Synaptic and doing it from there.  It's a bit more informative as to why it's not letting you.  If it says I can't do it because of package X, try to install package X, and it will tell you what is wrong with package Y that it depends on.

---

### Post by rllacey on 2008-05-06
I seem to be having a similar problem using Synaptic. When I go to install mythtv-backend, it gives me an error of:

```

The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.21.0+trunk16733-0ubuntu0~mythbuntu1) but 0.21.0-0ubuntu2~gutsy1 is to be installed
                  Depends: mythtv-transcode-utils (= 0.21.0+trunk16733-0ubuntu0~mythbuntu1) but it is not going to be installed

```

mythtv-common is installed. I've tried removing it and reinstalling, but still nothing. I've also removed and reinstalled trandcode-utils, but no go there. Still getting same errors. Any suggestions?

---

### Post by superm1 on 2008-05-07
> **rllacey said:**
> I seem to be having a similar problem using Synaptic. When I go to install mythtv-backend, it gives me an error of:

```

The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.21.0+trunk16733-0ubuntu0~mythbuntu1) but 0.21.0-0ubuntu2~gutsy1 is to be installed
                  Depends: mythtv-transcode-utils (= 0.21.0+trunk16733-0ubuntu0~mythbuntu1) but it is not going to be installed

```mythtv-common is installed. I've tried removing it and reinstalling, but still nothing. I've also removed and reinstalled trandcode-utils, but no go there. Still getting same errors. Any suggestions?
This is sounding like you have a third party repository in place.  Do you have any added to your sources.list right now?

If so, please disable them, apt-get update and try agian.

Either way, what's the output of:

```
dpkg -l | grep myth
```

---

### Post by rllacey on 2008-05-07
Here is my dpkg -l | grep myth
```

ii  gtk2-engines-mythbuntu                     0.3-0ubuntu1                          Mythbuntu GTK+ 2.x Theme
ii  libmyth-0.20                               0.20.2-0ubuntu10.1                    Common library code for MythTV and add-on mo
ii  libmyth-0.21-0                             0.21.0+trunk16733-0ubuntu0~mythbuntu1 Common library code for MythTV and add-on mo
ii  libmyth-perl                               0.21.0-0ubuntu2~gutsy1                A PERL library to access some MythTV feature
ii  libmyth-python                             0.21.0-0ubuntu2~gutsy1                A python library to access some MythTV featu
ii  mytharchive-data                           0.21.0-0ubuntu2~gutsy1                create and burn DVD's from MythTV - data fil
ii  mythbuntu-artwork-usplash                  0.6-0ubuntu1                          mythbuntu artwork for usplash
rc  mythbuntu-control-centre                   0.11-0ubuntu1~ppa1                    Mythbuntu Configuration Application
ii  mythbuntu-default-settings                 0.63-0ubuntu1                         default settings for Mythbuntu
ii  mythbuntu-gdm-theme                        0.2-0ubuntu1                          mythbuntu gdm greeter theme
ii  mythbuntu-lirc-generator                   0.17-0ubuntu1~gutsy1                  Mythbuntu Lirc Configuration Generator
rc  mythtv-backend                             0.20.2-0ubuntu10.1                    A personal video recorder application (serve
ii  mythtv-common                              0.21.0-0ubuntu2~gutsy1                A personal video recorder application (commo
rc  mythtv-database                            0.21.0-0ubuntu2~gutsy1                A personal video recorder application (datab
ii  mythtv-doc                                 0.21.0-0ubuntu2~gutsy1                A personal video recorder application (docum
rc  mythtv-frontend                            0.21.0-0ubuntu2~gutsy1                A personal video recorder application (clien
ii  mythtv-themes                              0.21.0-0ubuntu1~gutsy1                Additional themes metapackage for MythTV
ii  mythtvfs                                   0.5.0-1                               userspace filesystem client for MythTV
rc  mythweb                                    0.21.0-0ubuntu2~gutsy1                Web interface add-on module for MythTV
ii  mythzoneminder                             0.21.0-0ubuntu2~gutsy1                view status and display footage recorded wit
rc  ubuntu-mythtv-frontend                     0.21.0-0ubuntu2~gutsy1                Metapackage to setup and configure a "Fronte

```

My sources.list is the following:

```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```

---

### Post by superm1 on 2008-05-07
> **rllacey said:**
> Here is my dpkg -l | grep myth
```

ii  gtk2-engines-mythbuntu                     0.3-0ubuntu1                          Mythbuntu GTK+ 2.x Theme
ii  libmyth-0.20                               0.20.2-0ubuntu10.1                    Common library code for MythTV and add-on mo
ii  libmyth-0.21-0                             0.21.0+trunk16733-0ubuntu0~mythbuntu1 Common library code for MythTV and add-on mo
ii  libmyth-perl                               0.21.0-0ubuntu2~gutsy1                A PERL library to access some MythTV feature
ii  libmyth-python                             0.21.0-0ubuntu2~gutsy1                A python library to access some MythTV featu
ii  mytharchive-data                           0.21.0-0ubuntu2~gutsy1                create and burn DVD's from MythTV - data fil
ii  mythbuntu-artwork-usplash                  0.6-0ubuntu1                          mythbuntu artwork for usplash
rc  mythbuntu-control-centre                   0.11-0ubuntu1~ppa1                    Mythbuntu Configuration Application
ii  mythbuntu-default-settings                 0.63-0ubuntu1                         default settings for Mythbuntu
ii  mythbuntu-gdm-theme                        0.2-0ubuntu1                          mythbuntu gdm greeter theme
ii  mythbuntu-lirc-generator                   0.17-0ubuntu1~gutsy1                  Mythbuntu Lirc Configuration Generator
rc  mythtv-backend                             0.20.2-0ubuntu10.1                    A personal video recorder application (serve
ii  mythtv-common                              0.21.0-0ubuntu2~gutsy1                A personal video recorder application (commo
rc  mythtv-database                            0.21.0-0ubuntu2~gutsy1                A personal video recorder application (datab
ii  mythtv-doc                                 0.21.0-0ubuntu2~gutsy1                A personal video recorder application (docum
rc  mythtv-frontend                            0.21.0-0ubuntu2~gutsy1                A personal video recorder application (clien
ii  mythtv-themes                              0.21.0-0ubuntu1~gutsy1                Additional themes metapackage for MythTV
ii  mythtvfs                                   0.5.0-1                               userspace filesystem client for MythTV
rc  mythweb                                    0.21.0-0ubuntu2~gutsy1                Web interface add-on module for MythTV
ii  mythzoneminder                             0.21.0-0ubuntu2~gutsy1                view status and display footage recorded wit
rc  ubuntu-mythtv-frontend                     0.21.0-0ubuntu2~gutsy1                Metapackage to setup and configure a "Fronte

```My sources.list is the following:

```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```
OK, according to that list you have the old libmyth-0-21.  Try to reinstall that package.

---

### Post by rllacey on 2008-05-07
OK. I removed libmyth-0.20 and libmyth-0.21 and reinstalled libmyth-0.21. After that, I tried installing mythtv-backend and received the following output:

```

blacey@mythtv:~$ sudo apt-get install mythtv-backend
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
  mythtv-backend: Depends: mythtv-common (= 0.21.0+trunk16733-0ubuntu0~mythbuntu1) but 0.21.0-0ubuntu2~gutsy1 is to be installed
                  Depends: mythtv-transcode-utils (= 0.21.0+trunk16733-0ubuntu0~mythbuntu1) but it is not going to be installed


```

I reinstalled mythtv-common. When I go to install mythtv-transcode-utils, I get:

```

blacey@mythtv:~$ sudo apt-get install mythtv-transcode-utils
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
  mythtv-transcode-utils: Depends: mythtv-common (= 0.21.0+trunk16733-0ubuntu0~mythbuntu1) but 0.21.0-0ubuntu2~gutsy1 is to be installed
E: Broken packages


```

Very strange. Any ideas?

---

### Post by volkswagner on 2008-05-07
Have you searched in synaptic for broken packages?

---

### Post by rllacey on 2008-05-07
I did a 'Edit, Fix Broken Packages', but nothing happened. I then tried to do 'Edit, Apply Marked Changes', but it is greyed out. Am I doing something wrong?

---

### Post by rllacey on 2008-05-08
Anyone?

---

