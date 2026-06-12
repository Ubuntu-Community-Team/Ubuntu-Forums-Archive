---
title: "Total noob needs help."
date: 2010-05-09
forum: Multimedia Software
---

### Post by RavenStandsAlone on 2010-05-09
I may not even be in the right discussion. I need help with installing flashplayer in Ubuntu 9.1. I know that I used a command in terminal on my Mint 8 install like, <apt remove flashplugin-nonfree && apt install adobe-flashplugin> and it did the rest. It's not doing it in Ubuntu. A little advice here? I don't even know how to download the install package from adobe and etc.

I still need step-by-step instructions to do this.

Thanks,

Raven

---

### Post by buntudawg on 2010-05-09
Hi. Normally installing the restricted extras package will install flash:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by RavenStandsAlone on 2010-05-09
> **buntudawg said:**
> Hi. Normally installing the restricted extras package will install flash:

```
sudo apt-get install ubuntu-restricted-extras
```

That was the ticket. Thanks.

---

### Post by RavenStandsAlone on 2010-05-10
> **buntudawg said:**
> Hi. Normally installing the restricted extras package will install flash:

```
sudo apt-get install ubuntu-restricted-extras
```

totally not solved. When I ran that in terminal I got this message, "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

Gulp.... now what do I do next?

---

### Post by Ozymandias_117 on 2010-05-10
Just run ```
sudo dpkg --configure -a
``` like it says :P then try to install again

---

### Post by RavenStandsAlone on 2010-05-10
> **Ozymandias_117 said:**
> Just run ```
sudo dpkg --configure -a
``` like it says :P then try to install again

"raven@ravenslap:~$ sudo dpkg --configure -a
Setting up java-common (0.30ubuntu5) ...

Processing triggers for man-db ...
Setting up lib32v4l-0 (0.6.0-1) ...

Setting up lib32asound2 (1.0.20-3ubuntu6.1) ...

Setting up lib32gcc1 (1:4.4.1-4ubuntu9) ...

Setting up lib32z1 (1:1.2.3.3.dfsg-13ubuntu3) ...

Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up lib32bz2-1.0 (1.0.5-3) ...

Setting up lib32ncurses5 (5.7+20090803-2ubuntu2) ...

Setting up lib32stdc++6 (4.4.1-4ubuntu9) ...

Setting up ia32-libs (2.7ubuntu17) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
raven@ravenslap:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
raven@ravenslap:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
raven@ravenslap:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
raven@ravenslap:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
raven@ravenslap:~$"

---

### Post by buntudawg on 2010-05-10
Have you enabled the restricted repositories? Go to 

System>Administration>Software Sources

and select them (not sure if you need to enable multiverse as well)

Then in terminal
```
sudo apt-get update
```

Then
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Swagman on 2010-05-10
and if you have Synaptic open then close it before running those commands. (Not sure if software centre affects it)

---

