---
title: "What is libept0 and does it criticly require?"
date: 2010-07-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-07-30
I just removed this package in order to download all other updates could it cause any problems?

Thanks in advance.

---

### Post by hansdown on 2010-07-30
Hi aviramof.

It seems to affect your ability to use apt.

Might you, reconsider?

[https://launchpad.net/ubuntu/lucid/amd64/libept0](https://launchpad.net/ubuntu/lucid/amd64/libept0)

---

### Post by ranch hand on 2010-07-30
Yes it is one of the critical foundation libs for apt and for all I know it may well effect synaptic too, maybe update mangler.   I do not think I would remove it.

Kubuntu used to use adept as the package manager (old gnome app replaced by synaptic) and I know it depended on it.

[http://packages.debian.org/search?keywords=libept-dev](http://packages.debian.org/search?keywords=libept-dev)

---

### Post by mc4man on 2010-07-31
I don't see any issue with it gone except update-manager may under certain circumstances  cause a small temporary issue with synaptic. (hard to duplicate


libept0
Reverse Depends:
  packagesearch
  goplay

---

### Post by aviramof on 2010-07-31
If it so important then why synaptic asked me to remove it in order to update other packages?

and when i try to reinstall it i get:
libept0:
 Depends: libapt-pkg-libc6.10-6-4.8  but it is not installable

but i don't have libapt-pkg-libc6.10-6-4 in synaptic.

Commit Log for Sat Jul 31 06:18:25 2010

removed:
libept0

upgraded:
apt (0.7.25.3ubuntu10) to 0.7.26~exp12ubuntu1
apt-transport-https (0.7.25.3ubuntu10) to 0.7.26~exp12ubuntu1
apt-utils (0.7.25.3ubuntu10) to 0.7.26~exp12ubuntu1
aptitude (0.6.3-2ubuntu2) to 0.6.3-2ubuntu3
aptitude-gtk (0.6.3-2ubuntu2) to 0.6.3-2ubuntu3
libept1 (1.0.1) to 1.0.1build1
libpackagekit-glib2-14 (0.6.5-0ubuntu1) to 0.6.5-0ubuntu2
libpackagekit-qt-14 (0.6.5-0ubuntu1) to 0.6.5-0ubuntu2
packagekit (0.6.5-0ubuntu1) to 0.6.5-0ubuntu2
packagekit-backend-apt (0.6.5-0ubuntu1) to 0.6.5-0ubuntu2
python-apt (0.7.96.1ubuntu1) to 0.7.96.1ubuntu3
python-packagekit (0.6.5-0ubuntu1) to 0.6.5-0ubuntu2
synaptic (0.63.1ubuntu12) to 0.63.1ubuntu13

---

### Post by aviramof on 2010-07-31
Where can i download libapt-pkg-libc6.10-6-4.8?

---

### Post by mc4man on 2010-07-31
You should have libept1 instead (do here

---

### Post by SevenMachines on 2010-07-31
libept0 is replaced now by libept1, if you're up to date then it should remove safely without anything complaining (specifically aptitude and synaptic)

---

### Post by PaulW2U on 2010-07-31
> **SevenMachines said:**
> libept0 is replaced now by libept1, if you're up to date then it should remove safely without anything complaining (specifically aptitude and synaptic)
That's what I thought and removed libept0.

synaptic, apt-get and Update Manager all seem to work properly except that I see several lines like:

```
W: Ignoring file 'opera-beta.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```
listed when I run 'apt-get update' or 'apt-get upgrade'.

Another build of libept1 has just been released (1.03) and I have installed it but I still see these files listed which I didn't before I "upgraded". I've checked my Lucid installation and these files are also there so presumably are just backup files that should not be read?

Has anyone else updated these packages and found the same problem?

---

### Post by dino99 on 2010-07-31
no issue here with the new libept1

---

### Post by psyke83 on 2010-07-31
> **aviramof said:**
> I just removed this package in order to download all other updates could it cause any problems?

Thanks in advance.

Why do you refuse to read the sticky thread on partial upgrades? It will answer your question completely. In fact, the replies you see to this thread are merely giving you the information that you could have discovered by yourself, had you simply read the sticky thread and followed the diagnostic steps contained within.

I apologise if my reply comes across as rude, but I do recall several past instances in which you created a thread asked about a specific package or partial upgrade scenario, and you always received a reply (from myself or others), directing you to read the sticky thread. I do remember you replying at least once that you had already read the sticky, but  I find that very hard to believe.

---

### Post by ronacc on 2010-07-31
> **PaulW2U said:**
> That's what I thought and removed libept0.

synaptic, apt-get and Update Manager all seem to work properly except that I see several lines like:

```
W: Ignoring file 'opera-beta.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```
listed when I run 'apt-get update' or 'apt-get upgrade'.

Another build of libept1 has just been released (1.03) and I have installed it but I still see these files listed which I didn't before I "upgraded". I've checked my Lucid installation and these files are also there so presumably are just backup files that should not be read?

Has anyone else updated these packages and found the same problem?

Yes I'm gettinng the same warning on all the .save files , goahead and bug it, I'll confirm .

---

### Post by MacUntu on 2010-07-31
---

---

### Post by PaulW2U on 2010-07-31
> **ronacc said:**
> Yes I'm gettinng the same warning on all the .save files , goahead and bug it, I'll confirm .

Thanks, bug #612005.

---

### Post by ronacc on 2010-07-31
confirmed and added comment , here is a link to the bug , a # search wasn,t turning it up

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/612005 ](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/612005 )

---

### Post by ranch hand on 2010-07-31
Do you fellers have libept1 installed?  I am not having this problem but made sure that was installed before upgrading those packages.

Installing it removed libept0.

---

### Post by ronacc on 2010-07-31
I have libept1 installed . I think the problem is with apt though , it updated at the same time that libept0 was removed .And the warnings occur in places where libept I don't think is used

---

### Post by dagrump on 2010-07-31
It showed upgrade libept1, so I figured libept0 is out dated. I haven't seen any issues. I just upgraded for the night, no errors. So yesterdays dist-upgrade didn't break anything, well nothing I ran into any way.
I'm ready to do a clean install with A3, I have messed with stuff trying to get sound back to working so much. Frankly, I can't remember everything I jacked with? 
Might just remove the card and use the on board intel stuff.

---

### Post by aviramof on 2010-07-31
I have several problems now that when i download updates via update manager it shows that the size of all the updates is just 1kb which of course is not true and when i run the command sudo apt-get update && sudo apt-get upgrade i get this:
```
N: Ignoring file 'ubuntu-tweak-testing-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'skype.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-mozilla-daily-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'c-korn-vlc.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-tweak-stable.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dashua-compiz-c++-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-tweak-testing-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'skype.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-mozilla-daily-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'c-korn-vlc.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-tweak-stable.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dashua-compiz-c++-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'ubuntu-tweak-testing-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'skype.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-mozilla-daily-ppa-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'c-korn-vlc.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ubuntu-tweak-stable.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dashua-compiz-c++-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```
and i can't reinstall [B]libept0 it asks for libapt-pkg-libc6.10-6-4.8 that i can't find.
[/B]

---

### Post by mc4man on 2010-08-01
> i can't reinstall libept0 it asks for libapt-pkg-libc6.10-6-4.8 that i can't find.
Please read post # 8 and that should suffice.

> i get this:......... .save ect. ect

Well you could look above about a bug report - myself don't see what the issue is - the .save file should be ignored, has no affect on your ppa usage

I guess the bug filed is that by telling you it's ignoring the .save files it's 'not ignoring' them - so what..

---

### Post by aviramof on 2010-08-01
i have  libept1 install but it doesn't help.

---

### Post by MacUntu on 2010-08-01
Duped that bug, new one: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/611925](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/611925)

Workaround: ```
echo "Dir::Ignore-Files-Silently:: \"\.save$\";" | sudo tee /etc/apt/apt.conf.d/99ignoresavefiles
```

---

### Post by mc4man on 2010-08-01
> i have libept1 install but it doesn't help.
Doesn't help what, in other words -  what's wrong?

---

### Post by aviramof on 2010-08-01
Check post #19.

---

### Post by MacUntu on 2010-08-01
The 1 KB thing seems to be an update-manager bug (apt-get reports it right), the .save file warning is an apt issue ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/611925](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/611925)). libept0 is history, don't waste your time trying to install it.

---

### Post by aviramof on 2010-08-01
I didn't had this problem before later i would report it as update manager libept1 bug.

---

### Post by aviramof on 2010-08-01
Posted a bug and a picture:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/612326](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/612326)

---

### Post by altonbr on 2010-09-04
This appeared for me after installing a fresh copy Ubuntu 10.10 Maverick Meerkat beta and none of the workarounds seem to work. libept1 is installed as well.

---

