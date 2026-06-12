---
title: "Upgrade from 12.04 to 14.04 is having issues with MCC"
date: 2016-11-14
forum: Mythbuntu
---

### Post by krisbee2000 on 2016-11-14
I feel stupid because I can't figure this out from the forums.  I upgraded 12.04 to 14.40 (not clean install) - and MCC now no longer works.  Every time I go in to the repositories section, the dropdown is blank.  Every time I try to retrieve I get this error:
URL Error: [Errno 110] Connection timed out [http://download.mythbuntu.org/repos/repos.db](http://download.mythbuntu.org/repos/repos.db)

Every time I try to change any of the settings in that screen I get this error:
Exception in compareState of plugin Repositories

```
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 360, in compareState
    plugin.compareState()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 193, in compareState
    SELVER = self.convertVersion(self.repobox.get_active_text())
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 185, in convertVersion
    if VERSION.endswith(".x"):
AttributeError: 'NoneType' object has no attribute 'endswith'

```

I have the following PPAs turned on in my package manager:
[http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu)

Am I doing something wrong?  Other than that, just a few little hiccups and this upgrade went pretty smoothly.  Since I have lots of little tweaks here and there in my system I really didn't want to do a clean install - and this is otherwise working...

Thanks in advance!

---

### Post by tgm4883 on 2016-11-16
> **krisbee2000 said:**
> I feel stupid because I can't figure this out from the forums.  I upgraded 12.04 to 14.40 (not clean install) - and MCC now no longer works.  Every time I go in to the repositories section, the dropdown is blank.  Every time I try to retrieve I get this error:
URL Error: [Errno 110] Connection timed out [http://download.mythbuntu.org/repos/repos.db](http://download.mythbuntu.org/repos/repos.db)

Every time I try to change any of the settings in that screen I get this error:
Exception in compareState of plugin Repositories

```
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 360, in compareState
    plugin.compareState()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 193, in compareState
    SELVER = self.convertVersion(self.repobox.get_active_text())
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 185, in convertVersion
    if VERSION.endswith(".x"):
AttributeError: 'NoneType' object has no attribute 'endswith'

```

I have the following PPAs turned on in my package manager:
[http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu)

Am I doing something wrong?  Other than that, just a few little hiccups and this upgrade went pretty smoothly.  Since I have lots of little tweaks here and there in my system I really didn't want to do a clean install - and this is otherwise working...

Thanks in advance!

No need to reinstall, it's not that big of an issue and doesn't affect the install (plus it would probably still happen in the reinstall).

The issue is that you're still on 14.04 and that the URL for downloading the list of available releases changed in Mythbuntu. You have 1 of 2 options to resolve this.

1) (By far the easiest) You can add the updates PPA manually by running the following command.

```
sudo add-apt-repository ppa:mythbuntu/0.28
```


2) You can edit the python file with the wrong URL. The file that needs edited is

```
/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py
```

Find the line that contains this

```
http://download.mythbuntu.org/repos/repos.db
```

And change that URL to this

```
http://people.ubuntu.com/~tgm4883/repos.db
```

