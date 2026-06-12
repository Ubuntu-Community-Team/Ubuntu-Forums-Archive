---
title: "Nothing has worked"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by durty_dawg on 2007-02-16
I am a noob to linux but I love it, all ready my UNIX / Linux OS teacher said to get Ubuntu and now everyone I talk to I try to convert. Resistance is futile,lol. Ok so my plroblem is i have tried the suggestions to get wma's and mp3's to play and nothing has worked. I am open to all suggestions, though i have seen almost all post on the subject, Someone please help I got 75gigs of music I can't listen too.

Specs
Ubuntu 6.06 
Dell Inspiron 1150/2.6 Ghz Intel Celeron
512Mb RAM

---

### Post by n00bish on 2007-02-16
Is it a problem with sound in general or can you not play those specific files?  I personally use "xmms" as my music player - it's similar to WinAmp for windows.  You could try that - I've had it work right out of the box.

---

### Post by justin whitaker on 2007-02-16
> **durty_dawg said:**
> I am a noob to linux but I love it, all ready my UNIX / Linux OS teacher said to get Ubuntu and now everyone I talk to I try to convert. Resistance is futile,lol. Ok so my plroblem is i have tried the suggestions to get wma's and mp3's to play and nothing has worked. I am open to all suggestions, though i have seen almost all post on the subject, Someone please help I got 75gigs of music I can't listen too.

Specs
Ubuntu 6.06 
Dell Inspiron 1150/2.6 Ghz Intel Celeron
512Mb RAM

Use automatix or easy ubuntu to get all of the restricted codecs. You should then be able to run the files via rhythmbox. If not, you should try to see if your soundcard is supported by OSS or ALSA, and make sure the configuration is correct.

---

### Post by durty_dawg on 2007-02-16
Its wma and mp3 format. I'm trying to play it off my external hard drive, the w32codecs are not downloading for some reason what ever. This is the only problem i've come across so far. Its just making me a lil nucking futs.

---

### Post by Bloch on 2007-02-16
[http://www.getautomatix.com/](http://www.getautomatix.com/)
Double click on the downloaded file to install it with gdebi 

Use it to install the needed codecs. It can also install extra media players (which can also be installed by synaptic)

---

### Post by durty_dawg on 2007-02-16
Here is what i get when I try to update with easyubuntu.

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
[http://flomertens.keo.in/ubuntu/dists/dapper/Release.gpg:](http://flomertens.keo.in/ubuntu/dists/dapper/Release.gpg:) Temporary failure resolving 'flomertens.keo.'


I get this when I try to install automatix2 through terminal install.

"Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 7671B in 2m0s (64B/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing fglrx-control (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

I hope this info can get me a lil bit more info. I really apperciate all the help eveyone is being.

---

### Post by Bloch on 2007-02-16
Can you post your sources.list file? i.e copy and paste the contents of the sources.list text file (use the command below) and post it here.
 
 gedit /etc/apt/sources.list

---

### Post by durty_dawg on 2007-02-17
here is the source you requested.I hope this will help out even more.


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# If you get errors about missing keys follow these command's :
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
#
# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## plf mirror. use if primary repo is offline
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
## deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
## deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

##
## Use the following repos ONLY if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## official wine apt repository
##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main
##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main


## opera web browser
## deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## skype
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


If you need anything else let me know, ty for the assistance.

---

### Post by durty_dawg on 2007-02-17
The above post is of my source list could some one help me please!?

---

### Post by Daveth on 2007-02-18
you seem to have a range of breezy repositories listed yet seem to be running dapper, so make sure the breezy ones are unticked in the repository list or, better still, remove them. Then trying running easyubuntu again for those codecs.

---

