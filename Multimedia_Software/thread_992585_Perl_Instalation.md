---
title: "Perl Instalation"
date: 2008-11-24
forum: Multimedia Software
---

### Post by DarkLion on 2008-11-24
I am using Ubuntu 8.10 Intrepid 32bit, and am curious if anyone has had this problem. I try to install Perl and get this error,




This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I try to do as recommended yet get this error in terminal,



E: Type 'wget' is not known on line 55 in source list /etc/apt/sources.list

 Does anyone know how to solve this problem? I thank you for any advice and for your time in assisting me.

---

### Post by pgatrick on 2008-11-24
Sounds like maybe something is messed up in your sources.list. Could you post the contents of /etc/apt/sources.list here?

EDIT: Also, I would have thought perl was installed by default.:-k

---

### Post by DarkLion on 2008-11-24
The contents are as follows,

/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.distUpgrade
/etc/apt/sources.list.d/medibuntu.list.save
/etc/apt/sources.list.d/winehq.list
/etc/apt/sources.list.d/winehq.list.save

I cannot find the Perl Audio Editor/Converter program anywhere. I hope this helps with diagnosing the problem. I also have this as well. It is from sources.list.save.


deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://playonlinux.botux.net/](http://playonlinux.botux.net/) hardy main #PlayOnLinux
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main #GNOME Do
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- 
sudo apt-key add - && sudo aptitude update

---

### Post by pgatrick on 2008-11-24
Oops, thought you meant the programming language. :redface:
You don't have just a normal sources.list file?

---

### Post by pgatrick on 2008-11-24
Ah I see, delete those last two lines from sources.list, those command were meant to be entered at the command line:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O-
sudo apt-key add - && sudo aptitude update

```

After that just run 'sudo apt-get update' and it should work. :)

---

### Post by DarkLion on 2008-11-24
I just tried to save the changes yet it gives me this error message,



You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I attempted to change the permissions yet it tells me that I am not the owner. It also says that the owner is root. I do not know how to change this. I am sorry if my system is becoming a bother. I know at times it is to me LOL. Isn't  technology just wonderful!

---

### Post by pgatrick on 2008-11-24
Oops, I should have mentioned you need root privileges to do that stuff. Just type sudo before the command. :)

---

### Post by DarkLion on 2008-11-24
Forgive me for I am still relatively new at Ubuntu. When you say to type sudo before the command, do you mean before running the wget command or is this for changing the permissions? If it is for the permissions then I must appologize for imposing further, for I require instructions on the procedure. I greatly appreciate all of the help you have given me and am grateful for any further assistance you can give.

---

### Post by pgatrick on 2008-11-25
Sudo is a command to make you temporarily root, you type it before another command in the command line if you need root privileges. So to edit your sources.list you'd have to type at the command line something like 
```
sudo vim /etc/apt/sources.list
``` 
or 
```
sudo gedit /etc/apt/sources.list
``` 
(or whichever text editor you use). 

Then when it opens the file it does so as root and you have the proper permissions to make changes to the file. :) 

Also those last two lines in the sources.list file I said need to be removed, you probably should run those commands, so again at the command line just enter:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O-
```
then
```
sudo apt-key add - && sudo aptitude update
```
(you probably need to do this to use the medibuntu repository, which I'm assuming has the program you're looking for?)

---

### Post by DarkLion on 2008-11-28
I greatly appreciate all the help that you were able to give. It is truly people like yourself who are a part of the forum, that make me most certain That I will not go back to Windows. Again, many thanks for the assistance. I believe that things shall be going smoother for my system. May you have a most wonderful evening, and many blessings.

---

