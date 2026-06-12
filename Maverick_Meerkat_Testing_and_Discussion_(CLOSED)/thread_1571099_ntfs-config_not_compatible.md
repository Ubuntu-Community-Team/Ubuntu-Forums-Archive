---
title: "ntfs-config not compatible"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-09-09
Trying to run ntfs-config and the program crashes. The notification says the problem can not be reported and some dependencies need updating.

Michael

---

### Post by seeker5528 on 2010-09-09
It works for me, so I would say getting yourself up to date would be the first step.

Later, Seeker

---

### Post by cor2y on 2010-09-09
[FONT=Sans][FONT=Sans]Well i just updated to the beta  used the zsync file on the iso to get it uptodate before installing and i can confirm ntfs-config, not ntfs-3g is not compatible with 10.10 beta.
[/FONT][/FONT]it complains about 'No such file or directory: '/etc/hal/fdi/policy'" even after a repo update check and install of updates.

---

### Post by seeker5528 on 2010-09-09
> **cor2y said:**
> [FONT=Sans][FONT=Sans]Well i just updated to the beta  used the zsync file on the iso to get it uptodate before installing and i can confirm ntfs-config, not ntfs-3g is not compatible with 10.10 beta.
[/FONT][/FONT]it complains about 'No such file or directory: '/etc/hal/fdi/policy'" even after a repo update check and install of updates.

I'm not running a fresh install, so that may be the difference.

Eliminating the use of HAL is a work in progress, so maybe this directory doesn't get created by default anymore.

If you create the directory does it work then?

Later, Seeker

---

### Post by cor2y on 2010-09-10
a whole batch of updates today got ntfs-config launching but it took three times for it to work since it kept crashing before i could configure the ntfs partition.

---

### Post by kansasnoob on 2010-09-10
I know this is probably a dumb question, but why does one need "ntfs-config" if you have "ntfsprogs"?

---

### Post by coffeecat on 2010-09-10
> **kansasnoob said:**
> I know this is probably a dumb question, but why does one need "ntfs-config" if you have "ntfsprogs"?

ntfsprogs, as you probably know, is a set of tools for working with the  ntfs filesystem. ntfs-config, on the other hand, is a GUI tool for  adding entries to fstab to automount ntfs partitions. Use with care. It  has been known to  [setup the same  mountpoint for two partitions and make a system unbootable. ]("http://ubuntuforums.org/showthread.php?t=1567878") :|

---

### Post by cariboo on 2010-09-10
Ntfs-config is a gui app allowing the user to set read/write permissions on an ntfs partition, ntfsprogs is a set of tools that allow you to maintain your ntfs partition it includes the following tools

[list]
[*] ntfsfix
[*] mkntfs
[*] ntfsinfo
[*] ntfslabel
[*] ntfsresize
[*] ntfsundelete
[*] ntfscluster
[*] ntfscat
[*] ntfsls
[*] ntfscp
[*] ntfsclone
[*] ntfsmount
[*] ntfsdrcrypt
[*] ntfscmp
[/list]

---

### Post by ranch hand on 2010-09-10
Well, you learn something everyday.  Two packages that I have no need for at all.

There is a compatibility problem.  I am not compatible with ntfs.

---

### Post by kansasnoob on 2010-09-10
I was serious. Even on a multi-boot computer with Windows I've never found ntfs-config to be necessary or helpful :)

