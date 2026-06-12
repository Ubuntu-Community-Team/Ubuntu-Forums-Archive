---
title: "gedit removed"
date: 2011-02-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by katrama on 2011-02-04
I did a dist-upgrade to natty yesterday. Since then I cant install gnome-panel.

How do I get the Applications, preferences running?

I tried to print a pdf and it tells /usr/lib/backend/cups/hp does not exists.

Even gedit was removed. Any idea why this happened?

I am using a laptop HP2540p.

Any answers for this?

---

### Post by cariboo on 2011-02-04
Have you tried:

```
apt-get -f install
``` 

To install the missing packages?

---

### Post by ronacc on 2011-02-04
natty is still alpha did you intend to test it ? if you did try updating , things are changing fast .

---

### Post by Quackers on 2011-02-04
I think gedit was one of the packages that the python-gobject update removed, along with firefox et al (about 3 python-gobject updates ago :-) )

---

### Post by Harry33 on 2011-02-04
> **katrama said:**
> I did a dist-upgrade to natty yesterday. Since then I cant install gnome-panel.
How do I get the Applications, preferences running?
I tried to print a pdf and it tells /usr/lib/backend/cups/hp does not exists.
Even gedit was removed. Any idea why this happened?
I am using a laptop HP2540p.
Any answers for this?

Upgrading distribution to a development version is always a risk and at least a good knowledge is needed in order to know what is happening.
In fact it is a lot easier to upgrade to pre-alfa1 than it is to upgrade to alfa2 or even alfa3.
A number of packages have gone through ABI bumps, their name has changed, dependencies has been renewed and yet it is still alfa with a number of interesting bugs.
It is almost impossible to say anything else than perhaps you should reinstall Maverick.

If this setup was not the only one you have, you may of course download Natty alfa ISO and make a clean installation with it (formatting partitions).
Here:
[http://cdimage.ubuntu.com/releases/natty/alpha-2/](http://cdimage.ubuntu.com/releases/natty/alpha-2/)

---

### Post by jerrylamos on 2011-02-04
Beats me.  This is a fresh install of Alpha 2.  In Unity I did Ctrl-Alt-t to get a teminal session and did a "gedit" which fired right up.

I've got multiple partitions with Lucid 10,04, Maverick 10.10, and a couple Natty's.  My impression is daily upgrades on top of Natty eventually start screwing up, so I do a fresh install from time to time.

Now I don't like Unity but I do run it on the two of my five test pc's that "Compiz" chooses to run on just because I'm testing Ubuntu looking for bugs.

Jerry

---

### Post by katrama on 2011-02-05
I tried apt-get -f install

I did a recovery boot and repaired the packages. This removed the firefox and gedit. It was visible on the terminal and I was surprised. 

I have some important installations on my machine. So I will not be able to format the partition.

Will have to wait for the next release.

---

### Post by zika on 2011-02-05
> **Quackers said:**
> I think gedit was one of the packages that the python-gobject update removed, along with firefox et al (about 3 python-gobject updates ago :-) )Gedit was one of the packages that was offered to be removed in partial-upgrade offered during the python-gobject "crisis" [http://ubuntuforums.org/showthread.php?t=1681049](http://ubuntuforums.org/showthread.php?t=1681049). It seems that OP did dist-upgrade (which, very often, means partial-upgrade) in a bad moment.
Moral: no partial upgrades, i.e. monitor the list of packages that are offered to be removed... [http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by Harry33 on 2011-02-05
Natty alfa2 with the latest updates does not have any more problems with pygobject.
Also python2.6 is not reinstalled.
The working version of pygobject is 2.27.0+git20110131-0ubuntu6.
Gedit and Firefox do not create unmet dependencies now.

---

### Post by rburkartjo on 2011-02-05
gedit also still working for me

---

### Post by zika on 2011-02-05
> **Harry33 said:**
> Natty alfa2 with the latest updates does not have any more problems with pygobject.
Also python2.6 is not reinstalled.
The working version of pygobject is 2.27.0+git20110131-0ubuntu6.
Gedit and Firefox do not create unmet dependencies now.
That's right. But, I, still, think that OP issued dist-upgrade command in a (very) bad momment and got struck with that partial upgrade we were talking w.r.t. pygobject... Bad luck...

He could get the list of removed packages from my posts in [http://ubuntuforums.org/showthread.php?t=1681049](http://ubuntuforums.org/showthread.php?t=1681049)...

---

