---
title: "upgrading software sources"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by scandido on 2010-09-22
Yesterday I upgraded from 10.04 to 10.10, and today when I look at the Software Sources window I see 

disabled on upgrade to maverick (repo address)

on all the third party repositories on the "Other Software" tab (see attached). I assume this is because it wants me to change the repositories to ones specifically for Maverick. Is there any principled way to do this, or should I just assume the ones that already say Maverick are good, the Chrome one won't matter since it doesn't specify a distribution, and then try to Maverick versions of the other two?

Thanks in advance for you assistance.

---

### Post by seeker5528 on 2010-09-22
You could type the address of each repository in and see what the latest distribution is [http://repo.ahadiel.org/apt/](http://repo.ahadiel.org/apt/) for example has karmic and lucid repositories. 

Spideroak doesn't seem to allow browsing the archive, so looks like you are stuck with whatever they tell you is available.

Later, Seeker

---

### Post by scandido on 2010-09-22
Okay, this is generally the procedure I use, but it seems like in many scenarios this is an area that could be improved. For example, perhaps repositories should contain some kind of automatic upgrade information, or Ubuntu could manually follow the procedure outlined above and see if things make sense before punting and asking the user to do it. 

I know there is an appropriate place to submit such an idea, but I'm not sure where it is (LaunchPad, Papercuts, etc.?). Can someone tell me what that place is and I will make the suggestion?

---

### Post by seeker5528 on 2010-09-22
> **scandido said:**
> Okay, this is generally the procedure I use, but it seems like in many scenarios this is an area that could be improved. For example, perhaps repositories should contain some kind of automatic upgrade information, or Ubuntu could manually follow the procedure outlined above and see if things make sense before punting and asking the user to do it.

Installing stuff from a 3rd party repository or PPA is something you choose to do, and accept that there are additional potential risks of conflict.

Ubuntu devs doing things to make PPAs easier to deal with is one thing.

Ubuntu devs actively including something in the installer that would increase the risk of a distribution upgrades failing is a whole different thing. Doesn't seem likely to me.

Best to disable unofficial repositories and uninstall any conflicting packages during the upgrade then let the user sort it out later. If we found these things once, and they are things we care about, it shouldn't be that big of a deal to add/enable them again.

Later, Seeker

---

### Post by cariboo on 2010-09-22
Disabling third party repositories for an upgrade is done on purpose, it is fairly new, as it only started  in karmic. The purpose is to stop incompatible libraries and files from being installed during the upgrade process.

Incompatible third party repositories were one of the main reasons for upgrade failures. You can always re-enable them after the upgrade is finished.

---

### Post by scandido on 2010-09-22
I do realize third party repos are not officially supported and carry additional risks. I also realize that these should be disabled during the upgrade. However, if this can be resolved automatically after the upgrade without the user having to do it, how would that be a bad thing?

I believe you are assuming that these repositories were added by the user explicitly either via software sources or by editing the configuration file. You and I, who understand how this works, can go about resolving the problem. However, with more and more applications automatically adding their own repositories for updates (see Chrome, Dropbox, and SpiderOak) when the DEB file is installed via download and click, there are a lot of users who don't understand how their apps are being updated, or why they stopped after the upgrade.

I'm not suggesting that I have the solution to this problem. Just perhaps that this is something that should be thought about, especially as Ubuntu appears to be putting into place a new way for software to be handled (the software store, which seems like it will eventually be more than a pretty GUI for apt).

---

### Post by VinDSL on 2010-09-23
> **scandido said:**
> Is there any principled way to do this, or should I just assume the ones that already say Maverick are good, the Chrome one won't matter since it doesn't specify a distribution, and then try to Maverick versions of the other two?One of the things I like about Mint (an Ubuntu fork) is, they have a rating system for updates.  This takes the *guesswork* out of it, and converts a (possibly) misperceived assumption into an informed gamble, e.g. do I pick door #4 or not?  LoL!

IMHO, with Ubuntu, it's best to use the shotgun approach!

If you're looking for simplicity, as well as freedom *from* choice, Ubu Tweak is the way to go:

[IMG]http://vindsl.com/images/ubu-tweak-3rd-party.png[/IMG]

You can do it ALL, with one click, from a single screen...  ;)

