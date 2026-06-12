---
title: "Reaktor 5 working under WINE"
date: 2007-09-19
forum: Multimedia Production
---

### Post by stmiller on 2007-09-19
Ubuntu Feisty 64bit
Linux 2.6.22.1 compiled kernel
Wine 0.9.45 - winehq provided repos

Reaktor 5.1.0.010

It works! No screen artifacts. It is NOT slow or sluggish. Set CPU usage to 100% just to be sure.
MIDI I/O *works* with my USB midi device. You may have to adjust the latency setting in the Reaktor audio prefs. 

Under the Reaktor prefs it detects my AMD X2 CPU as normal:

Number of Processors: 2
MMX Support: present
ISSE Support: present
3DNow Support: present
ISSE-2 Support: present

[[img]http://xs119.xs.to/xs119/07383/reaktor1.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs119&d=07383&f=reaktor1.png)

---

### Post by orange2k on 2007-09-20
Great news!
Im a long time Energy XT user and Im used to work with a lot of VST plugins, which I miss running native XT Linux version in Ubuntu.
But Im gonna try to run the win version of Energy XT via wine/wine-asio to be able to use VST-s in Ubuntu...

Cheers...

---

### Post by stmiller on 2007-09-20
Whoa, I had not idea there was a native Energy-XT version for Linux!  ](*,)

Very cool...

---

### Post by justin whitaker on 2007-09-20
Wow. That's awesome!

---

### Post by orange2k on 2007-09-20
Check the Energy XT web site...
I also found a couple of synth plug-ins that run just fine with the Linux version. There is also a plug-in pack (MDA plug-ins) available there, that has been ported to Linux, consisting of many effects and a few instruments. Also in the XT2 you have the synth/sampler built-in - capable of some very unique timbres...

But as I said, I miss all those free VST-s...sadly you can use them only with the win version...:(

---

### Post by dveble on 2007-09-21
wineasio eXT2 runs "almost" as good as the native Linux
version. (well, with win vsts :) )

---

### Post by stmiller on 2007-09-21
I submitted info on Reaktor 5 to the winehq database, but when submitting an entry, it has to be 'approved,' however long that takes. So hopefully I can get this into the database and more people can use Reaktor in Linux.

I'm purposely avoiding newer update releases of Reaktor, as the updates put in annoying license-check software to verify your install. It's a headache and a mess dealing with that, even with a legit license and serial. So I'm sticking to this slightly older version for my purposes. YMMV.

I am curiously awaiting a 32bit compatibility library of jack to use wine-jack, as right now in 64bit Ubuntu [the only wine audio option is alsa]("http://ubuntuforums.org/showthread.php?t=555084").

---

