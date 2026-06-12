---
title: "Amarok alternatives &amp; Amarok without KDE Desktop"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by PartisanEntity on 2007-03-22
As far as functionality goes, which of the many musiplayers comes close to Amarok? (im interested in easy management of large mp3 collections and good handling of all the various online streaming radio methods).

And, is there any up to date (Edgy) How To on how to install Amarok in gnome without installing the metapackage for kde-desktop?

---

### Post by Gargamella on 2007-03-22
i heard of Listen to be a very good one for features and to be close to amarok (but i prefear and use amarok).

Anyway it worths a try.

---

### Post by PartisanEntity on 2007-03-23
hmm Listen is not bad, nice and simple yet has the features I am looking for.

I too was very impressed with Amarok, but I don't want to install KDE-desktop since I have no need for it and it seemed a bit extreme to install the whole metapackage just to use Amarok, so I was looking for an alternative, Listen might be it.

---

### Post by allix on 2007-03-23
As far as I can tell, there is no package called kde-desktop in official edgy repos and the [amarok package]("http://packages.ubuntu.com/edgy/kde/amarok") does'nt seem to depend on one either. When I was running gnome-flavored Ubuntu I just installed the amarok och libxine-extracodecs packages. No problem there.

---

### Post by stokedfish on 2007-03-23
> **PartisanEntity said:**
> As far as functionality goes, which of the many musiplayers comes close to Amarok?
None, seriously.

[http://amarok.kde.org/forum/index.php/topic,13388.msg18066.html#msg18066](http://amarok.kde.org/forum/index.php/topic,13388.msg18066.html#msg18066)

Exaile and the other Amarok clones are nice, but totally lacking.

I'd just stick to Amarok, it's simply ahead of the game.

---

### Post by PartisanEntity on 2007-03-23
> **allix said:**
> As far as I can tell, there is no package called kde-desktop in official edgy repos and the [amarok package]("http://packages.ubuntu.com/edgy/kde/amarok") does'nt seem to depend on one either. When I was running gnome-flavored Ubuntu I just installed the amarok och libxine-extracodecs packages. No problem there.

I actually tried to install Amarok today from the repos but I got some errors every time I tried to launch it.

---

### Post by scorn_ik on 2007-03-24
I was succesfully installed amarok and was able to launch it without any error but it doesn't play any media file.......please help..what is the prob?

---

### Post by stokedfish on 2007-03-24
sudo apt-get install amarok-xine

---

### Post by scorn_ik on 2007-03-24
after executing this line , the ouput is--->

Reading package lists... Done
Building dependency tree... Done
amarok-xine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


now what ? will now amarok run in gnome perfectly?

---

### Post by allix on 2007-03-24
> **scorn_ik said:**
> I was succesfully installed amarok and was able to launch it without any error but it doesn't play any media file.......please help..what is the prob?

Install the libxine-extracodecs package using synaptic. Make sure both universe and multiverse repos are enabled.

---

### Post by Kreuger on 2007-03-24
There's a program I read about yesterday called [Exaile]("http://www.exaile.org/trac") which aims to copy amarok with a GTK interface, you could look into that. I never got around to installing it to try it out but the screenshots look quite a bit like amarok.

---

### Post by scorn_ik on 2007-03-24
It works :guitar: .......thanks guys and specially allix ...:)

---

### Post by PartisanEntity on 2007-03-27
> **stokedfish said:**
> **amarok-xine**

So is this a stand-alone version of Amarok? i.e. it runs in Gnome without the Kubuntu metapackage being installed?

---