---

### Post by seeker5528 on 2010-09-23
> **scandido said:**
> I believe you are assuming that these repositories were added by the user explicitly either via software sources or by editing the configuration file. You and I, who understand how this works, can go about resolving the problem. However, with more and more applications automatically adding their own repositories for updates (see Chrome, Dropbox, and SpiderOak) when the DEB file is installed via download and click, there are a lot of users who don't understand how their apps are being updated, or why they stopped after the upgrade.

If 3rd party applications are going to be adding their own repositories when they get installed, then they should be providing the support to the user to re-add it when necessary. If they can add it during the installation, surely they can do their own checks and offer to add it again, providing a link to some instructions if necessary, if the checks show the application is out of date. Just my opinion. 

Later, Seeker

---

### Post by scandido on 2010-09-23
> **seeker5528 said:**
> If 3rd party applications are going to be adding their own repositories when they get installed, then they should be providing the support to the user to re-add it when necessary. If they can add it during the installation, surely they can do their own checks and offer to add it again, providing a link to some instructions if necessary, if the checks show the application is out of date. Just my opinion. 


Yes, certainly they can, and perhaps some will. Others likely will not.

My thought is that one of the concepts of package management is to standardize and centralize the software update mechanism, rather than having separate (perhaps no) mechanism for each individual piece of software. 

As Ubuntu gains market share, more companies are finding it worthwhile to release their software and will not necessarily choose to distribute it through the Ubuntu repositories. If mechanisms are not put in place to allow package management to work in these scenarios, software installation will become like it is on Windows.

Obviously, there are good reasons why third party repositories are risky and should be considered for advanced users. But, as they are being added transparently for all users when installing common software, there are two possible approaches. 
1) Allow it to be broken, (correctly) blame the third-party software, contribute to the idea that Linux doesn't work for non-power users.
2) Put measures in place to improve the overall computing environment and make Ubuntu just work for everyone. 

Truthfully, I suppose neither of our opinions matter.

---

### Post by cariboo on 2010-09-23
Opinions do matter, you came become a member of the [ubuntu-devel]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") mailing list and make a suggestion, you should probably be prepared to come up with an outline of why this is needed, and be prepared to defend your suggestion. BTW no coding skills needed for a suggestion.

---

### Post by VinDSL on 2010-09-23
> **cariboo907 said:**
> Opinions do matter[...]

[...] be prepared to defend your suggestion.

BTW no coding skills needed for a suggestion.My suggestion is:

