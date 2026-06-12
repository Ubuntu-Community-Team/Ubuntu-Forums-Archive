---
title: "Nvidia Driver, setinit3-Envy doesn't work"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by stanley_asbeek on 2008-01-31
Hi there.

i'm fresh to linux and i've installed the last version of ubuntu 7.10

i want to install my graphic drivers but i have several problems

first of all, when i'm doing : 
"sudo sh NVIDIA-Linux-x86-169.09-pkg1.run"

the install say that i'm running X Server.

so i tryed to go in "sudo telinit 1" to install but there the install say's taht's not safe to install in setinit 1 and that i have to install in setinit 3
when i try to byepass the warning, the install doesn't want to install at all, say's that i don't have envirement or something like that.

when i "sudo setinit 3" i'm comming in graphique mode of ubuntu, so when i try to lunch install, he say's that i still run a X Server.

so i looked around in the forums, and i saw a program named "envy" i downloaded it and tried to install, but he says this : 
[img]http://img218.imageshack.us/img218/9633/capturexc8.jpg[/img]
[img]http://img218.imageshack.us/img218/7379/capture1yn8.jpg[/img]

i did put the cdrom in the driver and i can browse it but envy still doesn't see it.

i allso tryed that one from : oedha
[http://ubuntuforums.org/showpost.php?p=4240567&postcount=3](http://ubuntuforums.org/showpost.php?p=4240567&postcount=3)
but the install said something elese that not work :s

i realy don't know what to do, i have tried all i can, but doesn't like to work.

does any one have any idea ?

i'm on a GeForce 7600 GS.

i'm so sorry for my poor english, i'm frensh :o)

thx anyway

Stan

---

### Post by overdrank on 2008-01-31
HI and welcome, I don't understand the language in the screen shots but I believe when trying the ```
"sudo sh NVIDIA-Linux-x86-169.09-pkg1.run"
```  You will need to use the keys alt, ctrl, F1 and this will bring you to command line then you can use the command

```
sudo /etc/init.d/gdm stop
``` then install the drivers and this command to start 
```
sudo /etc/init.d/gdm start  
```

---

### Post by stanley_asbeek on 2008-02-01
hi overdrank,
thx for you ply.

i have tried what you have said, but when i lunch the install after doing ```
sudo /etc/init.d/gdm stop
```

i have to accept the licence, there no problem, after the install says : 
> No precompiled kernel interface was found to match your kernel; would you like to attempt to download a kernel interface for your kernel from NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)
Yes/No

in both cases, if i'm doing yes or no, there are several problems, the install allways faild.

any hint ? maby my install of ubuntu was wrong? or maby the driver must be older and i sould take one that match with ubuntu's version... 
i don't realy know.

---

### Post by overdrank on 2008-02-01
> **stanley_asbeek said:**
> hi overdrank,
thx for you ply.

i have tried what you have said, but when i lunch the install after doing ```
sudo /etc/init.d/gdm stop
```

i have to accept the licence, there no problem, after the install says : 


in both cases, if i'm doing yes or no, there are several problems, the install allways faild.

any hint ? maby my install of ubuntu was wrong? or maby the driver must be older and i sould take one that match with ubuntu's version... 
i don't realy know.

HI and I am taking a guess here. Please post the output of this command. ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by stanley_asbeek on 2008-02-01
> **overdrank said:**
> HI and I am taking a guess here. Please post the output of this command. ```
gksudo gedit /etc/apt/sources.list
```

i've done the command and that the result : 

> (gksudo:6312: Gtk-WARNING **: cannot open display:

i have done that when i'm in ctrl+alt+f1 screen, i don't know if you want me to do that anyware else ?
terminal when i'm in graphic mode maby ?

edit : wow, i've done that command in graphic mode, that the result : 
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

don't know if it help :p

thx anyway for your time and intrest :o)

---

### Post by overdrank on 2008-02-01
> **stanley_asbeek said:**
> i've done the command and that the result : 



i have done that when i'm in ctrl+alt+f1 screen, i don't know if you want me to do that anyware else ?
terminal when i'm in graphic mode maby ?

edit : wow, i've done that command in graphic mode, that the result : 


don't know if it help :p

thx anyway for your time and intrest :o)

```

[COLOR="Red"]#[/COLOR]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://be.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://be.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://be.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]deb http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
[/COLOR]
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
[COLOR="Red"]deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner[/COLOR]

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

Ok I have made some changes in your repo list and highlighted them red. I commented out the cd for gutsy as one of the errors on your first post. Also I uncommented the other repos and maybe you can use envy now after you run the command ```
sudo apt-get update
```

---

### Post by tseliot on 2008-02-01
> **stanley_asbeek said:**
> so i looked around in the forums, and i saw a program named "envy" i downloaded it and tried to install, but he says this : 
...

i did put the cdrom in the driver and i can browse it but envy still doesn't see it.

i allso tryed that one from : oedha
[http://ubuntuforums.org/showpost.php?p=4240567&postcount=3](http://ubuntuforums.org/showpost.php?p=4240567&postcount=3)
but the install said something elese that not work :s

i realy don't know what to do, i have tried all i can, but doesn't like to work.

does any one have any idea ?

You will have to enable multiverse and universe repositories, as described in point E of the [FAQ]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")

---

