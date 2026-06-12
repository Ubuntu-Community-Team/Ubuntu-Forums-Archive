---
title: "could someone please tell me what the #$%$ is happening"
date: 2009-11-16
forum: Mythbuntu
---

### Post by rodercot on 2009-11-16
OK! so I do a normal system upgrade, my frontend will not start fue to a schema mismatch, I upgrade to .22  on the backend now the backend works and the one frontend machine works. 

 I come home and fire up the 2nd front end and NADA, it will not start, the log says that this version of myth is older and will not work with your current database. If I try and apt-get update  && Upgrade on this front end it says no updates are available. What a nightmare all because I wanted to update ALSA and a few dependencies.
 
 why is the 2nd frontend machine not getting the same upgrade that caused all this mess in the first place on the first machine. My sources are all the same on both machines. How do I force an upgrade of the 2nd frontend machine and if I knew what files I was looking for I could probably setup from synaptic.

 On top of that, I cannot get rid of the terra theme on either the backend or front end machine, I set it to project gotham wide and it just stays on Terra no matter what I try.

 FFFUUUUDDDGGGEE...

 Regards,

 Dave

---

### Post by tgm4883 on 2009-11-16
1) Make your title more descriptive and you might get more help

2) List what releases of Mythbuntu you are using on each machine

3) List what version of MythTV you are using on each machine

4) Post your repos that you are using on each machine.

---

### Post by rodercot on 2009-11-16
Sorry if my post seemed a little heated.

 All System were Mythbuntu 8.10, 2 frontends and a Master Backend that were all working perfectly. The bedroom machine had not been upgraded in a while and I was having some dropouts with audio so I wanted to update ALSA and get some other files I needed for XBMC. I did a update and upgrade on that machine. After the update completed It would not start the frontend and said that my schema was 30 versions old. 

  So onto the 8.10 master, I downloaded and installed the mythbuntu repos and updated the Master's db to .22 all went fine and the front end on the master is ok

 Once I had updated the master I rebooted the first front end and it worked updated the schema and proceeded on, The only problem I am having now as I said it I cannot get it to switch to Project Gotham Wide, it stay stuck on Terra UI. I have just noticed looking at the logs that it is complaining about not being able to find the project gotham wide mainmenu.xml or .ui file so it is loading terra in it's place.

 Tonight when I got home from work I figure for the other frontend I would just have to boot up and update the schema on that machine as well but no go, it says this version of myth is too old for the database I am running so I tried a update and upgrade and no new files found.

 Mythbackend info

 mythfrontend version: branches/release-0-22-fixes [22840] [www.mythtv.org](www.mythtv.org)

 Current MythTV Schema Version (DBSchemaVer): 1244

 backend repos

 ```
# deb cdrom:[Mythbuntu 8.10 _Intrepid Ibex_ - ISO i386 (20081030)]/ intrepid main
deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

deb http://packages.medibuntu.org/ intrepid free non-free
deb http://ppa.launchpad.net/encbladexp/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/encbladexp/ppa/ubuntu intrepid main

```

 Frontend that is working

 mythfrontend version: branches/release-0-22-fixes [22840]

 Repos

 ```
# deb cdrom:[Mythbuntu 8.10 _Intrepid Ibex_ - ISO i386 (20081030)]/ intrepid main
deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu intrepid-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu intrepid-backports restricted main multiverse universe
deb http://packages.medibuntu.org/ intrepid free non-free
deb http://ppa.launchpad.net/thefirstm/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/thefirstm/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/team-xbmc/intrepid-ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc/intrepid-ppa/ubuntu intrepid main
```

 Frontend that is not working - This version is from the log from yesterdays startup.

 2009-11-15 17:28:42.817 mythfrontend version: 0.21.20080304-1
 [www.mythtv.org](www.mythtv.org)

 repos

 ```
# deb cdrom:[Mythbuntu 8.10 _Intrepid Ibex_ - ISO i386 (20081030)]/ intrepid main
deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb http://packages.medibuntu.org/ intrepid free non-free
```

 
 Thanks in advance,

 Dave

---

### Post by tgm4883 on 2009-11-17
I assume you are using the auto-builds on all of your machines. Do you have a /etc/apt/sources.list.d/mythbuntu-repos.list file? If so, what does that file contain on each of your systems.

---

### Post by blackoper on 2009-11-17
I'd copy the source list directly from the frontend that is working then run a sudo aptitude update/upgrade and see what happens.

Also did you install the weekly mythtv ppa into that frontend that is working, if so it won't be in your main sources.list but will reside in a separate .list file under the /etc/apt/sources.list.d/ section

Try adding the ppa to the source list from here: [http://www.mythbuntu.org/auto-builds]("http://www.mythbuntu.org/auto-builds")

-- TGM beat me to it :)

---

### Post by rodercot on 2009-11-17
> **tgm4883 said:**
> I assume you are using the auto-builds on all of your machines. Do you have a /etc/apt/sources.list.d/mythbuntu-repos.list file? If so, what does that file contain on each of your systems.

 I have that file on the backend here is the repo info.

 Backend sources.list.d

 ```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu intrepid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu intrepid main
```

 front-end working 

 ```
:/etc/apt/sources.list.d$ ls
avenard.list
xbmc@mythbed:/etc/apt/sources.list.d$ sudo vim avenard.list
[sudo] password for xbmc:
deb http://www.avenard.org/files/ubuntu-repos intrepid release

```

 front-end not working

 There are no repos in the sources.list.d directory on this machine. 

 Thanks,
 
 Dave

---

### Post by tgm4883 on 2009-11-17
> **rodercot said:**
> I have that file on the backend here is the repo info.

 Backend sources.list.d

 ```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu intrepid main
deb http://us.autobuilds.mythbuntu.org/mythbuntu/trunk-0.22/ubuntu intrepid main
```

 front-end working 

 ```
:/etc/apt/sources.list.d$ ls
avenard.list
xbmc@mythbed:/etc/apt/sources.list.d$ sudo vim avenard.list
[sudo] password for xbmc:
deb http://www.avenard.org/files/ubuntu-repos intrepid release

```

 front-end not working

 There are no repos in the sources.list.d directory on this machine. 

 Thanks,
 
 Dave

Well there is your problem. Couple things.

1) Add the mythbuntu-repos package to your non-working frontend. [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

2) Upgrade that frontend to 0.22 (0.21 and 0.22 are not compatible)

---

### Post by rodercot on 2009-11-17
Thanks tgm4833 et all. 

 OK I think I got the repos setup on all three machines. I guess I can get rid of the avenard repo on the one machine now.
 
 Is there any way to get Project-Gotham wide working with .22?

 Thanks,

 Dave

---

### Post by tgm4883 on 2009-11-17
Doesn't look like that theme has been updated for 0.22 (I could be wrong). I would bug the theme author about that

---

### Post by rodercot on 2009-11-17
> **tgm4883 said:**
> Doesn't look like that theme has been updated for 0.22 (I could be wrong). I would bug the theme author about that


 I am not really in love with that theme in particular other than all my modifications are inside it. Added menu items, suspend button etc.. and I have been searching for some tips on how to customize the new theme at least just adding a button to the main screen and then an action (exec) function, but it looks as though that has all changed from how it used to be setup.

 Thanks,
  
 Dave

---

### Post by blackoper on 2009-11-17
it's still the same just where the mainmenu.xml file is in a different place.

/usr/share/mythtv/themes/defaultmenu/ should be where you find it now

---