(It's python, so only change that line as spacing and whitespace are important)

Then restart MCC.

---

### Post by krisbee2000 on 2016-11-16
Thank you SO MUCH!  This in-place upgrade went pretty damn smoothly on the backend - only one line to comment out for apache but other than that, just this issue and I've been good.  My frontend had some other issues, but I figured them out as well.

Thank you again!  I am going to drag my feet for about a year before moving to 16.04 - I do plan on getting from.27 to .28 shortly, though.

---

### Post by uteck on 2016-11-16
You will probably have to do a fresh install to get past 15.10, since the change to systemd is a major pain.  My laptop had been updated since 10.04 but the systemd change was too much and I had finally had to start over.  But that is a year or so down the road for you, but be ready to back up your database and restore to a new install.

---

### Post by jp23 on 2016-12-06
> **krisbee2000 said:**
> I feel stupid because I can't figure this out from the forums.  I upgraded 12.04 to 14.40 (not clean install) - and MCC now no longer works.  Every time I go in to the repositories section, the dropdown is blank.  Every time I try to retrieve I get this error:
URL Error: [Errno 110] Connection timed out [http://download.mythbuntu.org/repos/repos.db](http://download.mythbuntu.org/repos/repos.db)

Every time I try to change any of the settings in that screen I get this error:
Exception in compareState of plugin Repositories

```
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 360, in compareState
    plugin.compareState()
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 193, in compareState
    SELVER = self.convertVersion(self.repobox.get_active_text())
  File "/usr/share/mythbuntu/plugins/python/mythbuntu_repos.py", line 185, in convertVersion
    if VERSION.endswith(".x"):
AttributeError: 'NoneType' object has no attribute 'endswith'

```

I have the following PPAs turned on in my package manager:
[http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu)

Am I doing something wrong?  Other than that, just a few little hiccups and this upgrade went pretty smoothly.  Since I have lots of little tweaks here and there in my system I really didn't want to do a clean install - and this is otherwise working...

Thanks in advance!

No you are not doing a thing wrong. What has happened is that someone has changed the repos url and has not bothered to update the relevant components.

Here's the file you need to take a look at /usr/share/mythbuntu/plugins/python/mythbuntu_repos.p
In that file is a line that says  [http://download.mythbuntu.org/repos/repos.db](http://download.mythbuntu.org/repos/repos.db)

that should read   [http://people.ubuntu.com/~tgm4883/repos.db](http://people.ubuntu.com/~tgm4883/repos.db)

I seem to recall that I had to reboot to (a) Get mcc (Myth control center) to start in anything less than 5 minutes (it was clearly timing out after trying to reach an unreachable url)  (b) See the actual repositories.

I really don't understand how people can make changes like this and not fix the relevant updates. Since mythbuntu is no more - it seems the people who really cared about making this a stable usable system are no longer there and so a more slapdash approach to the project is being taken. Alas. It was the same in Knoppmyth. Sic Transit Gloria Mythbuntu

---

### Post by tgm4883 on 2016-12-06
> **jp23 said:**
> No you are not doing a thing wrong. What has happened is that someone has changed the repos url and has not bothered to update the relevant components.

Here's the file you need to take a look at /usr/share/mythbuntu/plugins/python/mythbuntu_repos.p
In that file is a line that says  [http://download.mythbuntu.org/repos/repos.db](http://download.mythbuntu.org/repos/repos.db)

that should read   [http://people.ubuntu.com/~tgm4883/repos.db](http://people.ubuntu.com/~tgm4883/repos.db)

I seem to recall that I had to reboot to (a) Get mcc (Myth control center) to start in anything less than 5 minutes (it was clearly timing out after trying to reach an unreachable url)  (b) See the actual repositories.

I really don't understand how people can make changes like this and not fix the relevant updates. Since mythbuntu is no more - it seems the people who really cared about making this a stable usable system are no longer there and so a more slapdash approach to the project is being taken. Alas. It was the same in Knoppmyth. Sic Transit Gloria Mythbuntu

The Mythbuntu team recommends that you update to the latest LTS release and states that a release is supported until shortly after the next LTS release. Nobody fixed Mythbuntu 14.04 when the URL changed because it was no longer supported.

---

### Post by AlecJ on 2016-12-15
Still getting errors with MCC on start up  "Exception in applyStateToGUI of plugin Plugins"

there is no where to enter a mythweb password and the repro's number box is non existent.

I followed tmg4338 by updating the repro to 0.28

rebooted, to same problem
then changed the URL line  
same problem?

Mythweb is working, found a way to set it up from command line, but i'm unable to change anything, it won't save any new setting.
was trying to use it to rearrange the channels as I did before in 12.04

---

