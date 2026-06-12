---
title: "cdrtools - why do linux distributuin create bad forks"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by Major_Kong on 2007-10-10
Something i suspect is not very well known (found out only recently):

>  On May 15th 2006, most projects from the cdrtools project bundle have been relicensed under CDDL (giving more freedom to users than the GPL does). At the same time, an important amount of additional code (DVD support code from Jörg Schilling and a Reed Solomon decoder from Heiko Eißfeldt) has been added to the freely published sources.

In summer 2006, the attacks from the group of Debian maintainers escalated and in September 2006, these people created something they call a fork from cdrtools. They soon added a lot of bugs and this way turned the "fork" into a questionable experiment. The last work on this "fork" has been done eight months later on May 6th 2007, then the leader of the attacks stopped his efforts.

Although there is no "project" activity on the "fork" anymore, there are still people who spread incorrect claims on both the original project and the fork. Please help the free original project by correcting these incorrect claims. 


But here's the kicker:
> 
Many Linux distributions now come with broken variants of cdrtools
	_If you are on Debian, RedHat, SuSE and some other Linux distributions, you need to take extreme care as these distributions recently started to replace cdrtools by a fork that is based on an outdated version of cdrtools. This fork did not fix bugs but rather introduced new bugs that never have been in the original software._

For other Linux distributions, I suggest to have a look at /usr/bin/cdrecord and check whether this is a link to another program or whether there is an original program file. Also call "cdrecord -version" to check what version you are using. The affected distributions replaced all programs from cdrtools (cdrecord, cdda2wav, readcd, mkisofs, ...) by programs from the fork. 
[http://cdrecord.berlios.de/new/private/linux-dist.html](http://cdrecord.berlios.de/new/private/linux-dist.html)

But luckily, The Ubuntu burning team has packages for the original cdrtools. - [https://launchpad.net/~ubuntu-burning/+archive](https://launchpad.net/~ubuntu-burning/+archive) 


Don't know if this is old info, but...

---

