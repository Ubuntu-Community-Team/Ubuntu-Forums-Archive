---
title: "Need to find previous version of Handbrake"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Keith_Beef on 2009-12-19
I just tried to update Handbrake... failed.

When I downloaded the x86 64 bit deb package, the package installer complained that this conflicted with the installed version. So I removed the installed version using Synaptic (foolish me) and tried again.

Now, I find that the new version requires versions of the following libraries more recent than those on my system.
[LIST]
[*]libsoup2.4-1,
[*]libstdc++6.
[/LIST]

So I want to find the previous version of Handbrake... but it is not in the 9.04 repositories (according to Synaptic) and my Google searches have led me to a page at the Handbrake site listing the old version, but pointing to the download page with a link to the new version...

So, short of upgrading to 9.10 (which I am not going to do this weekend, since donwloading the whole system takes far, far too ong where I am), how can I get back that previous version that I removed using Synaptic.

---

### Post by JohnAStebbins on 2009-12-19
This PPA has the latest handbrake for 9.04
[https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

### Post by Keith_Beef on 2009-12-19
Thanks a lot, John.

Handbrake has been a boon to me, to my wife (on her Mac), and especially to a great many friends who don't consider themselves to be "computer nerds".

Installing this morning failed, and I don't understand why.

I added the sources to synaptic and retrieved the GPG key, following the instructions on the following page.
[https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa)

Handbrake was already showing up in Synaptic, and this is still the case, without a version number.

Is there a was of finding out if Synaptic and apt-get are looking in the wrong source? 

```
$ sudo apt-get install --print-uris handbrake 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package handbrake is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package handbrake has no installation candidate
```


K.

---

### Post by JohnAStebbins on 2009-12-20
The packager for that PPA has split things into 3 packages.
handbrake-cli for the command line version
handbrake-gtk for the gui
handbrake-common for general release documents

I'm guessing you want the gui so you should only have to install handbrake-gtk

---

### Post by Keith_Beef on 2010-01-06
In the end, I upgraded to 9.10... I was planning to do this anyway at some point.

Handbrake installed fine from the repositories once I had completed the upgrade.

K.

---

