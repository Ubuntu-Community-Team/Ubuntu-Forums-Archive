---
title: "Issue: samba-common (= 3.0.28a-1ubuntu4.4) but 3.0.28a-1ubuntu4.7 is to be installed"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by timZZ on 2009-05-24
Hi Everyone,

What steps would I take to start looking into the following?

This is on ubuntu 8.04

I have tried what I know but I have gotten stuck at this point.

#####@######:~$ sudo apt-get install samba
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4.4) but 3.0.28a-1ubuntu4.7 is to be installed
E: Broken packages

---

### Post by timZZ on 2009-05-25
I had a feeling this is common.

Anyone else run into this problem?

---

### Post by timZZ on 2009-05-25
Is it a tough one? Need more information?

I can provider I am just new to ubuntu so when I can't see the issue within Synaptic package manager I am not entirely sure how to handle these issues.

---

### Post by ncoll on 2009-05-26
Not sure but maybe it's looking for the samba version at [http://packages.ubuntu.com/hardy-updates/samba](http://packages.ubuntu.com/hardy-updates/samba).

---

### Post by dmizer on 2009-05-26
Try aptitude instead of apt-get, it will give you more information and possible solutions:
```
sudo aptitude install samba
```

---

