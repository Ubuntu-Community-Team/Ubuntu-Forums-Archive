---
title: "devede stopped working"
date: 2011-03-16
forum: Multimedia Software
---

### Post by thegoonden on 2011-03-16
Getting a little tired of applications working one day but not the next....this morning it's devede.
Firstly it somehow VANISHED from the system...all on it's own.
Then when I reinstalled it, it spits this guff out...........


/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import gio
ImportError: could not import gio
DeVeDe 3.16.9
Locale: en_GB.UTF-8
Using package-installed files
Traceback (most recent call last):
  File "/usr/bin/devede", line 146, in <module>
    arbol=gtk.Builder()
AttributeError: 'module' object has no attribute 'Builder'




(yesterday it was mplayer...I watched a view videos...and then it just started segfaulting on every video including the ones it just played. As such as well as any advice re: devede I would like to hear how to turn all ubuntu's sneaky background crap off so it acts like linux and not windows)


Thanks
PS: don't suggest 2mandvd, it's i386 only

---

### Post by thegoonden on 2011-03-16
LOL....how p*ssed off was I up there?

Sorry for vinegar posting.

Research seems to suggest this is just 64bit being 64bit???

Any ideas?

---

### Post by thegoonden on 2011-03-19
Wow....no fix...I take it Ubuntu is just broken by design then....are Microsoft secretly funding it to drive people away?

---

### Post by mc4man on 2011-03-19
> **thegoonden said:**
> Wow....no fix...I take it Ubuntu is just broken by design then....are Microsoft secretly funding it to drive people away?
No, but certainly can be broken by the user.
The 2 apps mentioned are interrelated and also with the shared ffmpeg libs.

> Firstly it somehow VANISHED from the system...all on it's own.
Can't see that happening.
Are you using any ppa's
Did you install or run an update/upgrade prior to this 'vanishing'
Are you using the ubuntu repo versions of devede, mplayer/mencoder and the shared ffmpeg libs?

---

### Post by thegoonden on 2011-03-19
mplayer fixed itself with a reboot (very windowsy behaviour), there were no stuck mplayer processes or the like....and there are so many layers of ubuntu stuff that I can't really make head nor tail of ps ax's output anymore, so cannot tell if some related process was stalled/dead.
No update happened prior to mplayer's death it literally played a video, then segfaulted on every subsequent attempt to play.


As for Devede, it's the stock and standard one from the standard repos, the only modifications to my sources are uncommenting anything restricted....I got fed up on other machines of flakey stuff from outside the ubuntu repos.

This morning I was getting that error as above, and now, despite no reboots or updates the program is working again...how can that be?

I know ubuntu prides itself on being the linux that winvictims can cope with, but does it have to emulated THAT aspect of things?

What can it be? A stuck lock file that got cleaned up eventually?
An essential background process that died and init cleared the corpse away eventually?
I'm not used to all the layers upon layers in Ubuntu, and get rather baffled by never being able to edit a config file, but the file that generates the file that generates the config file, and such things....there must be 10 times as many processes running in my ubuntu that my gentoo on boot, it's all too much for my wee head to keep perfect track of and know what every process is up to.

I dunno about user screwing it up BTW...I've not force fed any software or interfered with it's brains to any great extent.

I am fairly sure there was no manual update between it being there and vanishing, but surely if it had been autoremoved for some reason, there would have been bitching when I reinstalled it?


As I said, googling the error just gave me endless pages of shrugged shoulders and "64bit is broken, just accept that" posts.

For the sake of a few meg of RAM, as soon as I work out an elegant way to make 64bit go away, to be replaced with my exact current software in 32bit mode, I'll do it (dumping a list to re-inject into dpkg on the new system wont work because of arch specifications in many package names).


Anyway, thanks greatly for trying to help......I wish it hadn't fixed itself because now neither you, nor I, nor any future searchers will be any nearer understanding. :(

---

