---
title: "KDE and Compiz, systemsettings and simple-ccsm"
date: 2011-03-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by afoglia on 2011-03-20
I was trying to figure out why under the KDE system settings, when I go under Default Applications > Window Manager, select Compiz, and press the Configure button, I get the error message "Running the configuration tool failed."  I tracked it down to the file /usr/share/kde4/apps/ksmserver/windowmanagers/compiz.desktop.  In there is where the Compiz configure tool is set to "simple-ccsm".

Not only do I only have ccsm installed, I imagine most people do.  I've never heard of this simple-ccsm tool, and it's not a suggested package of either the kdebase-runtime-data or the compiz package.  Should it be changed to use ccsm instead (or at very least suggest the simple-ccsm package)?

Also, I can't even install simple-ccsm.  I get the error:

```
$ sudo apt-get install simple-ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages
```

But I have both of those packages already installed:

```
$ dpkg -l compizconfig-settings-manager python-compizconfig
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version           Description
+++-=================-=================-==================================================
ii  compizconfig-sett 0.9.4-0ubuntu2    Compiz configuration settings manager
ii  python-compizconf 0.9.4-0ubuntu1    Compizconfig bindings for python
```

Any ideas what the real problem could be?

---

### Post by mc4man on 2011-03-21
Don't use kubuntu so can't be too helpful
There is no currently compatible simple-ccsm so it's likely a mistake it's being set in the configure.
You may want to file a bug on.  or edit the file to ccsm, or  wait a bit,  - you should be able to open (configure) compiz by running ccsm however one does so  in kubuntu
  
I seriously  doubt natty will ship with ccsm, though I'd think they'd need to provide some limited means to access some plugins (unityshell for instance

Also based on the last changelog for compiz it would seem a new simple-ccsm will happen at some point


> 
compiz (1:0.9.4-0ubuntu7) natty; urgency=low

  * debian/control:
    - breaks on old simple-ccsm until a new one for 0.9 is available

---

### Post by Sef on 2011-03-21
> sudo apt-get install simple-ccsm

```
If you are using KDE,use kdesu instead of sudo.
```

---

### Post by Amaranth on 2011-03-21
No, running kdesu isn't needed when running a terminal program and wouldn't help here.

As for when we'll get a new simple-ccsm, probably not until next cycle (11.10). I haven't seen anyone working on it and it's apparently rather low priority for the unity team right now or more likely not even on their radar. Patches welcome though. :)

---

### Post by afoglia on 2011-03-21
> **mc4man said:**
> Don't use kubuntu so can't be too helpful
There is no currently compatible simple-ccsm so it's likely a mistake it's being set in the configure.
You may want to file a bug on.  or edit the file to ccsm, or  wait a bit,  - you should be able to open (configure) compiz by running ccsm however one does so  in kubuntu

Yeah, I can run it fine from the command line or from the application launcher.  This is more of a loose end that I feel merits addressing.  It just feels odd that a required package (for kubuntu) doesn't use the setting manager "suggested" by the compiz package, but rather one that I had never heard of.  I'll file a bug report/request about this.

> I seriously  doubt natty will ship with ccsm, though I'd think they'd need to provide some limited means to access some plugins (unityshell for instance

Why wouldn't natty ship with compiz?  Does unity use a different window manager by default?  (I lose track of all the changes.)

> Also based on the last changelog for compiz it would seem a new simple-ccsm will happen at some point

Thanks for pointing that changelog out.  I'm still confused how apt is figuring out there is a problem and why the error message isn't helpful.  I thought the dependencies were all that mattered.  (dpkg apparently gets further, but still encounters errors.)

---

### Post by VMC on 2011-03-21
> **afoglia said:**
> Why wouldn't natty ship with compiz?  Does unity use a different window manager by default?  (I lose track of all the changes.)
ccsm is compiz settings manager, not to be confused with compiz itself.


> **afoglia said:**
> Thanks for pointing that changelog out.  I'm still confused how apt is figuring out there is a problem and why the error message isn't helpful.  I thought the dependencies were all that mattered.  (dpkg apparently gets further, but still encounters errors.)What errors messages. Try using ```
sudo apt-get -f install
``` ,to fix any errors.

---

### Post by mc4man on 2011-03-21
> Why wouldn't natty ship with compiz? Does unity use a different window manager by default? (I lose track of all the changes.)

What I was referring to was ccsm (compizconfig-settings-manager

The reason I can't see it as part of the default install is there are some plugins and settings of them that  can seriously impact an install, even make it somewhat  unusable.

I can't see ubuntu ever providing this opportunity to users
(they don't even enable the relatively innocuous  File Management by default

---

### Post by afoglia on 2011-03-22
> **VMC said:**
> ccsm is compiz settings manager, not to be confused with compiz itself.


What errors messages. Try using ```
sudo apt-get -f install
``` ,to fix any errors.

Well, it just says there are errors, but not with any detail.

```
$ sudo dpkg -i simple-ccsm_0.8.2-0ubuntu1_all.deb 
[sudo] password for afoglia: 
Selecting previously deselected package simple-ccsm.
(Reading database ... 449687 files and directories currently installed.)
Unpacking simple-ccsm (from simple-ccsm_0.8.2-0ubuntu1_all.deb) ...
dpkg: dependency problems prevent configuration of simple-ccsm:
 compiz-core (1:0.9.4-0ubuntu7) breaks simple-ccsm (<< 0.9) and is installed.
  Version of simple-ccsm to be configured is 0.8.2-0ubuntu1.
dpkg: error processing simple-ccsm (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 simple-ccsm
```

With "-D 77777", the relevant messages are:

```
D000040:     checking Breaks
D000400:       checking breaker compiz-core virtbroken <none>
dpkg: dependency problems prevent configuration of simple-ccsm:
 compiz-core (1:0.9.4-0ubuntu7) breaks simple-ccsm (<< 0.9) and is installed.
  Version of simple-ccsm to be configured is 0.8.2-0ubuntu1.
dpkg: error processing simple-ccsm (--install):
 dependency problems - leaving unconfigured
D010000: trigproc_run_deferred

```

But there's a bug in the simple-ccsm package someone filed on Friday for this issue, and I don't even care to install simple-ccsm, so I won't bother going any deeper.

---

### Post by kio_http on 2011-04-02
I would advise you to use kwin for desktop effects.

Kwin desktop composition can be accessed in system settings, desktop effects.

Technically, compiz and KDE 4 do exactly mix properly. It does "work" but there are glitches and conflicts with KDE's processes.

---

