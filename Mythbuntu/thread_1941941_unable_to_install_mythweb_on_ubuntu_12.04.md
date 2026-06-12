---
title: "unable to install mythweb on ubuntu 12.04"
date: 2012-03-16
forum: Mythbuntu
---

### Post by odror on 2012-03-16
I get the following error

> # apt-get install mythweb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythweb : Depends: mythtv-common (>= 2:0.25.0~master.20120316.53761e2-0ubuntu1) but 2:0.25.0~master.20120305.6519666-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.


Any ideas when this is going to be fixed.

---

### Post by nickrout on 2012-03-16
Are you using mythbuntu-repos? You may need to activate them. Then aptitude update  and try again.

---

### Post by odror on 2012-03-16
> **nickrout said:**
> Are you using mythbuntu-repos? You may need to activate them. Then aptitude update  and try again.
No I am using the default packages that comes with ubuntu.

First I installed the metapackage mythtv. I was not able to install mythpluggins because of the mythweb issue.

---

### Post by nickrout on 2012-03-16
> **odror said:**
> No I am using the default packages that comes with ubuntu.

First I installed the metapackage mythtv. I was not able to install mythpluggins because of the mythweb issue.

looks like you are on amd64 as opposed to i386. As I say install mythbuntu repos and activate it for 0.25 and then update/upgrade

---

### Post by odror on 2012-03-16
> **nickrout said:**
> looks like you are on amd64 as opposed to i386. As I say install mythbuntu repos and activate it for 0.25 and then update/upgrade

12.04 comes by default with 0.25. It is probably a bug I will have to wait for the updates or force install mythweb.

---

### Post by nickrout on 2012-03-16
> **odror said:**
> 12.04 comes by default with 0.25. It is probably a bug I will have to wait for the updates or force install mythweb.

Why ask if you don't like the answer!

---

### Post by uncle hammy on 2012-03-22
You're kinda using an unreleased version of MyhtTV on an unreleased version of Mythbuntu and you're surprised you're having an issue?

Anyways, "12.04 comes with 0.25 by default" != "use the Mythbuntu repos" as suggested.

The version of 0.25 that Mythbuntu 12.04 ships with is lord only knows how far behind the current version.  Right now, there's a new build of 0.25 available almost daily as we approach actual release.  You'd be current if you'd use the repos as suggested, and your mythweb would likely work.

---

### Post by tgm4883 on 2012-03-22
The system seems to be in a weird state or has old packaging information. The version currently in the Ubuntu repositories is 2:0.25.0~master.20120316.53761e2-0ubuntu1 for both mythweb and mythtv-common (and all the other mythtv packages). That said, I recommend the Mythbuntu repos ( [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) ) as well.

---

### Post by nickrout on 2012-03-22
> **tgm4883 said:**
> The system seems to be in a weird state or has old packaging information. The version currently in the Ubuntu repositories is 2:0.25.0~master.20120316.53761e2-0ubuntu1 for both mythweb and mythtv-common (and all the other mythtv packages). That said, I recommend the Mythbuntu repos ( [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) ) as well.

When i first searched on ubuntu pacakaging web page after post #1 here the 64 bit version of mythbuntu-common was an earlier version than the i386. Therefore the OP was unable to install mythweb because there was not a recent enough version of 64 bit mythbuntu-common.

---

### Post by tgm4883 on 2012-03-22
> **nickrout said:**
> When i first searched on ubuntu pacakaging web page after post #1 here the 64 bit version of mythbuntu-common was an earlier version than the i386. Therefore the OP was unable to install mythweb because there was not a recent enough version of 64 bit mythbuntu-common.

That's odd that mythtv-common had a different version (I'm assuming you mean mythtv-common as mythbuntu-common is arch independent)

---

### Post by nickrout on 2012-03-23
> **tgm4883 said:**
> That's odd that mythtv-common had a different version (I'm assuming you mean mythtv-common as mythbuntu-common is arch independent)

You are correct I meant mythtv-commmon, sorry for the error.

It may just have been a timing glitch? The versions seem to be the same now. Problem should be solved.

---

