---
title: "Will Mythbuntu Repos upgrade change Ubuntu desktop?"
date: 2009-11-23
forum: Mythbuntu
---

### Post by williammanda on 2009-11-23
Due to a Jamu problem with the current Mythbuntu release 0.22.0+fixes22594-Oubuntu1 (karmic). I would like to get the current stable release of mythbuntu. But I don't have a standard Mythbuntu install. I installed karmic then mythbuntu control center. If I use the Mythbuntu repo method of upgrading will this affect the current installation? Will it just basically effect mythtv? Here is the post for the Jamu issue:

[http://ubuntuforums.org/showthread.php?t=1318635]("http://ubuntuforums.org/showthread.php?t=1318635")

---

### Post by tgm4883 on 2009-11-23
mythbuntu-repos should not affect ubuntu desktop stuff. You can see the packages that would get upgraded here

[https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22](https://edge.launchpad.net/~mythbuntu/+archive/trunk-0.22)

[https://edge.launchpad.net/~mythbuntu/+archive/testing](https://edge.launchpad.net/~mythbuntu/+archive/testing)

---

### Post by williammanda on 2009-11-24
I updated to the repos yesterday but I still have release 0.22.0+fixes22594. During the installation I selected ver .22, US and didn't select PPA. Was this correct? Also I still have the same Jamu issue.

---

### Post by tgm4883 on 2009-11-24
no, you should have 0.22.0+fixes22890-0ubuntu0+mythbuntu3. I'll have to check the repos, but they should be synced up. You can switch to the PPA to be sure.

---

### Post by williammanda on 2009-11-24
Well I found out that I needed to do an apt-get upgrade after installing the repo. Once I did that mythtv was upgraded .22 fixes 28890.

---

