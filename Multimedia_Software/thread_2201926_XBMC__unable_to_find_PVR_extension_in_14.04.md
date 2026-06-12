---
title: "XBMC : unable to find PVR extension in 14.04"
date: 2014-01-26
forum: Multimedia Software
---

### Post by Pierre A on 2014-01-26
Hello,

I have just installed 14.04 on an Intel NUC to setup an HTPC using XBMC.
I want to use tvheadend to display and record digital TV. Tvheadend is working, but XBMC lacks the PVR*Add-on.

According to the wiki [http://wiki.xbmc.org/index.php?title=PVR/Backend/Tvheadend](http://wiki.xbmc.org/index.php?title=PVR/Backend/Tvheadend) it either should be already installed or I need install the ubuntu package xbmc-pvr-tvheadend-hts that is not available from apt-get.

My XBMC version is (2:12.3+dfsg1-3ubuntu1) trusty

Any help will be appreciated.

---

### Post by ajgreeny on 2014-01-26
Don't forget trusty is still only in alpha stage, though it does seem to be very good so far as Xubuntu 14.04 64bit on my machines, running both as live, zsync updated ISOs, and as a fully updated virtual machine installation using Virtualbox on my Xubuntu 12.04 64bit system.

Maybe the problems you're seeing are related to the alpha stage and lack of a full range of packages in repositories for all that you need.

---

### Post by Pierre A on 2014-01-26
Thank you for your answer.

 I know that trusty is still il alpha stage, but I need a fairly recent distro because of my thunderbolt to ethernet adaptor. I also suspect that is the reason of my problem.
Should I file a bug against XBMC package because it does not inclule PVR support as in some other distros ?

---

### Post by ajgreeny on 2014-01-26
Sorry, no idea about XBMC so can't help you there.

---

### Post by Pierre A on 2014-01-26
Thank's anyway. I hope someone will have some clue for me.

---

### Post by tad1073 on 2014-01-27
Try using the saucy repo.

---

### Post by Pierre A on 2014-01-28
I added saucy repository, but  xbmc-pvr-tvheadend-hts is still not available.

Edit : I have found a PPA with an PVR addon (xbmc-pvr-addon) : [https://launchpad.net/~team-xbmc/+archive/ppa](https://launchpad.net/~team-xbmc/+archive/ppa) ppa:team-xbmc/ppa 
I successfully install the ppa, update, but the package is still not available.

---

### Post by Pierre A on 2014-01-29
I finally solved the problem.

As there is not xbmc-pvr-tvheadend-hts in the trusty ppa, I had to add also the saucy version of this repo : deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) saucy main 
Then, after an update, I was able to install the add-on.

Thank's for those who have answered to this post.

---

### Post by leilamoniz on 2014-11-15
> **Pierre A said:**
> I finally solved the problem.

As there is not xbmc-pvr-tvheadend-hts in the trusty ppa, I had to add also the saucy version of this repo : deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) saucy main 
Then, after an update, I was able to install the add-on.

Thank's for those who have answered to this post.


im also having the same problem.
im new to ubuntu, can you plz write the codes i need to write in terminal?

thx in advance

---

### Post by Pierre A on 2014-11-15
Hi leilamoniz,

I believe that now it should work as expected.
Try to add the repository to your sources list : (I don't have a ubuntu machine here to test, I hope I am not making typos)
# nano -w /etc/apt/sources.list
Then add the following line at the end of the file (I consider you are using trusty) : deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main 
Then save with CTRL+x
Then update and install
# apt-get update
# apt-get install xbmc-pvr-tvheadend-hts

---

