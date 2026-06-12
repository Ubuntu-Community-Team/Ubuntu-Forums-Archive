---
title: "unable to install gtkpod"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by sleepyjon on 2007-04-26
When I try to install gtk pod I get this:

```

sleepyjon@sleepyjon-desktop:~$ sudo apt-get install gtkpod
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
  gtkpod: Depends: libgpod0 but it is not installable
E: Broken packages

```

I went to synaptic to try and install libgpod0, but I get this error message:

```

libgpod0:

Package libgpod0 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


```

I have no idea what to try, can anyone help me?

---

### Post by reclusivemonkey on 2007-04-26
Which version of Ubuntu are you running? I found I couldn't get my gf's iPod to work with Edgy, but it works very well with Fiesty. If you want to get the best out of your iPod, I would recommend using Fiesty. Although this should not affect you installing gtkpod. Have you tried installed gtkpod from Synaptic?

---

### Post by sleepyjon on 2007-04-26
Oh, I knew I was forgetting something important, sorry about that.

I am using feisty, I just upgraded from edgy yesterday. I also tried installing gtkpod from synaptic, that didn't work, I get the same message.

---

### Post by reclusivemonkey on 2007-04-26
> **sleepyjon said:**
> Oh, I knew I was forgetting something important, sorry about that.

I am using feisty, I just upgraded from edgy yesterday. I also tried installing gtkpod from synaptic, that didn't work, I get the same message.

That's ok =] You might have got something screwy in your apt sources list.

Try 

```

sudo apt-get update

```

then 

```

sudo apt-get upgrade

```

If that doesn't work, try 

```

sudo apt-get autoremove libgpod0

```

then 

```

sudo apt-get autoclean

```

and try installing again. If it all fails, post your sources.list

I'm by no means a deb package expert (I came from Slackware and installed pretty much everything post install by source) but the above certainly won't do any harm. I installed gtkpod without a hitch, so it *should* work on Feisty in theory. HTH

---

### Post by sleepyjon on 2007-04-26
That didn't work, you wanted the sources.list right?

```

deb http://pt.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pt.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://pt.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://pt.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://pt.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://pt.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

---

### Post by reclusivemonkey on 2007-04-27
> **sleepyjon said:**
> That didn't work, you wanted the sources.list right?

```

deb http://pt.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pt.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://pt.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://pt.archive.ubuntu.com/ubuntu/ edgy universe
 deb-src http://pt.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://pt.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
 deb-src http://pt.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

Dude you've got edgy/dapper repos in your list. I am at work right now, but I can post you my sources.list for Feisty when I get home, but you might be able to find one on the fourms. I think that's your problem. Particularly, your universe repos are edgy.

---

### Post by sleepyjon on 2007-04-27
Oh thank you.

---

### Post by LuisGMarine on 2007-04-27
In case the other guy forgot to post his sources here are mine with all the extra repos from the Ubuntu Guide.  I also have the beryl repo's which I commented out , if you don't need them then just delete them.  Hope this helps

```

## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17

#beryl
#deb http://ubuntu.beryl-project.org/ feisty main
```

Good Luck

-LuisGMarine

You might also need to get the gpg key with the following command.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

then after that just run a:

```
sudo apt-get update
```

to update your repos, and as always here is the full guide on adding the extra repos.  [Click Here!]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by sleepyjon on 2007-04-28
Thank you for all the help everyone, that worked. I knew it was something stupid on my part.

---

### Post by reclusivemonkey on 2007-04-28
Glad you got it sorted. Thanks to the other poster; with a nine month old baby in the house, I don't always remember to follow up! Thankfully we have such a great community =]

---

