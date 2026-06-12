---
title: "Can't pull trunk builds from repos"
date: 2009-04-16
forum: Mythbuntu
---

### Post by JerkyChew on 2009-04-16
I'm not sure what's wrong here - I downloaded the .deb from the mythbuntu weekly builds and installed them via dpkg -i filename.deb, but instead of being prompted for trunk vs weekly (or whatever the alternative is) I ended up back at the shell with a couple 'ok' messages. Attempting apt-get update and then upgrade doesn't find any new versions of Myth, nor does the Synaptic gui. Is there something wrong or am I misconfigured somehow? I attempted to delete the repos via the gui but they wouldn't delete. Attempting to re-install the repos doesn't change anything either. 

Any ideas? I'm itching to use my HD-PVR! :D

---

### Post by managementboy on 2009-04-17
If you want trunk for Jaunty:

```
sudo nano /etc/apt/sources.list
```

then add
```
deb http://weeklybuilds.mythbuntu.org/mythbuntu-trunk/ubuntu jaunty main
deb-src http://weeklybuilds.mythbuntu.org/mythbuntu-trunk/ubuntu jaunty main

```
run
```
sudo apt-get update
```
then
```
sudo apt-get install mythtv
```
done?

---

### Post by tgm4883 on 2009-04-17
> **JerkyChew said:**
> I'm not sure what's wrong here - I downloaded the .deb from the mythbuntu weekly builds and installed them via dpkg -i filename.deb, but instead of being prompted for trunk vs weekly (or whatever the alternative is) I ended up back at the shell with a couple 'ok' messages. Attempting apt-get update and then upgrade doesn't find any new versions of Myth, nor does the Synaptic gui. Is there something wrong or am I misconfigured somehow? I attempted to delete the repos via the gui but they wouldn't delete. Attempting to re-install the repos doesn't change anything either. 

Any ideas? I'm itching to use my HD-PVR! :D

do 

```
dpkg-reconfigure mythbuntu-weekly
```

---

### Post by JerkyChew on 2009-04-17
Thanks for the help, but neither of those made a difference. I tried tgm4883's recommendation first because it seemed easiest... I told it to use trunk and the us repo, but apt-get update and apt-get upgrade found nothing to upgrade. Apt-get install mythtv told me it's already the newest version.

(All commands are run with sudo in front of them)

I then tried managementboy's suggestion of adding the repo's, although I changed jaunty to hardy since I'm running 8.10. Same deal, it won't upgrade anything.

And for the record, mythtvbackend --version gives me 

matt@magic:/etc/apt$ sudo mythbackend --version
Please include all output in bug reports.
MythTV Version   : 18207
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40

Perhaps something is wrong with the repo? I've tried this on an Ubuntu 8.10 laptop that I built this morning, same result.

---

### Post by tgm4883 on 2009-04-18
The way I told you is the recommended way of doing it.  I just checked, for some reason there aren't trunk builds for hardy, I'm not sure if that is by design or by accident.  I'm checking into it though.

---

### Post by tgm4883 on 2009-04-18
> **tgm4883 said:**
> The way I told you is the recommended way of doing it.  I just checked, for some reason there aren't trunk builds for hardy, I'm not sure if that is by design or by accident.  I'm checking into it though.

Alright got it.  There isn't a new enough QT4 in hardy for trunk builds.

---

### Post by JerkyChew on 2009-04-18
I guess I'm not sure what you mean - I have a Mythbuntu 8.10 box here running trunk, it's a frontend waiting for me to rebuild my backend. Are you saying that something has happened with the QT4 portion of the new builds and that's holding up their release? 

It sounds more like you're saying that I need to upgrade to 9.04 in order to build Trunk - I'm ok with this if it will get me where I need to be - But if that's the case how come I could pull down trunk with my 8.10 box a couple weeks ago?

---

### Post by tgm4883 on 2009-04-18
> **JerkyChew said:**
> I guess I'm not sure what you mean - I have a Mythbuntu 8.10 box here running trunk, it's a frontend waiting for me to rebuild my backend. Are you saying that something has happened with the QT4 portion of the new builds and that's holding up their release? 

It sounds more like you're saying that I need to upgrade to 9.04 in order to build Trunk - I'm ok with this if it will get me where I need to be - But if that's the case how come I could pull down trunk with my 8.10 box a couple weeks ago?

Ah I was confused as I was remembering back to what you posted (not reading it though :/ )

> I then tried managementboy's suggestion of adding the repo's, although I changed jaunty to hardy since I'm running 8.10. Same deal, it won't upgrade anything.


8.10 is intrepid, not hardy.  So if you are running hardy (8.04), no trunk builds, if you are running intrepid (8.10), you should have trunk builds available.

---

### Post by JerkyChew on 2009-04-22
I'm an idiot. I thought I had installed Hardy but sure enough, /etc/issue tells me I'm on 8.04. Thanks for all the help - I can use this as a reference for all my other builds.

---

