---
title: "Sudo apt-get says it &quot;couldn't find package&quot;"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by Darkness Falls on 2009-06-06
Hello everyone!

I'm completely new to Ubuntu; I got a new laptop recently and decided to make the switch from Windows while it was a 'clean slate'. I'm running a dual-boot setup: a completely fresh installation of Ubuntu 9.04 Jaunty Jackalope, distributed free with a magazine I was researching Ubuntu in (specifically *Linux Format #120*, in case it's significant), coupled with the Windows Vista installation that came with the laptop.

Now, currently I don't seem to have any sound, and the wireless adaptor doesn't appear on the Network Administrator list - my ultimate goal is to figure out how to solve these issues, so I can switch to using Ubuntu as my main operating system. After reading around online (and browsing these forums awhile), the most likely cause seems to be not having the right drivers for them, so I connected the laptop directly and tried

```
sudo apt-get install linux-backports-modules-jaunty
```in the terminal. Unfortunately, I got the following response:

```
Reading package lists... Done
Building dependency tree
REading state information... Done
E: Couldn't find package linux-backports-modules-jaunty
```The automatic updater that came with the distro seems to want to download updates, as well; however, it returns the following error when I tell it to install the updates:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding-3.0.9
+nobinonly-0ubuntu0.9.04.1_i386.deb
404 Not Found
```This error is repeated once for each item with various different addresses, presumably for the different files it's trying to download.

I know that the connection is working, because I can surf the net and view different websites. I've been a little reluctant to do so extensively, though, until I can get some protection up (probably in the form of using Firestarter to set up the firewall). But if the connection is working, I don't understand why *sudo apt-get* is failing, or why the updates return 404s. Can anyone help me understand a little more about what's going on, and how to resolve it?

Thanks in advance!

D.F.

---

### Post by Therion on 2009-06-06
Open Synaptic: System/Administration "Synaptic Package Manager"
In the search box type in (cut and paste):```
linux-backports-modules-jaunty
```and see if you can install it from there.

If you can't find the package in Synaptic, you may need to enable the Backports Repository.

To do that, go to System/Administration/Software Sources "Updates" tab.  
Click "ON" all four checkboxes under "Ubuntu Updates".
Click "Close" and then you'll be prompted "Reload", click "OK".
Go back to Synaptic and re-search for the package or try using *apt-get install* again.

---

### Post by Darkness Falls on 2009-06-06
Thanks! That's fixed the second problem nicely - the Update Manager ran again automatically, and spent some time downloading a whole bunch of packages. It seems to have also fixed the problem with *sudo apt-get* returning *couldn't find package *errors - I was able to download and install Firestarter using it and it's running quite happily now.

The *linux-backports-modules-jaunty* download, though, threw up another error message:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
linux-backports-modules-jaunty: Depends: linux-backports-modules-jaunty-generic (=2.6.28.13.17) but it is not going to be installed
E: Broken packages
```I took this to mean I had to install the *-generic* download first, but that returned the same error, ending in:

```
linux-backports-modules-jaunty-generic: Depends : linux-backports-modules-2.6.28-13-generic but it is not installable
E: Broken packages
```If it's not installable, I don't understand where to go from here. What do these error messages mean, and how can I resolve/work around the problem?

D.F.

---

### Post by Knatchwa on 2009-06-06
I am also seeing this error, I believe there was a fix before, I tried to force and no results from that, is there a reason why this kernal is not working, or for that matter installing? As it is saying that a dependancie is uninstallable. Any suggestions would be appreciated.

---

### Post by kvarley on 2009-06-06
Seems you may need to add some repo's.

---

### Post by Darkness Falls on 2009-06-06
This is going to sound like a really silly question, but what are 'repos'? I'm afraid I've only been using Ubuntu for about a day, and most of what I know has been picked up from googling various questions with the word 'Ubuntu' tacked onto the end! :p

What are repos, and how do I determine which one(s) I need to add? Do I add them via *sudo apt-get* in the same way as other applets?

D.F.

---

### Post by Therion on 2009-06-06
Broken packages are packages that have unsatisfied dependencies. If broken packages are detected, Synaptic will not allow ANY further changes to the system until all the broken packages have been fixed; so we need to fix that straight away. 

Open Synaptic (System/Administration "Synpatic Package Manager")
Click on "Edit" from the top menu.
Click on "Fix Broken Packages" 
Click on "Apply Marked Changes"
Confirm and click "Apply"
*Voila!* Broken packages are fixed.

Further:  [Everything You Wanted to Know About Repositories But Didn't Know Enough to Ask...](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Darkness Falls on 2009-06-07
Okay, this is confusing me. I ran the *Fix Broken Packages* command in Synaptic Package Manager, but it didn't give an option for 'Apply Marked Changes' or 'Apply'. It seemed to run automatically, then a message appeared at the bottom of the window saying "Successfully fixed dependency problems". If I load it again now, it says "26842 packages listed, 1753 installed, 0 broken. 0 to install/upgrade, 0 to remove", so I'm presuming it either found nothing to fix, or it did, but fixed it automatically.

Unfortunately, I'm still getting the same error message when I run *sudo apt-get install linux-backports-modules-jaunty* - it depends on -generic (=2.6.28.13.17), but it is not going to be installed.

I then thought to do a search on *linux-generic* in Synaptic Package Manager; it says the latest versions of it and all things starting in *linux* and ending in *generic* (*linux-headers-generic*, *linux-restricted-modules-generic*, etc.) are indeed 2.6.28.13.17, but that the currently installed version is 2.6.28.11.15. I'm guessing that this is probably relevant, but I don't then understand why it wouldn't update to the newer version. Any thoughts?

D.F.

---

### Post by snowpine on 2009-06-07
linux-generic 2.6.28.13.17 is a new kernel version. The kernel is the single most important package in Linux; you need to upgrade that first before you can install the new modules. Should be as simple as marking the new linux-generic for installation in Synaptic. Better yet, upgrade your whole system at once, using Synaptic, the Upgrade Manager, or the terminal commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Hope that helps!

---

### Post by snowpine on 2009-06-07
ps In the future, an alternate approach is to specifically fix your wireless and audio issues. The terminal command 'lspci' will tell you exactly which audio and wireless "chipset" you have. You can use that information to search for answers. Unless you know your hardware, you are really just guessing at solutions...

---

### Post by Darkness Falls on 2009-06-07
Now we're getting somewhere! I ran *sudo apt-get update* and it runs fine, no problems; *sudo apt-get dist-upgrade*, though, produces the following message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

It's not exactly an error message, but checking in Synaptic confirms that I'm still on 2.6.28.11.15, and marking it for update in the Synaptic window gives the following:

```
linux-generic:
  Depends: linux-image-generic (=2.6.28.13.17) but 2.6.28.11.15 is to be installed
  Depends: linux-restricted-modules-generic (=2.6.28.13.17) but 2.6.28.11.15 is to be installed
```

I then figured that I should try updating those two first, before updating the main *linux-generic* file, but that gave me:

```
linux-headers-generic:
 Depends: linux-headers-2.6.28-13-generic  but it is not installable
```

along with the same for *linux-restricted-modules-generic*, replacing *-headers* above with *-restricted-modules*.

I don't know if this is relevant or interesting, but the dark-green checkbox icons next to the various *linux-*-generic* entries have small gold stars superimposed on them, unlike some other packages - is that used to indicate kernel packages, or that they're read-only and don't want to be overwritten or something, or is that a red-herring?

Thanks muchly for the *lspci* code, though - that's certainly going to come in handy!

D.F.

---

### Post by alexgieg on 2009-06-07
You're doing nothing wrong. The problem is in the Ubuntu repositories, whose files are not properly synchronized right now.

What's happing is roughly this: you can have many different kernel versions installed at once, and choose which one you're going to run at boot time. This is good for advanced users, but not so much for someone who simply wants to turn the computer on, type his username and password, and start working.

What's done for these then is this: a default Ubuntu install always has a set of kernel metapackages (packages that when installed do nothing except to require other packages to be installed) installed with names such as "linux", "linux-headers", "linux-restricted-modules" etc. These in turn always point to the latest and greatest official kernel version (packages with long names such as "linux-something-X.Y.ZZ-NN-generic") to be installed.

Now, what happens when a new version of that metapackage "linux" is uploaded to the server, one that asks for a package "linux-image-2.6.28-13-generic", but **this** package, for some reason, isn't uploaded too?

Simply: your "sudo apt-get update && sudo upgrade" fails miserably. Because you have the "linux" package installed, that needs to be updated, but cannot because "linux-image-2.6.28-13-generic" isn't anywhere to be found.

It's frustrating, and even more so when you don't know what's going on, I know. But there's no solution other than to wait for the missing packages to appear. Once it happens the errors and warning will magically disappear.

Alternatively, you can uninstall those metapackages for a few days, so that your attempts at updating your system stop giving misleading error messages. They aren't needed for your system to work, and uninstalling them won't damage anything. If you want to try it do this in a single line:

```
sudo apt-get remove linux linux-generic linux-image linux-image-generic linux-restricted-modules linux-restricted-modules-generic linux-headers-generic linux-backports-modules-jaunty linux-backports-modules-jaunty-generic
```

Then, in a few days, add them back with the following command. If everything was fixed, it'll work. Otherwise it'll fail with an error similar to the one you received, but nothing worse will happen:

```
sudo apt-get install linux linux-generic linux-image linux-image-generic linux-restricted-modules linux-restricted-modules-generic linux-headers-generic linux-backports-modules-jaunty linux-backports-modules-jaunty-generic
```

And what if you don't ever install them again? Well, you simply won't automatically receive kernel updates. But you'll always be able to install them by hand with a "sudo apt-get install".

I hope this helps!

---

### Post by Alexis Phoenix on 2009-06-07
> **Darkness Falls said:**
> This is going to sound like a really silly question, but what are 'repos'? 

Repositories - various places on the 'net where the packages you need are stored.

---

### Post by alexgieg on 2009-06-07
Ah, by the way, the yellow star over a green square in Synaptic only means that package has an updated version available. If you click the star you'll see a menu with one of the option being to set that package to be updated. But it evidently won't work when other needed files aren't available.

---

### Post by Darkness Falls on 2009-06-08
Ahh, excellent - the easiest sort of probem to fix, the sort that goes away by itself after a while! I think I might try the 'wait a few days and try again' option first; after reading around, it seems like most of the other ways to get the sound card and wireless adapter working involve editing and compiling the kernel... I'd like to get to that level of competence eventually, but I think it's a little over my head at the moment!

Just a quick question - how often are the repositories usually updated? Is it a matter of literally a few days, or once a week, or once a month, or what? Is there any kind of schedule to it, or does it just happen when it happens?

Thanks very much for your help and responses, though - it's greatly appreciated!

D.F.

---

### Post by alexgieg on 2009-06-08
> **Darkness Falls said:**
> Just a quick question - how often are the repositories usually updated? Is it a matter of literally a few days, or once a week, or once a month, or what? Is there any kind of schedule to it, or does it just happen when it happens?

It depends on the repository. I'm not sure whether the following is accurate, but from my experience it seems to go like this:

a) The standard repositories almost never update. Only VERY important updates go into there, such as an official point update (think 9.04 to 9.04.1, if it ever happens). If you have only this enabled your system will be extremely un-updating. Think a person updating their Windows computer only from Service Pack to Service Pack, nothing in between.

b) Then comes the security update repository, which updates whenever something security related must be installed "right now this very instant!!!". It's similar to having Windows Update enabled on a Windows machine installing critical updates: you'll usually get something once a week.

c) Next comes the backports repository, where packages that should in principle only appear in the next Ubuntu version find their way into the current version for some reason or other, usually to fix non-security-related bugs or to add some important missing feature.

d) And then you have the huge set of private repositories, which update whenever their owners want them to, from once a minute to once a century. :-)

And someone please correct me if I got something wrong. ;-)

---

### Post by Darkness Falls on 2009-06-08
Awesome! Thanks very much for your help!

D.F.

---

### Post by agenthex on 2009-06-09
I'm getting the same problem that Darkness was kind enough to quote above.

I've been waiting for a repository sync for a few days now (closer to 3 or 4 days).

Synaptic seems like it has everything it needs, but it just tells me it won't do it.  Is there a launchpad bug report for this?  Would it help to report it?

---

### Post by virgoptrex on 2010-01-08
If you know from various forums that the software you are looking for is in the ubuntu universe or related repositories then....

It may be as simple as go to system> administration> software sources

enter your account password which may be same as super user (you can also set super user or "su" password like 'sudo passwd root' for future if you haven't already)

go to "third party" tab

and check all items! 

close and see if that works for installation of any packages like "sudo apt-get install blah blah blah"!

---

