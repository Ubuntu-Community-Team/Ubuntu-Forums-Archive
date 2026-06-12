---
title: "Just installed Amarok, few things"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Otterpanda on 2009-04-01
So I'm still getting used to Ubuntu, and I decided to try to grab a good media player to play songs from my ipod on. I asked a friend and he recommended Amarok. I just used sudo apt-get install amarok, and then after that was done installing. I started it up and tried to play songs from my ipod, but it said at that time it didn't support mp3 format, so I installed what was necessary to play mp3s. That made me wonder if I'm missing anything else, so those who are experienced with Amarok, am I? Also, the lyrics feature either isn't working or I'm just using it wrong. same with the artist wiki pages. Thanks for all the help you guys can give me! I really appreciate it.

---

### Post by wolfen69 on 2009-04-01
```
sudo apt-get install libxine1-ffmpeg ubuntu-restricted-extras

```
enjoy amarok.

---

### Post by Otterpanda on 2009-04-01
Thanks! :)

---

### Post by SuperSonic4 on 2009-04-01
Lyrc is really crappy script, install ruby-gtk (or something similar, I forget what it is ubuntu but it is ruby-gtk in arch) and use [Wiki-Lyrics]("http://www.kde-apps.org/content/show.php/Wiki-Lyrics?content=35151")

The artist wiki page is a bug in amarok 1.4.10 which is unlikely to be resolved since they're working on 2.x now. You can still click the external browser button to view it in firefox.

You may also want to add Bogdan's PPA to keep amarok 1.4.10 in jaunty since a lot of people prefer amarok 1.4 (including me so I bookmarked it XD): [https://edge.launchpad.net/~bogdanb/+archive/ppa](https://edge.launchpad.net/~bogdanb/+archive/ppa)

---

### Post by Otterpanda on 2009-04-01
Sorry if I sound completely noobish but I can't find anything called ruby-gtk in the synaptic package manager. As you can probably tell I'm relatively new to Linux. But also, the website is for KDE desktops, but I'm using GNOME by default, so would it still work? Once again, sorry if I'm being a total idiot.

---

### Post by wolfen69 on 2009-04-01
> **Otterpanda said:**
> Thanks! :)

i take it you got things sorted?

btw, ruby-gtk is not in the standard repos. you could just search for ruby to find what you need.

---

### Post by Excedio on 2009-04-01
> **Otterpanda said:**
> Sorry if I sound completely noobish but I can't find anything called ruby-gtk in the synaptic package manager. As you can probably tell I'm relatively new to Linux. But also, the website is for KDE desktops, but I'm using GNOME by default, so would it still work? Once again, sorry if I'm being a total idiot.
 
 
No worries dude. We were all Noobs at one point. :)
 
I'll be honest...I don't know the first thing about how to fix this problem. However, if you cannot get this to work correctly...give [Mozilla Songbird]("http://getsongbird.com/") a shot. I use it flawlessly and it has lots of add-ons.
 
mashTape will give you artist info. There is also a lyrics add-on (there are actually two, one works and the other doesn't, forgot the name of the one that works :-? ). Also has iPod support.

---

### Post by Excedio on 2009-04-01
LyricMaster is the good one. :)

---

### Post by Otterpanda on 2009-04-01
> **Excedio said:**
> No worries dude. We were all Noobs at one point. :)
 
I'll be honest...I don't know the first thing about how to fix this problem. However, if you cannot get this to work correctly...give [Mozilla Songbird]("http://getsongbird.com/") a shot. I use it flawlessly and it has lots of add-ons.

So I downloaded the tar.gz, but where do I extract it to?

---

### Post by Excedio on 2009-04-02
> **Otterpanda said:**
> So I downloaded the tar.gz, but where do I extract it to?

First...delete the file you just downloaded.

Second...Click [here]("http://files.tac-ops.net/unter-hund.com/songbird_1.1.1_i686_unter-hund-blog.deb") if you are running a 32bit machine or click [here]("http://files.tac-ops.net/unter-hund.com/songbird_1.1.1-x86_64-unter-hund-blog.deb") if you are running a 64bit machine.

Third...Click OK

Fourth...Click Install Package

---

### Post by mocoloco on 2009-04-02
Just piping in to say that I like Exaile quite a bit, it's a lot like Amarok but made to fit in with Gnome (Amarok's style is for KDE, using the QT toolkit).  I'm not one of those "purists" that won't do QT in Gnome or GTK in KDE, but I've like exaile.
My wife just uses the standard Rhythmbox with her iPod and likes it fine.

---

