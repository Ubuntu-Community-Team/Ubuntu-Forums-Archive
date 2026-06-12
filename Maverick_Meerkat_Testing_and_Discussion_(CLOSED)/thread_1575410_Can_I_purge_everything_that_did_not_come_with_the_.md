---
title: "Can I purge everything that did not come with the default install?"
date: 2010-09-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-09-15
I know I have a lot of packages that are not needed, but I forget what they are. They're not applications either so it's not so obvious.

Is there a method to purge anything that would not have come with the default install?

---

### Post by Regenweald on 2010-09-15
You could do a minimal install then install gnome-core. then add necessary stuff from the software centre.

---

### Post by QwUo173Hy on 2010-09-15
What I mean is, I've installed extra stuff over the last few weeks - as well as all the stuff from before the upgrade. I'd like to get rid of them and just have a standard Maverick install.

---

### Post by whoop on 2010-09-15
computer-janitor removes unused libraries...

---

### Post by wilee-nilee on 2010-09-15
> **jarlath said:**
> What I mean is, I've installed extra stuff over the last few weeks - as well as all the stuff from before the upgrade. I'd like to get rid of them and just have a standard Maverick install.

Look in synaptic history for your installs. There is no magic way to achieve this back to install state other then reinstalling, I believe, or just knowing what should be there.

---

### Post by Cenotaph on 2010-09-15
You can begin by purging every package maintained by the community, in the universe and multiverse repositories. Then if you don't mind reinstalling a lot of things, you could run tasksel and deselect everything which should leave you with a ubuntu-standard installation and then reinstall ubuntu-desktop after using autoremove. Should clean up most of the stuff.

---

### Post by seeker5528 on 2010-09-15
> **jarlath said:**
> Is there a method to purge anything that would not have come with the default install?

If you do:

```
sudo dselect update
sudo dpkg clear-selections
```

That will update dselect on what is current since it keeps track of some things in it's own way and set all the non-essential packages to be removed. Since this is tied through dselect mechanisms, then you should run dselect, arrow down to 'Select' and hit 'Enter'. 

Once you are on the selections menu hit the '/' key to get the search prompt, then type 'ubuntu-minimal' (without the quotes) and hit enter. This will probably bring you to another window where it shows you what additional packages will be installed, giving you a change to change some of them, if you hit 'Enter' it should take you back to the selection list if you have not made any modifications to the list.

The '+' key sets the package to 'Install'. Then hit '/' again, search for 'ubuntu-desktop', if you need to you can hit the '\' key to skip to the next item that matches the search string. 

Once ubuntu-minimal and ubuntu-desktop have been set to install, hit enter to get back to the main menu, arrow down to install and hit enter.

What you end up with probably won't be identical to what you would have on a clean install, but I think it will probably be as close as you can get.

Later, Seeker

---

### Post by QwUo173Hy on 2010-09-15
Hey, thanks guys. The command 'sudo dselect' gives me a 'command not found' error. If I install dselect, will it still be wise to whats current, or will it have missed the show, so to speak?

---

### Post by seeker5528 on 2010-09-15
> **jarlath said:**
> Hey, thanks guys. The command 'sudo dselect' gives me a 'command not found' error. If I install dselect, will it still be wise to whats current, or will it have missed the show, so to speak?

If you use dselect to update the package list then dpkg knows about everything that is new since the last time you updated the package list from within Dselect, even if you have just updated the package list with 'apt-get update', from within Synaptic, or whatever other mechanism you prefer. So usually when I have run dselect, seeing how it's usually few and far between, there is usually a huge amount of stuff it recognizes as new, some of which it wants to install automatically for whatever reason. This was my reasoning for doing the dselect update before resetting the packages.

If the package list is already up to date or you update the package list using 'apt-get update', doing it from within Synaptic or whatever, and don't do the update from within dselect at all, that's probably fine too. They all use the same package list, so it shouldn't really affect the outcome relative to the desired outcome of getting back to a set of installed packages that resembles what you might have installed on a fresh install. It's just some additional information that may kept in a way that is specific to dselect, aptitude, or synaptic.

Later, Seeker

