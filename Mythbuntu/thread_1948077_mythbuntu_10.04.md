---
title: "mythbuntu 10.04"
date: 2012-03-27
forum: Mythbuntu
---

### Post by macaronij on 2012-03-27
hi i have mythbuntu 10.04 whit mythtv 0.22 working properly
i also have a pc desktop whit ubuntu 11.10
i want to install mythfront end in my ubuntu 11.10 but the repository already have mythtv 0.24
can i add a mythbuntu repository whit mythtv 0.22 in my ubuntu 11.10?
(installing from source is hard)
tx for your help!!!

---

### Post by ijumpship on 2012-03-27
Theoretical,You can all you have to do include the Lucid Lynx repositories in your Apt and then update it,then install from this.
However in the past I had nothing but problems (such as sound,etc) this way,so what I do is use a live cd as a front-end on my earlier machine.

Or 

Do a dual boot by partitioning the drive with the desktop and use that to install the mythbuntu 10.04

With Lucid Lynx (10.04) I had nothing but problems with sound,video cards,turner etc.so I would not recommend that method.

As I always recommend to everyone keep the data on a different drive from your boot partition,that way you can easily upgrade or revert or back up
Hope I am of some help.

---

### Post by nickrout on 2012-03-28
You are better to update your existing machine to 0.24-fixes via mythbuntu-repos. 0.22 is old and unsupported. 0.24-fixes works fine on 10.04.

---

### Post by macaronij on 2012-03-28
> **ijumpship said:**
> ,so what I do is use a live cd as a front-end on my earlier machine.
Or 
Do a dual boot by partitioning the drive with the desktop and use that to install the mythbuntu 10.04


i would prefer a method that doesn t need a reboot to watch tv, then another reboot to use the desktop

i tryed to update my mythtv to 0.24 but i had a lot of problems, i will stay whit this working system for now 

my only option is to install mythtv 0.22 from source?

---

### Post by klc5555 on 2012-03-28
> **macaronij said:**
> i would prefer a method that doesn t need a reboot to watch tv, then another reboot to use the desktop

i tryed to update my mythtv to 0.24 but i had a lot of problems, i will stay whit this working system for now 

my only option is to install mythtv 0.22 from source?

In theory a remote frontend-only in Ubuntu could be done by installing mythtv-common and mythtv-frontend from the old-releases server: [http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/)

However, there is a unique problem with v. 0.22. Installing the two main myth packages will require libmyth 0.22 as a dependency. libmyth-dev won't fulfill the dependency. The original libmyth 0.22 was buggy, and even though it was eventually patched, the online repositories and archives have been pretty thoroughly scrubbed of binary debfiles both of the original version of libmyth 0.22 and the patched version. 

