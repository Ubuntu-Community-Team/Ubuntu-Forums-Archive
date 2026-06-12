---
title: "Amarok version mismatch ?"
date: 2009-01-12
forum: Multimedia Software
---

### Post by akwatve on 2009-01-12
Hi

I have installed Amarok2 (according to adept manager) with KDE 4.1 but when I click on Amarok->Help->About amarok, It shows me version number as "1.4.10" for kde 3.5.10

I am not sure whats wrong here. Can anyone help ?

Thanks in advance

---

### Post by pluviosity on 2009-01-15
Maybe it's a mismatch, or it could have been accidentally left unchanged.  Are you sure you have the newer Amarok installed?

---

### Post by akwatve on 2009-01-15
Well, I use adept manager to install/remove stuff. My adept says I have Amarok 2. So I am going by that. And I did try to remove and reinstall Amarok just make sure I do install Amarok 2. But still it shows up as 1.4.10


The interesting thing is it says "KDE 3.5.10". I surely have installed KDE 4.1

---

### Post by eightmillion on 2009-01-15
> **akwatve said:**
> Well, I use adept manager to install/remove stuff. My adept says I have Amarok 2. So I am going by that. And I did try to remove and reinstall Amarok just make sure I do install Amarok 2. But still it shows up as 1.4.10


The interesting thing is it says "KDE 3.5.10". I surely have installed KDE 4.1

Could you open a terminal and run this command and post the output?
> apt-cache policy amarok amarok-kde4

Amarok 2 is in the package amarok-kde4. You probably just have the package amarok installed.

---

### Post by akwatve on 2009-01-16
Here is the output :
> 
> sudo apt-cache policy amarok amarok-kde4
amarok:
  Installed: 2:1.4.10-0ubuntu3
  Candidate: 2:1.4.10-0ubuntu3
  Version table:
 *** 2:1.4.10-0ubuntu3 0
        500 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) intrepid/main Packages
        100 /var/lib/dpkg/status
W: Unable to locate package amarok-kde4


---

### Post by eightmillion on 2009-01-16
> **akwatve said:**
> Here is the output :

It looks like you have to add: 
> deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main
to you /etc/apt/sources.list

Then you should be able to do '**sudo aptitude update && sudo aptitude install amarok-kde4**' to get Amarok 2 installed.

---

### Post by akwatve on 2009-01-16
Hmmm I was finally able to install the right version. But shouldn't Ubuntu update process take care of including new package sources in the list ?
At least adept should not report incorrect version number.

Thanks a ton for your help. I really appreciate it.

---

### Post by akwatve on 2009-01-16
Just an update to document stuff ...

Apparently KDE uses phonon which hopelessly assumes alsa (or pulseaudio god knows what)

I have OSS and phonon refuses to use it. I see quite a few posts on lack of sound with phonon. The whole thing forced me to get rid of Amarok2 altogether and go back to Amarok1.4
Old is Gold!!

Thanks a lot eightmillion for your help though.

---

