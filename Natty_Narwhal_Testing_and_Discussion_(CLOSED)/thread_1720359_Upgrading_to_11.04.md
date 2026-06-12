---
title: "Upgrading to 11.04"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by shoot2kill on 2011-04-03
Hi, when I try and upgrade from 10.10 to 11.04b, I get the following error:

```

sudo do-release-upgrade -d

```

```

Could not determine the upgrade                                                                                                                                                                                                                                                                                                                 An unresolvable problem occurred while calculating the upgrade:         
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
=== Command detached from window (Sun Apr  3 12:35:57 2011) ===
=== Command terminated with exit status 1 (Sun Apr  3 12:35:57 2011) ===


```

I have tried looking in the /var/log/dist-upgrade/ directory, but there are lots of files in there and I don't know where to look.

Any help greatly appreciated, Thanks!

---

### Post by LowSky on 2011-04-03
Do you have any non ubuntu repos installed?

you will need to disable them in software sources.

open synaptic if you do not have a direct link to software sources.
 on the top bar click settings>repositories.

once it opens click on "Other Software"
disable all 3rd part repos. Basically anything that doesn't say Canonical.

---

### Post by clhsharky on 2011-04-03
shoot2kill


Natty has its own sub-forum, very helpful, good Sticky's.
Development & Programming>Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)


Sharky

---

### Post by uRock on 2011-04-03
Moved to NNT&D

---

### Post by shoot2kill on 2011-04-04
OK, Still getting this error, although this time I have noticed the following error on apt-get update

```


W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://uk.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

I'm guessing this is the reason. Is there a way I can re-sign the signature keys or something?

Thanks

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-04
Try the update mangler, the one thing it does good enough is distro upgrades.

---

### Post by shoot2kill on 2011-04-04
I'm guessing you mean update-manager?

If so, this is what I tried first, with no luck, so I then tried the do-release-upgrade.

anyway
```
update-manager -d
```
gives the following error when launched through terminal
```

scalamoosh@Scala-Laptu:~$ update-manager -d
extracting 'natty.tar.gz'
authenticate 'natty.tar.gz' against 'natty.tar.gz.gpg' 
WARNING: Failed to read mirror file

```

---

### Post by Puneach on 2011-04-04
I have exactly the same problem.

---

### Post by shoot2kill on 2011-04-05
Bump?!

---

### Post by beew on 2011-04-05
Yeah, why would you do that? 11.04 is not stable yet and 10.10 is not even 6 months old!

---

### Post by shoot2kill on 2011-04-05
> **beew said:**
> Yeah, why would you do that? 11.04 is not stable yet and 10.10 is not even 6 months old!

I have developed a few scripts that run in 10.10, and need to adapt them to work when people change to 11.04. In order to adapt and test these scripts, I need to be running 11.04, and I would much prefer to upgrade from 10.10 than do a fresh install...

---

### Post by Tich666 on 2011-04-06
Same problem here...
This was a fresh install of Maverick (64bit) which I quite heavily customized and upgraded using ppas.

Now this is the output of my upgrade process:
```
update-manager -d
extracting 'natty.tar.gz'
authenticate 'natty.tar.gz' against 'natty.tar.gz.gpg' 
WARNING: Failed to read mirror file

```
and after "computing the changes" it pops up this error message:
```
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
```

I tried with several different mirrors, always the same result.
How am I supposed to fix this? purge all ppas? I have no idea what causes this error.

---

### Post by Puneach on 2011-04-06
I've solved the problem. In my case I had to downgrade all the installed packages from xorg-edgers repository to the standard ubuntu repository versions. Hope it helps.

---

### Post by dashman on 2011-04-07
> **Puneach said:**
> I've solved the problem. In my case I had to downgrade all the installed packages from xorg-edgers repository to the standard ubuntu repository versions. Hope it helps.
how do you do that ?

---

### Post by Puneach on 2011-04-07
Ubuntu-tweak can roll your packages back to the last official versions. It is done by purging xorg-edgers PPA from "package cleaner" side menu item.

---

### Post by dashman on 2011-04-07
I tried your solution but it didn't work

/var/log/dist-upgrade logs attached (the .doc file is actually a log file. you can open it with a regular text editor)

---

### Post by beew on 2011-04-07
> **dashman said:**
> I tried your solution but it didn't work

/var/log/dist-upgrade logs attached (the .doc file is actually a log file. you can open it with a regular text editor)

Try ppa-purge, the purge ppa function in Ubuntu tweak doesn't always work (actually on xorg-edger's launchpad page they instruct you to purge the ppa with ppa-purge before upgrading)

---

### Post by dashman on 2011-04-07
> **beew said:**
> Try ppa-purge, the purge ppa function in Ubuntu tweak doesn't always work (actually on xorg-edger's launchpad page they instruct you to purge the ppa with ppa-purge before upgrading)
what command should I type exactly ?

---

### Post by Puneach on 2011-04-07
Your log file looks like mine before I updated, so I believe the problem is still the same. What version of ubuntu-tweak did you use? Mine was 0.5.10 downloaded from the official site ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)). Did you notice if your packets really were rolled back to the ubuntu repository versions?

---

### Post by dashman on 2011-04-07
I have version 0.5.10 as well
how do I notice what you speaking of ?

I am not an expert guys

---

### Post by beew on 2011-04-07
> **dashman said:**
> what command should I type exactly ?

> To revert to official packages, you can install the ppa-purge package  and run "sudo ppa-purge xorg-edgers". If you have driconf it is  recommended to remove ~/.drirc when changing versions!

It is on the ppa's launchpad page.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

---

### Post by Puneach on 2011-04-07
Just add back the xorg-edgers repository back with sudo add-apt-repository ppa:xorg-edgers/ppa and refresh the repositories index, then look if your update manager wants you to update some packages from this PPA. In case it wants you to update them, you probably have the official packages, in case it does not, you probably still have packages from xorg-edgers PPA installed. Also, you can run your synaptic and sort your packages by the repository they come from.

---

### Post by dashman on 2011-04-07
Puneach I chose the synaptic method -- screenshot attached

beew, I try that and I get back to you

---

### Post by Puneach on 2011-04-07
Sorry for confusing you, but I meant that synaptic is to be used just to check that your packages are rolled back to the official versions. You should re-add xorg-edgers ppa once more (sudo add-apt-repository ppa:xorg-edgers/ppa) and read beew's message - he seems to be right. If it does not help - try purging every other unofficial repository.

---

### Post by cariboo on 2011-04-07
The ugrade process is supposed to disable all the ppa's, but to be on the safe side, you should run ppa-purge on each ppa before attempting to do an upgrade

---

### Post by Tich666 on 2011-04-08
Thanks for the help and hints! Trying ppa-purge of xorg-edgers now. 

I should not have to purge ppas which deal with programms not offered by main repos I think.. don't want to hunt down all of them after the upgrade again, would much rather just update them via ubuntu-tweak.

edit: well, that didn't work as planned.
I then tried to purge the other ppas with ubuntu-tweak, BIG MISTAKE, and now have to re-add and manually purge all of them again, grrr..

Guess I'll just wait with upgrading until the ppa issue is fixed and the update-manager actually disables them properly or whatever.
I mean what good are ppas when every time you want to upgrade your distro you have to disable them all manually?! Really defeats the purpose of them.

---

### Post by dashman on 2011-04-08
Puneach and beew thanks a lot. It worked and I installed Natty beta. wow . Unity looks amazing !
I think Ubuntu is going to win a lot of users with this release

---

