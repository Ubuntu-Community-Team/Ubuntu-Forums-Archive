---
title: "Mythbuntu-repos errors on Linux Mint"
date: 2010-12-03
forum: Mythbuntu
---

### Post by williammanda on 2010-12-03
During the install of the mythbuntu-repo it incurred an error (see attached photo). I went into synaptic and removed and re-installed again but got the same error. Please advise.
Thanks

---

### Post by tgm4883 on 2010-12-03
> **williammanda said:**
> During the install of the mythbuntu-repo it incurred an error (see attached photo). I went into synaptic and removed and re-installed again but got the same error. Please advise.
Thanks

Are you using linux mint?

---

### Post by williammanda on 2010-12-03
yes

---

### Post by tgm4883 on 2010-12-03
> **williammanda said:**
> yes

Hmm, this is the second time I have seen a similar error on a linux mint machine. I'll need to install a mint vm and test this

---

### Post by williammanda on 2010-12-03
> **tgm4883 said:**
> Hmm, this is the second time I have seen a similar error on a linux mint machine. I'll need to install a mint vm and test this

Where will you post your results?

---

### Post by tgm4883 on 2010-12-03
> **williammanda said:**
> Where will you post your results?

Check this bug report and verify it's the same as yours (looks the same)  [https://bugs.edge.launchpad.net/mythbuntu/+bug/678104](https://bugs.edge.launchpad.net/mythbuntu/+bug/678104)

I'll post my findings there

---

### Post by tgm4883 on 2010-12-04
At this time, I cannot fix this issue. If someone can answer the question I posted in the bug report, I will look at fixing this again.

---

### Post by williammanda on 2010-12-04
> **tgm4883 said:**
> Check this bug report and verify it's the same as yours (looks the same)  [https://bugs.edge.launchpad.net/mythbuntu/+bug/678104](https://bugs.edge.launchpad.net/mythbuntu/+bug/678104)

I'll post my findings there

I agree with everything in the bug report except for the 64 bit, I'm using 32 bit.

> Bug Description

When trying to install mythbuntu-repos with gdebi on mint10-julia-64bit: 8.8-0ubuntu0+mythbuntu~auto20101116001839 this fails with E: Sub-process /usr/bin/dpkg returned an error code (1)

In Gdebi, I see that the problem lies in Debconf (or what is handed to it): "use of unitialized value" in some Perl module (see screenshot)

In addition, in mythbuntu-control-centre, occasionally the "Repositories" tab was there twice. When it was there, it was still not possible to select a repo and an upgrade path. Now it's gone aga

---

### Post by tgm4883 on 2010-12-04
> **williammanda said:**
> I agree with everything in the bug report except for the 64 bit, I'm using 32 bit.

I changed the thread title in hopes someone with LinuxMint would know the answer. Until then, I cannot fix the issue.

---

### Post by williammanda on 2010-12-04
I also posted the issue on the linux mint forum.

---

### Post by williammanda on 2010-12-05
I got around the issue by following what was posted in the bug report. I changed the "julia" codename to "maverick" in this file:

william@C2D ~ $ cat /etc/lsb-release
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=10
DISTRIB_CODENAME=julia
DISTRIB_DESCRIPTION="Linux Mint 10 Julia"
william@C2D ~ $ 

william@C2D ~ $ cat /etc/lsb-release
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Linux Mint 10 Julia"
william@C2D ~ $ 

Then I installed mythbuntu-repo. This isn't a fix but just a temporary way to get the install completed.

---

