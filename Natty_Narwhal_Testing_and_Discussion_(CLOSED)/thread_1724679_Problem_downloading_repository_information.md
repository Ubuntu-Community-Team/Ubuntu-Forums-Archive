---
title: "Problem downloading repository information"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by xeriouxi on 2011-04-08
Hi,

Not sure why this has suddenly started to happen (I think it started a few days ago) but I can't seem to properly download the repository information correctly. I get some updates listed after the error (though I have a feeling it's not all of them) but I can't figure out why it's having trouble.

The error I get is:

```
W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty/Release  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/Release  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-backports/Release  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-security/Release  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-proposed/Release  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

My sources.list file is:

```
# 

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Alpha amd64 (20110318)]/ natty main restricted

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Alpha amd64 (20110318)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty main restricted independent
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates main restricted independent
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse independent
# deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ natty-security main restricted independent
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ natty-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb http://gb.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe independent
deb-src http://extras.ubuntu.com/ubuntu natty main
```

I haven't altered any repository information or made any changes to the software sources. Does anyone know why this might have happened and how to fix it?

Many thanks! =)

---

### Post by MadCow108 on 2011-04-08
where is the independent section coming from?
I do not have that in my list, neither have I heard from it.

removing them all should solve the error message

---

### Post by cariboo on 2011-04-08
Have you tried a different server? You can change the server in Synaptic->Settings->Repositories

---

### Post by xeriouxi on 2011-04-08
> **MadCow108 said:**
> where is the independent section coming from?
I do not have that in my list, neither have I heard from it.

removing them all should solve the error message

I'm not sure where the independent section came from. It's nothing that I manually added I know in the Software Center a while back there was a catagory for this that had one application (Daily Journal) in it.

I removed the 'independent' entries from the sources.list file and it seems to be working fine now.

> **cariboo907 said:**
> Have you tried a different server? You can change the server in Synaptic->Settings->Repositories

I did try a different server, yes, and it came up with the same message.

Thanks both for your help! =)

---

