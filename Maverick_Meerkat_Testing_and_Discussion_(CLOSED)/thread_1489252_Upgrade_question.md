---
title: "Upgrade question"
date: 2010-05-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-05-20
I've never upgraded to a testing version before by ONLY changing sources on a previous version install.  Today I decided to do this...

So I edited my sources.list and changed every instance of lucid to maverick, updated apt, then ran the update manager.

I closed the partial upgrade request and updated the 370 other packages.  I reboot and quick check shows that I'm now on 10.10.

Here's the question.  Is there something else I need to edit or update other than the sources.list?

I usually don't jump in to testing versions until a beta is released but I wanted to get in on the fun a little earlier this time.

Thanks

---

### Post by ranch hand on 2010-05-20
Do not use Update Mangler, read the sticky.

You should check with synaptic to see why things were held back but the command "apt-get dist-upgrade" (for upgrading the distro) will install most of the stuff and right now I even think it is safe to do it.  That is a command that you need to really know what is up before invoking, just like a partial upgrade.

As far as editing you should be fine.  I haven't used UM since Hardy and I wonder what  kernel you are using.  The above command will get you the current one.

---

### Post by ronacc on 2010-05-20
you can check what kernel you are running by typing uname -r in a terminal , I think the current one is 2.6.34-2 , the -3 kernel was not all there yet when I updated earlier , I like Ranch Hand recommend synaptic for updating during a dev cycle . apt-get upgrade is safe , apt-get dist-upgrade can get you in trouble if you don't watch what it is proposing to do before telling it to proceed

---

### Post by autocrosser on 2010-05-20
I just got the -3 kernel about a hour ago for 64 bit---so it's the most current.....I always look at Synaptic (like both Ronacc & Ranch Hand)---I have not really trusted Update-Manager from the very first---and some of it's behaviour was changes during Jaunty cycle (not for the better)......

So, that makes 3 yes votes...:)

By the way---good to see you this early on---wait for "interesting times" ---do remember to check the forum first before doing ANY upgrade you are not 100% sure of.

---

### Post by LKjell on 2010-05-21
update-manager is very good to view change logs.

---

### Post by dino99 on 2010-05-21
hello guys,

what have you done about libc6-i686 removal ?

---

### Post by BwackNinja on 2010-05-21
eglibc (2.11.1-0ubuntu9) maverick; urgency=low

  * Merge with Debian (r4267, trunk).
  * Update to the eglibc 2.11 branch (r10490).
    - patches/ia64/submitted-memchr.diff, patches/any/cvs-readdir_r.diff,
      patches/any/submitted-confname.h.diff: Remove, applied upstream.
  * Stop building libc6-i686 on architecture i386.
  * Disable patches/any/arm-syscalls-out-of-line.diff to fix build
    failure on armel.


output from aptitude changelog libc6

let it be removed.

---

### Post by ranch hand on 2010-05-21
> **LKjell said:**
> update-manager is very good to view change logs.
You can also see that change log in synaptic or aptitude.

In synaptic you simply highlight the package in question, click on the "Package" menu and select "Download Changelog".

What Update Mangler is really good for is going to System>Administration>Software Sources and unchecking "Check for Updates" under the Updates tab, then going to System>Preferences>Startup Applications and unchecking "Update Notifier".

As far as I can see this is the only thing it is good for.  It does help to get you a little more familiar with your System menu.

---

### Post by screaminj3sus on 2010-05-21
> **ranch hand said:**
> You can also see that change log in synaptic or aptitude.

In synaptic you simply highlight the package in question, click on the "Package" menu and select "Download Changelog".

What Update Mangler is really good for is going to System>Administration>Software Sources and unchecking "Check for Updates" under the Updates tab, then going to System>Preferences>Startup Applications and unchecking "Update Notifier".

As far as I can see this is the only thing it is good for.  It does help to get you a little more familiar with your System menu.
I've never really had an issue with the update manager even during alphas/betas of ubuntu.