[LIST]
[*]Temporarily disable third-party PPA sources
[*]Run Update Mangler (*ranch hand*'s saying)
[*]Enable third-party PPAs
[*]Re-run Update Manager
[/LIST]

Nothing could be more simple (except using Ubu Tweak)!

But, wait... that's already been suggested, acted upon, and implemented.

I suppose they could use a Winders model, e.g. forget the PPAs and update programs individually.

Personally, I like it (upgrading software sources) the way it is...

---

### Post by seeker5528 on 2010-09-23
> **scandido said:**
> My thought is that one of the concepts of package management is to standardize and centralize the software update mechanism, rather than having separate (perhaps no) mechanism for each individual piece of software.

A standardized and cetralized update is one of the concepts. Providing a manged environment is a bigger one. If you start throwing 3rd party repositories in there, it's not managed anymore.

> If mechanisms are not put in place to allow package management to work in these scenarios, software installation will become like it is on Windows.

If there was better support for LSB compliant packaging, I'm sure it wouldn't be that big of a stretch to come up with a way to provide centralized mechanism to co-ordinate their updates. 

If distributions provided better support for LSB compliant packages, more 3rd parties might provide compliant packages. If more 3rd parties provided LSB compliant packages, distributions might do more to support for their installation. Classic catch 22.  

Later, Seeker

---

### Post by ronacc on 2010-09-23
Ubuntu devs are responsible for the content of the official repos , they are not and can not be responsible for the content of PPA's and other 3rd party sources  , disabling 3rd party sources on upgrade is quite reasonable as there is no way of telling that the PPA's etc are even applicable to the new version , as an example medibuntu does not provide a repo until a version is released , updating it for instance lucid>maverick would produce an error during update because maverick does not exist in their repo structure , also many PPA's are for a single or only a few versions . It is better to let the individual user re enable applicable 3rd party sources.

---

### Post by jerrylamos on 2010-09-23
> **ronacc said:**
> Ubuntu devs are responsible for the content of the official repos , they are not and can not be responsible for the content of PPA's and other 3rd party sources  , disabling 3rd party sources on upgrade is quite reasonable as there is no way of telling that the PPA's etc are even applicable to the new version , as an example medibuntu does not provide a repo until a version is released , updating it for instance lucid>maverick would produce an error during update because maverick does not exist in their repo structure , also many PPA's are for a single or only a few versions . It is better to let the individual user re enable applicable 3rd party sources.

CD daily build 20100923 selects 3rd party software and 3rd party software sources by default.  My book, that's dead wrong. In years of testing Alpha & Beta Ubuntu I've never used 3rd party selection on update.

Further, the install done by these has the same wrong defaults.  Screws up update-manager resulting in partial update and even apt-get hang.

I found this on 20100920 and re-verified it today on 20100923 so I submitted bug #646493.

Only way I have of verifying that the default selection includes 3rd party software and sources is to download the iso and write a disk.  Tedious.  Anyone have any ideas?

Thanks, Jerry

---

### Post by seeker5528 on 2010-09-24
> **jerrylamos said:**
> CD daily build 20100923 selects 3rd party software and 3rd party software sources by default.  My book, that's dead wrong. In years of testing Alpha & Beta Ubuntu I've never used 3rd party selection on update.

I'm assuming you mean the partner repository, since others wouldn't be supported.

```
deb http://archive.canonical.com/ubuntu maverick partner
```

Assuming it's functional during the development cycle. 

Courtesy of [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Of course the partner repository is a totally different thing than 3rd party (not hosted at canonical) repositories, which is what has been discussed in this thread up to this point. PPAs are somewhere in between, but probably will not be supported out of the box either in the foreseeable future.

> Further, the install done by these has the same wrong defaults.  Screws up update-manager resulting in partial update and even apt-get hang.

Wrong defaults?

> I found this on 20100920 and re-verified it today on 20100923 so I submitted bug #646493.

After reading the bug report I'm still not sure what you mean by "wrong defaults"

If the partner repository needs a new key, I would certainly call that a bug.

There doesn't seem to be much distributed through this repository, flash, adobe-air, skype, etc.. so I doubt that your fears about them being unmaintained/unwanted is justified. 

Later, Seeker

---

### Post by xebian on 2010-09-24
> **scandido said:**
> ...

...But, as they are being added transparently for all users when installing common software, there are two possible approaches. 
...
Truthfully, I suppose neither of our opinions matter.

You could be right in some cases but I know Google chrome tells you that it will add to your apt/sources file and gives you the choice to opt out.

I do agree on your point, that update manager can disable them during the upgrade.  However, after the upgrade and during the 'clean up' it should restore it back to where it was, or in lieu of should explicitly tells you either by  a pop up indicator (since they have been so enamored with these anyway ) or via the update log.

BTW I don't use update-manager so it doesn't affect me at all.

---

### Post by seeker5528 on 2010-09-25
> **xebian said:**
> I do agree on your point, that update manager can disable them during the upgrade.  However, after the upgrade and during the 'clean up' it should restore it back to where it was, or in lieu of should explicitly tells you either by  a pop up indicator (since they have been so enamored with these anyway ) or via the update log.

The problems you have with 3rd party repositories is....

[list]Is the provided software self contained and installed in '/opt/something/'?[/list]
[list]Is the provided software installed in '/usr/bin/' or '/usr/local/bin/' or '/usr/local/something/' and if so do they use shared libraries from the system?[/list]
[list]If the provided software does use shared libraries from the system, are these libraries still compatible after the distribution upgrade?[/list]

I'm all for more overtly providing information about what was disabled, but there are too many variables for me to think it's a good idea to re-enable 3rd party repositories automatically.

Later, Seeker

---