So, your options will be to track down the seriously hard to find debfile for libmyth-0.22 fixes (and hope its bugs don't bite you if you find and install it, 'cause it's certainly **unsupported**) or supply this lib from a source other than a debfile. 

Or move to a slightly later version of mythtv. If 0.24.x doesn't do it for you, as you indicated, you may find the 0.23.x series somewhat less obnoxious.

---

### Post by nickrout on 2012-03-28
Unless you have cleaned out /var/cache/apt/archives, the .deb packages should be there on your existing machine.

---

### Post by tgm4883 on 2012-03-28
> **klc5555 said:**
> In theory a remote frontend-only in Ubuntu could be done by installing mythtv-common and mythtv-frontend from the old-releases server: [http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/)

However, there is a unique problem with v. 0.22. Installing the two main myth packages will require libmyth 0.22 as a dependency. libmyth-dev won't fulfill the dependency. The original libmyth 0.22 was buggy, and even though it was eventually patched, the online repositories and archives have been pretty thoroughly scrubbed of binary debfiles both of the original version of libmyth 0.22 and the patched version. 

So, your options will be to track down the seriously hard to find debfile for libmyth-0.22 fixes (and hope its bugs don't bite you if you find and install it, 'cause it's certainly **unsupported**) or supply this lib from a source other than a debfile. 

Or move to a slightly later version of mythtv. If 0.24.x doesn't do it for you, as you indicated, you may find the 0.23.x series somewhat less obnoxious.

While I agree with you that the OP needs to update to a more current MythTV version via the Mythbuntu repos, I just wanted to point out that the Mythbuntu team doesn't remove our old repositories. What this means is that you can get our latest build of 0.22 from [https://launchpad.net/~mythbuntu/+archive/trunk-0.22](https://launchpad.net/~mythbuntu/+archive/trunk-0.22) (which is highly likely one of the very last 0.22 builds from the fixes branch).

---

### Post by klc5555 on 2012-03-28
> **tgm4883 said:**
> While I agree with you that the OP needs to update to a more current MythTV version via the Mythbuntu repos, I just wanted to point out that the Mythbuntu team doesn't remove our old repositories. What this means is that you can get our latest build of 0.22 from [https://launchpad.net/~mythbuntu/+archive/trunk-0.22](https://launchpad.net/~mythbuntu/+archive/trunk-0.22) (which is highly likely one of the very last 0.22 builds from the fixes branch).

Well and sure enough there it is! Right at [https://launchpad.net/~mythbuntu/+archive/trunk-0.22/+packages](https://launchpad.net/~mythbuntu/+archive/trunk-0.22/+packages)
 libmyth 0.22 along with its fellow mythtv 0.22 debs. Hooray!

I wish the thing could be posted also at [http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/) which would make it a whole lot easier to find, since all the other libmyth debs since 0.17 are there. Even the Debian repositories themselves nuked libmyth 0.22.

Anyhow, if despite our warnings the original poster is trying to set up 0.22 on a remote frontend-only, he should uninstall any mythtv packages he may have installed on the remote frontend machine. He should then use gdebi or the equivalent to install the 0.22 version of mythtv-common, followed by libmyth 0.22, followed by mythtv-frontend 0.22. I don't think there are any other dependencies, but if gdebi says there are, they will have to be gotten and installed also.

If the thing installs (and it should), then running "mythfrontend" from a user prompt should bring up the frontend configuration screens, where he can point mythfrontend to the machine running his mythbackend, providing that backend has been correctly configured for remote frontend connections. And he should be ready to roll.

If the OP's backleveled mythtv0.22 installation works and he wishes to keep it, he should lock the installed mythtv 0.22 packages using Synaptic, so that Update Manager doesn't try to upgrade them on a daily basis.

---

### Post by macaronij on 2012-03-28
> **klc5555 said:**
> Well and sure enough there it is! Right at [https://launchpad.net/~mythbuntu/+archive/trunk-0.22/+packages](https://launchpad.net/~mythbuntu/+archive/trunk-0.22/+packages)
 libmyth 0.22 along with its fellow mythtv 0.22 debs. Hooray!

I wish the thing could be posted also at [http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/m/mythtv/) which would make it a whole lot easier to find, since all the other libmyth debs since 0.17 are there. Even the Debian repositories themselves nuked libmyth 0.22.

Anyhow, if despite our warnings the original poster is trying to set up 0.22 on a remote frontend-only, he should uninstall any mythtv packages he may have installed on the remote frontend machine. He should then use gdebi or the equivalent to install the 0.22 version of mythtv-common, followed by libmyth 0.22, followed by mythtv-frontend 0.22. I don't think there are any other dependencies, but if gdebi says there are, they will have to be gotten and installed also.

If the thing installs (and it should), then running "mythfrontend" from a user prompt should bring up the frontend configuration screens, where he can point mythfrontend to the machine running his mythbackend, providing that backend has been correctly configured for remote frontend connections. And he should be ready to roll.

If the OP's backleveled mythtv0.22 installation works and he wishes to keep it, he should lock the installed mythtv 0.22 packages using Synaptic, so that Update Manager doesn't try to upgrade them on a daily basis.

Excelent step-by-step post, than you all for the awnser.
Solved!

---

