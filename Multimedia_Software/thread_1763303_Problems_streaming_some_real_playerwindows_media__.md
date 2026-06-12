---
title: "Problems streaming *some* real player/windows media  radio stations since reinstall"
date: 2011-05-20
forum: Multimedia Software
---

### Post by Dáire Fagan on 2011-05-20
Since removing Ubuntu 10.10 and fresh installing Xubuntu 11.04 I have had problems with *some* radio streams.

For instance [http://media.newstalk.ie/listen_live/popup](http://media.newstalk.ie/listen_live/popup) works fine, but if one clicks on the link for RTE 1 on the right-hand side of [http://www.rte.ie/radio/](http://www.rte.ie/radio/), which I cannot link because it's javascript, it does not work anymore whether I select Real Player or Windows Media format.

For me the interface that appears is as per screenshot, and it used to look different for me so I suspect the problem might just be that I am missing a plugin?

[IMG]http://oi54.tinypic.com/a4adte.jpg[/IMG]

I have installed mozilla-plugin-vlc but it made no difference.

---

### Post by ron999 on 2011-05-20
> **dusf said:**
> 

I have installed mozilla-plugin-vlc but it made no difference.

Hi
RTE1 opens in it's own player window.
The 'Windows Media' option plays for me using **gecko-mediaplayer** plugin with Firefox. Look in Synaptic Package Manager.

---

### Post by Dáire Fagan on 2011-05-20
> **ron999 said:**
> Hi
RTE1 opens in it's own player window.

As it does for me, I just could not link it because it's javascript :)

> **ron999 said:**
> The 'Windows Media' option plays for me using **gecko-mediaplayer** plugin with Firefox. Look in Synaptic Package Manager.

```
dusf@banshee:~$ dpkg -s gecko-mediaplayer
Package: gecko-mediaplayer
Status: install ok installed

```

Thanks, but I installed it and restarted Firefox but it made no difference, that said the interface you have is, or is very similar to how mine used to look.

---

### Post by beew on 2011-05-22
I am not sure what you mean by "does not link". Anyway, the real player option works with stand alone player but not embedded, the window media player option works embedded My screenshot is a bit different though. The control is at the lower right corner instead of the horizontal bar on the upper screen. 

I use replayer for playing realplayer streams (gecko doesn't seem to work) and gecko for win media player and most other things.

---

### Post by Dáire Fagan on 2011-05-22
After installing gecko-mediaplayer it now looks as per the screenshot, but still with no sound from RTE Radio.

---

### Post by myxer on 2011-06-04
Hi - I've got the same problem with RTE and realplayer / 11.04 in general.  My problem seems to be some conflict with lsb and my 64 bit system.  I've got version 4 lsb but in trying to install realplayer11gold.deb I get a message saying i need lsb>=3.1.  I've taken all the 3X lsb off but no joy at all.  tried solutions in [https://help.ubuntu.com/community/RealPlayerInstallationMethods ]("https://help.ubuntu.com/community/RealPlayerInstallationMethods")... but zip

---