Quite often detrimental :(

So I guess a better question would be, "what do you need ntfs-config for"?

I'm honestly not being a smart a$$. I've never found a need for it.

I'd compare it to "palimpsest". It can create more problems than it can possibly solve :)

But that is just an opinion.

---

### Post by coffeecat on 2010-09-10
> **kansasnoob said:**
> So I guess a better question would be, "what do you need ntfs-config for"?

I'm honestly not being a smart a$$. I've never found a need for it.

That's a fair question. **You** don't need ntfs-config. I don't need it either. We both know how to edit /etc/fstab. But there are people who are not confident doing this. A GUI app to add fstab entries (and for other filesystems too) would be a useful tool for some people. I believe Opensuse has this functionality somewhere in Yast, so why not Ubuntu? Having said that, I wouldn't recommend ntfs-config. I was distinctly underwhelmed when I tried it and that link I posted is a true cautionary tale.

---

### Post by kansasnoob on 2010-09-10
> **coffeecat said:**
> That's a fair question. **You** don't need ntfs-config. I don't need it either. We both know how to edit /etc/fstab. But there are people who are not confident doing this. A GUI app to add fstab entries (and for other filesystems too) would be a useful tool for some people. I believe Opensuse has this functionality somewhere in Yast, so why not Ubuntu? Having said that, I wouldn't recommend ntfs-config. I was distinctly underwhelmed when I tried it and that link I posted is a true cautionary tale.

Ditto :D

The one time I fiddled with "ntfs-config" it left me confused :confused:

And my original question was meant to be taken seriously. I think if we knew why the OP needed "ntfs-config" we could probably offer a better alternative.

---

### Post by Morbius1 on 2010-09-10
ntfs-config is a rather odd little utility. The first thing it asks you upon first run is if you want to enable write support for  ntfs partitions.  Write support for NTFS partitions have been enabled by  default ( ntfs-3g ) since I think Hardy so I'm not sure why it doesn't know that and  I'm not sure what it does when you answer Yes.

---

### Post by coffeecat on 2010-09-10
> **Morbius1 said:**
> Write support for NTFS partitions have been enabled by  default ( ntfs-3g ) since I think Hardy so I'm not sure why it doesn't know that and  I'm not sure what it does when you answer Yes.

I think I may have the answer. If you look at the download page of the ntfs-config website...

[http://flomertens.free.fr/ntfs-config/download.html](http://flomertens.free.fr/ntfs-config/download.html)

... it says the current version is 1.0.1 and offers downloads for Edgy and Feisty. :-s (If you click on the download links you are offered the same package.) I'm posting from Maverick atm, and Synaptic tells me that the version of ntfs-config in the Maverick repo is....  1.0.1.

Which suggests that it hasn't been maintained since 2007 at the latest. Which, in my book, means that it is a dead project. Or, if not dead, certainly moribund.

Another reason not to use it?

---

### Post by cariboo on 2010-09-10
Unfortunately, there are quite a few dead projects in the repos, ntfs-config is # 2789 on the popularity-contest list with 144,221 installs. This doesn't mean a lot of people use it, but a lot of people do it install it.

---

### Post by ranch hand on 2010-09-10
OK, I'll bite, where on earth do you get those figures for the popularity contest?  I check the box on my installs but thought that was just for the devs to know what was going on.  Sounds like an interesting thing to look at.

---

### Post by Morbius1 on 2010-09-10
ntfs-config does have one thing going for it, it's not mountmanager or Pysdm. Those two are by far much more dangerous. Clever programmers codifying "man mount". Unfortunately it lets the unsuspecting victim ... er ... user do just about anything they want.

---

### Post by coffeecat on 2010-09-10
> **Morbius1 said:**
> ntfs-config does have one thing going for it, it's not mountmanager or Pysdm. Those two are by far much more dangerous. 

Thanks for the tip. And if you look at [the pysdm home page]("http://pysdm.sourceforge.net/") it seems to have been dead for even longer than ntfs-config.

---

### Post by cariboo on 2010-09-10
> **ranch hand said:**
> OK, I'll bite, where on earth do you get those figures for the popularity contest?  I check the box on my installs but thought that was just for the devs to know what was going on.  Sounds like an interesting thing to look at.

How about right [here]("http://popcon.ubuntu.com/by_inst"). I found it while doing research on getting rid of firestarter from the repositories.

---

### Post by ktp on 2010-09-10
popcon is great

---

### Post by ranch hand on 2010-09-10
> **cariboo907 said:**
> How about right [here]("http://popcon.ubuntu.com/by_inst"). I found it while doing research on getting rid of firestarter from the repositories.
Wow, that is cooler than I even dreamed.  Thanks a bunch.

---

### Post by ktp on 2010-09-10
you do know that under Software Sources, there is an option for user to choice if they want to submit statistics to "popcon".  This is used to find "popular applications".

---

### Post by ranch hand on 2010-09-10
Yup, just did not know I could get to the results.  I always check that box.

---

### Post by praveenmarkandu on 2010-09-17
someone is probably gonna tell me im an idiot, because no one likes hal.

but if you install hal, you can get ntfs-config to work.

---

### Post by cariboo on 2010-09-17
If that's what it takes to make it work, I don't have any problems with it.

---

### Post by coffeecat on 2010-09-18
> **praveenmarkandu said:**
> but if you install hal, you can get ntfs-config to work.

> **cariboo907 said:**
> If that's what it takes to make it work, I don't have any problems with it.

I do. :wink: It's still an abomination. I tried it on my laptop (in Lucid) and it offered to mount:

sda1 = Acer recovery partition.
sda2 = Windows 7 boot partition.
sda3 = Windows 7 C: partition.

... but failed to show my sda5 NTFS data partition in the initial screen. It did when I explored around a bit in the interface, but this is designed for inexperienced people who are unhappy with editing fstab. They wouldn't know to untick sda1 and sda2 at least. (Personally I wouldn't have my Windows C: in fstab either - I'd mount it only on an as-need basis.)

OK, "abomination" is a bit harsh. This is pre-alpha software which doesn't seem to have been developed since it was first coded. Which is a pity. Nice idea, but incomplete.

---

### Post by Sophont on 2010-09-18
> **cariboo907 said:**
> If that's what it takes to make it work, I don't have any problems with it.

You don't see a problem with installing modules that the devs have been removing for a couple of releases to get a program to run that has not seen updates for years?

Are you sure that's the best way to go forward?

---

### Post by cariboo on 2010-09-18
> **Sophont said:**
> You don't see a problem with installing modules that the devs have been removing for a couple of releases to get a program to run that has not seen updates for years?

Are you sure that's the best way to go forward?

There are still quite a few packages in the repositories that have hal as a dependency, It's going to take time to weed them out. From what I've seen so far having hal installed hasn't created any problems for me.

Ntfs-config is fairly high up on the [popularity list]("http://popcon.ubuntu.com/by_inst"), #2790, so it's going to be pretty hard to get rid of it.

---

