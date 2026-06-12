---
title: "Ubuntu Is Good But Managing My iPod Is Still A Big Problem"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Ekolost on 2008-07-19
Help

---

### Post by MattBD on 2008-07-19
Floola might be worth a try. It's not in the repositories, but you can grab it from [http://www.getdeb.net/app/Floola](http://www.getdeb.net/app/Floola) instead.
There's also gtkpod. If your iPod has the songs in AAC format, you'll need to install the gtkpod-aac version instead.
Both Floola and gtkpod are dedicated iPod managers, so you might find they're more likely to work than media players like Amarok.
A third option is Yamipod, but that isn't nicely packaged for Ubuntu. It's at [http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)

---

### Post by Ekolost on 2008-07-19
Help

---

### Post by Ekolost on 2008-07-19
Help

---

### Post by MattBD on 2008-07-19
I'm surprised that none of those work. I know that when the 6th generation iPods, including the 160GB Classic, were released, Apple made some changes to stop third party applications such as Amarok, Banshee and Rhythmbox working with them, although from what I heard at the time the developers of one of these applications managed to get round it in two weeks. I just would have thought that support for the Classic would have reached these applications by now.
If this is the only thing stopping you from using Ubuntu, I'd suggest you try again in a few months time when Intrepid is out. I have an 80GB iPod I bought a few weeks before the 6th gen iPods were released, and that works fine with any player I try in Linux, so it will come some time.
I'd also give Banshee and Exaile a try, both are very good media players for the Gnome desktop. Exaile has a plugin to manage iPods, and I think Banshee will do it out of the box.

---

### Post by Ekolost on 2008-07-19
Help

---

### Post by Ekolost on 2008-07-19
Help

---

### Post by MattBD on 2008-07-19
Some people have managed to get iTunes working in Wine. There are a few tutorials around, so that might be worth trying. I just did a Google search and found one at [http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html](http://www.wine-reviews.net/applications/itunes-73-on-linux-with-wine.html) but this might be out of date.
It's worth trying it in Wine, but there's certainly no guarantees and any time iTunes updates it could break compatibility. Native support is bound to improve over time though. Perhaps if you used more recent versions of the apps than are in the Ubuntu repositories - for instance, Banshee recently hit v1.0 and I think that's more recent than the version available in the Ubuntu repositories, so try grabbing that direct from the website at [http://banshee-project.org/](http://banshee-project.org/).
BTW, the package format you need for Ubuntu is called a deb package. You should normally be able to install it using a graphical app called GDebi. If you right-click on it in the Nautilus file manager, you should see the option to open it with this.

---

### Post by Pro-reason on 2008-07-19
> **Ekolost said:**
> 
I tried gtkpod which didn't recognize my songs album covers. I downloaded Floola but it wouldn't install. (I double clicked on the installation file and nothing would happen)YamiPod wouldn't install either (same reason as Floola)

That's strange.  Do it from the command line instead.

```

wget http://www.getdeb.net/download/2901/0
sudo dpkg -i floola_3.1-0~getdeb1_i386.deb
Floola

```

That will work for version 3.1.-0 of the software for Ubuntu 8.04 on standard PC architecture.

---

### Post by MattBD on 2008-07-19
> **Ekolost said:**
> By the way MattBD i googled Intrepid but im still puzzled as to what it does. Could you explain it to me?

Sorry, didn't make myself clear there. By Intrepid I mean the next version of Ubuntu, due in October, which will be called Intrepid Ibex.

---

### Post by Ekolost on 2008-07-19
Help

---

### Post by Ekolost on 2008-07-19
Help

---

### Post by MattBD on 2008-07-20
> **Ekolost said:**
> By the way MattBD what applications do you use to get podcasts?

I'm not much of a podcast listener, so there's nothing I use, but I know Rhythmbox will work, and there's also loads of dedicated apps. The one I hear the most about is gpodder, but if you open Synaptic and search for podcast, you'll find quite a few apps.

---

### Post by Ekolost on 2008-07-20
Help

---

### Post by Ekolost on 2008-07-20
Help

---

### Post by MattBD on 2008-07-20
Great to hear that it's sorted now.

---

### Post by Ekolost on 2008-07-20
Help

---

### Post by jaystrum on 2008-07-20
I am having problems with my Ipod. I was using Rythembox and was very happy with it until my Ipod went TU and I now have to restore the thing to factory settings. Only Itunes will do and I am having real trouble getting it to install through crossover office. Any suggestions?

---

### Post by Pro-reason on 2008-07-20
> **jaystrum said:**
> I am having problems with my Ipod. I was using Rythembox and was very happy with it until my Ipod went TU and I now have to restore the thing to factory settings. Only Itunes will do and I am having real trouble getting it to install through crossover office. Any suggestions?
There is a [separate forum]("http://ubuntuforums.org/forumdisplay.php?f=313") for Wine/Cedega/Crossover issues.

If Rhythmbox was working fine until your iPod failed, then perhaps you should just continue using it.

---

### Post by Ekolost on 2008-07-22
Help

---

### Post by soxs on 2008-07-22
Amarok needs a little kind of additional setup and libraries to make covers appear on your iPod.
I am sorry, atm I can#t seem to find it, but I am sure it was somewhere at the amarok homepage :-S howto do it..

---

### Post by Ekolost on 2008-07-23
Help

---

### Post by soxs on 2008-07-30
I got it:
Read here what is required to make your iPod use covers (It requires you to recompile amarok, but that's no big deal either):
[http://amarok.kde.org/wiki/Media_Device:IPod](http://amarok.kde.org/wiki/Media_Device:IPod)

---