---

### Post by LKjell on 2010-05-21
> **ranch hand said:**
> You can also see that change log in synaptic or aptitude.

In synaptic you simply highlight the package in question, click on the "Package" menu and select "Download Changelog".
..

I know, but the point with update-manager is that you can view the change log without clicking twice.

---

### Post by crjackson on 2010-05-21
I ran sudo apt-get upgrade and it did nothing (because I had already upgraded those packages with the update manager).

It was reporting Maverick 10.10 but running on the Lucid Kernel.  So I jumped in with both feet and BLINDLY ran sudo apt-get dist-upgrade.

It pulled in about 65 more packages and remove 40 (KDE) packages. It updated me to the newest Kernel.

I rebooted and cleaned out the old packages and such. It's working fine but all KDE is gone.

That isn't a problem since I'm using this computer strictly for testing.

---

### Post by crjackson on 2010-05-21
Here's some interesting information. 

During the Lucid testing cycle, my LCD on the testing laptop died (well, it didn't die, it when dim).  I tried everything and assumed it was a hardware problem since it was the same in the LiveCD.

After upgrading to the Maverick Kernel, my LCD is nice and bright again.  I can only assume that it's a VERY strange coincidence that it Died under Lucid and stayed that way, and just happened to kick in for Maverick testing.

OR

The Maverick Kernel fixes a problem that Lucid hasn't.

Also, my touchpad doesn't work under Maverick.

---

### Post by ronacc on 2010-05-21
it pays to keep some old live cd's around where you know everything does work ( or an old install disk ) to use to check problems like the lcd or your wifi etc . Touchpads can be a bit flaky especially early on , search the forum for posts that might apply . You can get kde back by going to synaptic and installing kde-standard , then use either the login required boot option or timed log in and you can select which WM to log into at bootup with the options menu at the bottom of the login window .

edit: you could have installed the kernel from synaptic ( or apt-get ) without doing a dist-upgrade and it wouldn't have removed all that stuff , the dist-upgrade does keep everything consistent though .

---

### Post by nanog on 2010-05-21
> and remove 40 (KDE) packages

There are obviously unresolved dependencies. When these are resolved just reinstall whatever kde package pulled those dependecies. Do not run dist-upgrade unless you are certain that any removed packages are unnecessary. In other words, read the sticky!


When upgrading by changing sources you may now have to edit repos in this directory. 

```
/etc/apt/sources.list.d
```

you can also accomplish this by editing sources via the graphical software sources tool.

its also a very good idea to comment out unecessary ppas. if you are  using ppas during development i strongly recommend downloading  the ppa-purge package from xorg-edgers ppa or get-deb.

---

### Post by crjackson on 2010-05-21
> **nanog said:**
> There are obviously unresolved dependencies. When these are resolved just reinstall whatever kde package pulled those dependecies. Do not run dist-upgrade unless you are certain that any removed packages are unnecessary. In other words, read the sticky!


When upgrading by changing sources you may now have to edit repos in this directory. 

```
/etc/apt/sources.list.d
```

you can also accomplish this by editing sources via the graphical software sources tool.

its also a very good idea to comment out unecessary ppas. if you are  using ppas during development i strongly recommend downloading  the ppa-purge package from xorg-edgers ppa or get-deb.

Good idea about editing the additional sources lists.  I already have that ppa and ppa-purge installed.

Thanks

---

### Post by crjackson on 2010-05-21
> **ronacc said:**
> it pays to keep some old live cd's around where you know everything does work ( or an old install disk ) to use to check problems like the lcd or your wifi etc . Touchpads can be a bit flaky especially early on , search the forum for posts that might apply . You can get kde back by going to synaptic and installing kde-standard , then use either the login required boot option or timed log in and you can select which WM to log into at bootup with the options menu at the bottom of the login window .

edit: you could have installed the kernel from synaptic ( or apt-get ) without doing a dist-upgrade and it wouldn't have removed all that stuff , the dist-upgrade does keep everything consistent though .

Well, what I meant by kde not working wasn't the desktop.  I don't use the kde WM.  I meant that the 3 kde applications I normally use were removed along with the kde-basefiles.

BUT the latest round of updates put all the kde files back, and the kde application are working again.

I do have older LiveCD's around, but I have had troubles with the screen flickering when opening and closing so I jumped to the mistake conclusion that the LCD crapped all the way out.  I didn't even test with an older LiveCD because "I JUST KNEW" my screen died.

---

### Post by crjackson on 2010-05-21
> **ronacc said:**
> it pays to keep some old live cd's around where you know everything does work ( or an old install disk ) to use to check problems like the lcd or your wifi etc . Touchpads can be a bit flaky especially early on , search the forum for posts that might apply . You can get kde back by going to synaptic and installing kde-standard , then use either the login required boot option or timed log in and you can select which WM to log into at bootup with the options menu at the bottom of the login window .

edit: you could have installed the kernel from synaptic ( or apt-get ) without doing a dist-upgrade and it wouldn't have removed all that stuff , the dist-upgrade does keep everything consistent though .

Thanks, I knew I could have selectively installed packages, but I just had the urge run Ba** to the wall and see what happened.  This is a testing machine so it wouldn't have upset me if everything got borked.  I'm just happy to see the bright LCD again.

---

### Post by crjackson on 2010-05-21
> **ranch hand said:**
> You can also see that change log in synaptic or aptitude.

In synaptic you simply highlight the package in question, click on the "Package" menu and select "Download Changelog".

What Update Mangler is really good for is going to System>Administration>Software Sources and unchecking "Check for Updates" under the Updates tab, then going to System>Preferences>Startup Applications and unchecking "Update Notifier".

As far as I can see this is the only thing it is good for.  It does help to get you a little more familiar with your System menu.

I followed your suggestion and got rid of the annoying update notifier.  I don't mind it on my main systems, but it is rather a pain with a testing version.

---

### Post by Starks on 2010-05-23
> **crjackson said:**
> I ran sudo apt-get upgrade and it did nothing (because I had already upgraded those packages with the update manager).

It was reporting Maverick 10.10 but running on the Lucid Kernel.  So I jumped in with both feet **and BLINDLY ran sudo apt-get dist-upgrade**.

It pulled in about 65 more packages and remove 40 (KDE) packages. It updated me to the newest Kernel.

I rebooted and cleaned out the old packages and such. It's working fine but all KDE is gone.

That isn't a problem since I'm using this computer strictly for testing.
You should've used a sudo aptitude upgrade

---

### Post by crjackson on 2010-05-23
> **Starks said:**
> You should've used a sudo aptitude upgrade

Because...?

---

### Post by LKjell on 2010-05-23
> **crjackson said:**
> Because...?

Because you should never ever try dist-upgrade if you do not know what you are doing. aptitude's upgrade is almost identical to apt-get's upgrade. The difference is that aptitude will install new packages while apt-get won't. Therefore if you did aptitude upgrade it will install all those packages that you needed. However, you do not need that now since the debian rules have changed and you can do a normal apt-get upgrade. 

In the end it means have patience if you do not know what to do.

---

### Post by 23meg on 2010-05-23
> **crjackson said:**
>  I jumped in with both feet and BLINDLY ran sudo apt-get dist-upgrade.

> **crjackson said:**
> It pulled in about 65 more packages and remove 40 (KDE) packages.

> **crjackson said:**
> That isn't a problem since I'm using this computer strictly for testing.

It may not have been an immediate problem in this particular case, but generally, blindly dist-upgrading / accepting a partial upgrade in Update Manager *is* going to give you problems particularly in the development releases.

If you wonder why, [this sticky thread]("http://ubuntuforums.org/showthread.php?t=1479146") has the details.

---