---

### Post by ranch hand on 2010-09-15
Or you could do a clean install.

---

### Post by QwUo173Hy on 2010-09-15
Yeah, the dselect thing is a little over my head. I could do a fresh install (first time trying an upgrade). But I've jettisoned some KDE libs and some old kernels, as well as some very old config files (thanks to Ubuntu Tweak). I guess that will do for now.

Maverick is running very well already, and almost a month to the official release. I wonder if I'll notice any changes between now and then. Well... I hope those putting in the longer hours get a well deserved break when it's been released!

---

### Post by VMC on 2010-09-16
> **ranch hand said:**
> Or you could do a clean install.

I thought the same thing, but decided against mentioning it. Sounds too logical.

---

### Post by Slug71 on 2010-09-16
How about good ol autoremove and autoclean?

---

### Post by QwUo173Hy on 2010-09-16
> **Slug71 said:**
> How about good ol autoremove and autoclean?
I've done that, and I've tracked down everything installed since I upgraded to 10.10. There are just some junk left over now from the 10.04 Edubuntu install, but I've jettisonned the most obvious packages here.

Funny, no-one mentioned Computer Janitor. I've just spotted it in the Administration menu.

---

### Post by cariboo on 2010-09-16
> **jarlath said:**
> I've done that, and I've tracked down everything installed since I upgraded to 10.10. There are just some junk left over now from the 10.04 Edubuntu install, but I've jettisonned the most obvious packages here.

Funny, no-one mentioned Computer Janitor. I've just spotted it in the Administration menu.

No one mentioned computer janitor, because the majority of use don't like it and don't use it. Personally, I think using Ubuntu Tweak to clean up your system is a much safer way to go.

---

### Post by seeker5528 on 2010-09-16
> **jarlath said:**
> Yeah, the dselect thing is a little over my head.

Dselect can be a PITA, but relative to what was described in this thread, it's not a situation where the stuff that makes it a PITA should really be a factor, so I'm sure it sounds harder than it actually is.

> **ranch hand said:**
> Or you could do a clean install.

Where's the fun in that? :p

Later, Seeker

---

### Post by panaut0lordv on 2010-09-16
> **whoop said:**
> computer-janitor removes unused libraries...

> **jarlath said:**
> Funny, no-one mentioned Computer Janitor. I've just spotted it in the Administration menu.

U sure? :)

And personally I'd just try to remove everything except ubuntu-desktop and related :)

---

### Post by QwUo173Hy on 2010-09-16
[QUOTE=panaut0lordv;9853595]U sure? :)
Nicely spotted :)

---

### Post by ranch hand on 2010-09-16
> **seeker5528 said:**
> Dselect can be a PITA, but relative to what was described in this thread, it's not a situation where the stuff that makes it a PITA should really be a factor, so I'm sure it sounds harder than it actually is.



Where's the fun in that? :p

Later, Seeker
If  FUN is what he is looking for I would recommend computer janitor.  It should remove all kinds of interesting things, particularly in a pre-release OS, to give days of FUN fixing it.

It might even boot after using it.  Well, it could happen.

---

### Post by QwUo173Hy on 2010-09-16
I actually did give computer janitor a run. Of all the things it listed, I unticked the multimedia codecs (dvdcss and win32 something-or-other).
I made sure the kernel it was removing wasn't my current one by running 'uname -a' and sure enough, it was a prior kernel.

I'm happy with the system as it is now, short of re-installing. On a PIII with 512 RAM, it's not as much fun as it can be :)

---

### Post by ktp on 2010-09-16
> **jarlath said:**
> Funny, no-one mentioned Computer Janitor. I've just spotted it in the Administration menu.

See [comment#4]("http://ubuntuforums.org/showpost.php?p=9850426&postcount=4")

---

### Post by QwUo173Hy on 2010-09-16
> **ktp said:**
> See [comment#4]("http://ubuntuforums.org/showpost.php?p=9850426&postcount=4")
See [comment #17]("http://ubuntuforums.org/showpost.php?p=9853595&postcount=17") ;)

---

### Post by ktp on 2010-09-16
nicely done =)

---

