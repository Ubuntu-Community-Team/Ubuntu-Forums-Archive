---
title: "Upgrading without pulling in stuff I've uninstalled"
date: 2010-10-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2010-10-25
Hello,

I am attempting to optimise my Ubuntu installation. I've removed a good hundred or so packages, which I don't use. Nothing to drastic.

Do to so, I had to remove the ubuntu-desktop package. I have, however, left the ubuntu-standard, ubuntu-minimal packages intact. 

My question is, can I still upgrade my system to the latest release without pulling in all of the stuff I've spent hours removing? Do I *need* to have ubuntu-desktop present in order to have a functional system?

I have ubuntu-standard and ubuntu-minimal intact.. Surely I can get a working system without ubuntu-desktop?

If it is possible, how is it done? Thanks in advance.

[COLOR="Gray"]PS. I ask in the this forum because its loosely related to upgrading to Natty at some point. Plus, if anyone knows how to do this, it's the pre-alpha development-release early adopters :-P[/COLOR]

---

### Post by VMC on 2010-10-25
I'm also interested in this subject. I know about [Pinning]("https://help.ubuntu.com/community/PinningHowto"), but one would think, if you remove any trace of the program, it wouldn't get updated. I guess it depends on the depends and what they bring along regardless of what you have removed.

---

### Post by cyberkilla on 2010-10-25
> **VMC said:**
> I'm also interested in this subject. I know about [Pinning]("https://help.ubuntu.com/community/PinningHowto"), but one would think, if you remove any trace of the program, it wouldn't get updated. I guess it depends on the depends and what they bring along regardless of what you have removed.

I read somewhere that the update-manager will install ubuntu-desktop if it doesn't exist, which obviously pulls in all of the stuff you've removed.

It would be nice to get a definitive answer/solution though :)

---

### Post by seeker5528 on 2010-10-25
If you use update-manager it's going to do more to try to insure the end result ends up with the software installed that would have been installed if you had done a new install instead of an upgrade.

If you edit the sources.list yourself and use Synaptic, apt-get, aptitude, etc... you have more control, but you might not get some of the stuff that might have been installed by update-manager.

For me personally, if I edit the sources.list myself, then use Synaptic, my upgrade process would typically be a 3 step process assuming sources have already be changed and package list already updated.

Step 1

Select individual packages then depending on what it indicates will be newly installed or removed choose to proceed or to cancel and select something else.

Step 2

Once I have some of the low hanging fruit and it starts to become more difficult to find packages that don't pull in a bunch of new stuff or cause a bunch of stuff to be removed then I make sure Synaptic is set to do a 'default upgrade' ('Settings --> preferences --> general --> System Upgrade:'), then  click on 'Mark All Upgrades'. 

Step 3

On the 'settings --> preferences --> general' tab, deselect the option to treat recommends as dependencies and switch the 'Upgrade Type:'to 'Smart upgrade', then try installing different combinations of stuff, to try to figure out what will make the least drastic changes, comparing what it says will happen occasionally with what it says will happen when I click on 'mark all upgrades'.

If you want to do it in the least amount of steps, in Synaptic, you could do two steps.

Step 1

Go to the 'settings --> preferences --> general' tab, make sure the option to treat recommends as dependencies is unchecked and change the 'Upgrade Type:' to 'default upgrade', then click on 'select all packages' and apply the changes.

Step 2

Go to the 'settings --> preferences --> general' tab and change the 'Upgrade Type:'to 'Smart upgrade', click on 'select all packages', then apply the changes.

The command line equivalent to the 2 step process would be:

```
sudo apt-get --no-install-recommends upgrade
sudo apt-get --no-install-recommends dist-upgrade
```

Later, Seeker

---

### Post by ranch hand on 2010-10-25
I have installs with out ubuntu-desktop.  I never use Update Mangler.

The only drawback to not having ubuntu-desktop is if there are new packages added to the ubuntu-desktop meta package that you want installed.  They can be installed individually.

All installed packages will be upgraded in the normal manner.  Ubuntu-desktop does not effect that.  It is unneeded in a stable release.  Just make sure you follow what is being added to the testing release ubuntu-desktop meta package for any new package you may actually want (it does happen).

---

### Post by cyberkilla on 2010-10-26
> **seeker5528 said:**
> If you use update-manager it's going to do more to try to insure the end result ends up with the software installed that would have been installed if you had done a new install instead of an upgrade

...

The command line equivalent to the 2 step process would be:

```
sudo apt-get --no-install-recommends upgrade
sudo apt-get --no-install-recommends dist-upgrade
```

Later, Seeker

Thank you for the detailed explanation. So, it's a case of switching to the new sources, and manually upgrading, whilst being mindful of what APT is attempting to do.

I can just about live with that.

> **ranch hand said:**
> I have installs with out ubuntu-desktop.  I never use Update Mangler.

The only drawback to not having ubuntu-desktop is if there are new packages added to the ubuntu-desktop meta package that you want installed.  They can be installed individually.

All installed packages will be upgraded in the normal manner.  Ubuntu-desktop does not effect that.  It is unneeded in a stable release.  Just make sure you follow what is being added to the testing release ubuntu-desktop meta package for any new package you may actually want (it does happen).

Ranch Hand, just out of interest, do you use a similar method to the one described above by Seeker?

---

### Post by ranch hand on 2010-10-26
No I do not.  I generally like the recommends for some reason, probably ignorance.  My knowledge of what is needed and what is not with any particular package is improving and I find that I am installing less and less all the time.

I think that it is probably a good idea, particularly on smaller drives.

I am intending to do just that one of these days just to see if I can see any difference in function.  I suspect that if any is noticable it would be simple a slight increase in speed (and of course some extra space).

Most recommends, have little or no real connection that I can see with what I am doing.  Gparted is installed on all my OS', for instance, and the recommends include ntfs support.  This is of no use to me at all as ntfs can be deleted without that.  This is also true of support for several other file systems included in the recommends.

---

### Post by seeker5528 on 2010-10-27
> **ranch hand said:**
> I generally like the recommends for some reason, probably ignorance.

Generally speaking I leave the option to treat recommends as depends on.

But when you are talking major upgrade and not wanting to pull in a bunch of stuff you uninstalled, the recommends often work against you.

Even with recommends being treated as dependencies, you can remove a recommended package, without removing the package that pulled it in, and security/bug fix updates won't cause it to be pulled in again.

One of the reasons I like using Synaptic is that it is easy to turn the option to treat recommends as depends on and off so you can see pretty quickly what is recommended by comparing what it will do, which sometimes is easier than looking at the package properties and sometimes not depending on how many packages are involved. There are situations where I will turn the option to treat recommends as dependeds of then turn it on again.

Another reason is that if you know something is only recommended you can go to 'custom filters --> marked changes' and deselect an individual recommended package to not have it installed while still pulling in the rest of the recommended packages.

On a major upgrade things become significantly more complex due to new packages, package merging/splitting, renamed packages. As it relates to recommends as depends, even some non-renamed packages may show up as new again for some reason, in which case if the option is enable the recommends will be pulled in again in spite of the fact that you already had an earlier version of that package installed.

So generally speaking it would be suggested to the the 'recommends as depends' option enabled.

When doing a major upgrade, what you use to do the upgrade, whether recommends as depends is enabled or not at any given step, and whether you install in a couple of steps or do smaller chunks all just depends on how how far you have strayed from what is recommended and relative to that how much work you want to put in during the upgrade and how much after.

Later, Seeker

---

### Post by cyberkilla on 2010-10-31
Well, just to reiterate, thanks to both of you for the help;)

---

