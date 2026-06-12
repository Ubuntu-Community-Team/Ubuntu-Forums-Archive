---
title: "Serious Networking Errors"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Desert Sailor on 2009-11-10
So now after a couple of weeks it has become painfully obvious that 9.10 has some serious networking problems.  Which I am sorry to say only the more skilled among us are able to fix.  

So first a comment, then some questions....

COMMENT:  If you're reading this forum, be very comfortable with Ubuntu and Linux before you install or upgrade to 9.10 or you very likely will lose  your Internet connection. 

QUESTION 1:  I am fairly sure the more advanced community is aware of the problem, and is working on a fix.  From you more experienced users, how long does a fix like this usually take.  Is it something that will be released in a few weeks, or are we talking months, or is it so bad it won't be fixed until next release 10.4???

QUESTION 2:  When you download a release .iso file. Does it contain the latest patches and fixes, or will you basically be getting the same 9.10 version which was the Release Candidate (RC).  If I wait and download a new version of 9.10 in a few months will it still be broken until updated and patched, or will it be a fixed and working .iso file off the server??? 

Every OS has it's problems, But this release is too much like Vista for my comfort.  I was hoping for better from Ubuntu.

---

### Post by xombie on 2009-11-10
On my desktop using ralink rt2500 wireless 9.10 has been working OK. On my dad's laptop using atheros ath9k wireless connection is unreliable(finally installed 9.04). According to a bug report on launchpad the problem is with the ath9k driver upstream. The radio constantly disconnects and reports the error to NetworkManager and it finally gives up and disables wireless. The wait right now is on the ath9k developers to find the regression and then wait for a new 9.10 kernel release incorporating the change. NetworkManager giving up and disabling wireless seems to be a bug and I am not sure if it has been reported.

---

### Post by wirelessmonkey on 2009-11-10
Ok, I'm 6 systems in, and the only problem I've had is on a multi-homed, multi-vlan, network setup. So, I'm afraid your problems here in the SLC ( ;)  ) aren't universal.

---

### Post by DGortze380 on 2009-11-11
> **Desert Sailor said:**
> So now after a couple of weeks it has become painfully obvious that 9.10 has some serious networking problems.  Which I am sorry to say only the more skilled among us are able to fix.  

So first a comment, then some questions....

COMMENT:  If you're reading this forum, be very comfortable with Ubuntu and Linux before you install or upgrade to 9.10 or you very likely will lose  your Internet connection. 

QUESTION 1:  I am fairly sure the more advanced community is aware of the problem, and is working on a fix.  From you more experienced users, how long does a fix like this usually take.  Is it something that will be released in a few weeks, or are we talking months, or is it so bad it won't be fixed until next release 10.4???

QUESTION 2:  When you download a release .iso file. Does it contain the latest patches and fixes, or will you basically be getting the same 9.10 version which was the Release Candidate (RC).  If I wait and download a new version of 9.10 in a few months will it still be broken until updated and patched, or will it be a fixed and working .iso file off the server??? 

Every OS has it's problems, But this release is too much like Vista for my comfort.  I was hoping for better from Ubuntu.

You're really going to have to be more specific if you'd like help with this...

---

