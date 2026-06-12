---
title: "ATi X800GT s-video output under Ubuntu 9.10"
date: 2010-04-27
forum: Multimedia Software
---

### Post by GROwen on 2010-04-27
Hi all,

I've only just started playing with Ubuntu as a total Linux learner and have hit a bit of a wall with getting the s-video output from an Radeon X800GT card to work.

I've tried running the proprietry driver installation but receive this message;

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

and am totally clueless as to what my next step should be.

Any help anyone can give is greatly appreciated.

Thanks in advance,

Guy

---

### Post by Mark Phelps on 2010-04-28
There is no ATI Linux driver that will work with your card and Ubuntu 9.10.  Sorry, but ATI dropped Linux support for your card (and lots of others) over a year ago.

You will have to remove the restricted driver, replace it with the open source driver, and live with that.  There are no other video drivers that will work with your card and current Ubuntu versions.

---

