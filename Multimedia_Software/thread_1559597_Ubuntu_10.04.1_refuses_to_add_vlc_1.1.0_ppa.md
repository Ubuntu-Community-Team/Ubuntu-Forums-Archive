---
title: "Ubuntu 10.04.1 refuses to add vlc 1.1.0 ppa"
date: 2010-08-23
forum: Multimedia Software
---

### Post by Michael577 on 2010-08-23
I have the new Ubuntu 10.04.1 and I heard that the new VLC was released. I found out that I had to add a PPA to the repository, so I added it but I keep getting this error. 

```
michael@michael-laptop:~$ sudo add-apt-repository ppa:c-korn/vlc
Error: can't find signing_key_fingerprint at https://launchpad.net/api/1.0/~c-korn/+archive/vlc
``` [COLOR=#008080][I]
[COLOR=Black]I also added this twice![/COLOR]

deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main[/I][/COLOR]

this is from [COLOR=Cyan][Softipedia]("http://news.softpedia.com/news/First-Look-VLC-1-1-0-on-Ubuntu-10-04-145279.shtml")[/COLOR]. I also added the key that was on the site (which is attached) . so can anyone help me out with this? oh and I get this on the software sources after adding it

```
Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
```

---

### Post by luigi_mb on 2010-08-23
Unfortunately the PPA for vlc is no longer active. 

/luigi

---

### Post by Michael577 on 2010-08-23
> **luigi_mb said:**
> Unfortunately the PPA for vlc is no longer active. 

/luigi

Well If that's the case then how do you get it now?

---

### Post by mc4man on 2010-08-23
Well you could build it yourself (the safest) or try another ppa.
ppa's for vlc range from safe to not so - the ones that replace your ffmpeg libs are the most risky and best enabled

A good ppa that replaces your ffmpeg libs will also offer replacements for the apps/plugins ect. that will break.

A perfectly safe ppa for lucid is this one (will get you up to 1.1.0
[https://launchpad.net/~bdrung/+archive/backports](https://launchpad.net/~bdrung/+archive/backports)

One that replaces ffmpeg libs and appears to do a good job overall is this one (1.1.3 - the current stable - better enabled than the above one
[https://launchpad.net/~lucid-bleed/+archive/ppa](https://launchpad.net/~lucid-bleed/+archive/ppa)

 I tested that  ppa -  a comment here (post 1200
[http://ubuntuforums.org/showthread.php?t=786095&page=120](http://ubuntuforums.org/showthread.php?t=786095&page=120) 

After testing the ppa I emailed the maintainer that his ppa broke the repo mplayer and he quickly built and added a replacement, that is a definite positive

---

### Post by sidzen on 2010-08-23
> **Michael577 said:**
> Well If that's the case then how do you get it now?

You might try adding this source to your /etc/apt/sources.list  [PHP]deb http://www.debian-multimedia.org squeeze main non-free[/PHP]Then [PHP]apt-get update && apt-get install debian-multimedia-keyring && apt-get update[/PHP]Then, simply install vlc:  [PHP]apt-get install vlc[/PHP]Hope this works!

---

### Post by Michael577 on 2010-08-24
> **mc4man said:**
> Well you could build it yourself (the safest) or try another ppa.
ppa's for vlc range from safe to not so - the ones that replace your ffmpeg libs are the most risky and best enabled

A good ppa that replaces your ffmpeg libs will also offer replacements for the apps/plugins ect. that will break.

A perfectly safe ppa for lucid is this one (will get you up to 1.1.0
[https://launchpad.net/~bdrung/+archive/backports]("https://launchpad.net/%7Ebdrung/+archive/backports")

One that replaces ffmpeg libs and appears to do a good job overall is this one (1.1.3 - the current stable - better enabled than the above one
[https://launchpad.net/~lucid-bleed/+archive/ppa]("https://launchpad.net/%7Elucid-bleed/+archive/ppa")

 I tested that  ppa -  a comment here (post 1200
[http://ubuntuforums.org/showthread.php?t=786095&page=120](http://ubuntuforums.org/showthread.php?t=786095&page=120) 

After testing the ppa I emailed the maintainer that his ppa broke the repo mplayer and he quickly built and added a replacement, that is a definite positive

Thank YOU:KS! The backports PPA worked. the lucid-bleed PPA didn't (It made a mess and confusions on my computer and it wouldn't install.) I'll wait for the next dist. to be released (10.10) before trying to upgrade vlc to 1.1.3. Well I'm going to mark this post SOLVED! So thank you everyone (Especially mc4man) for helping me out! 8)

---

### Post by andrew.46 on 2010-08-24
Hi sidzen,

> **sidzen said:**
> You might try adding this source to your /etc/apt/sources.list  

```
deb http://www.debian-multimedia.org squeeze main non-free
```



It was a few months back but the vlc developers were none too happy about that particular repository:

Important notice for Debian/Ubuntu user
[http://forum.videolan.org/viewtopic.php?f=13&t=70719](http://forum.videolan.org/viewtopic.php?f=13&t=70719)

Perhaps things have changed?

Andrew

---

### Post by sidzen on 2010-08-25
> **andrew.46 said:**
> Hi sidzen,
It was a few months back but the vlc developers were none too happy about that particular repository:
Important notice for Debian/Ubuntu user
[http://forum.videolan.org/viewtopic.php?f=13&t=70719](http://forum.videolan.org/viewtopic.php?f=13&t=70719)
Perhaps things have changed?

Andrew

Thank you for the update, Andrew.  I was unaware of that particular problem and I got my info second-hand from a source I trusted.  Was out-of-commission for a couple weeks, also!  Sorry to hear of the problems with VLC -- on top of the wodim issue.

Maybe I'll just go to Slack and stay there ! ? :frown:

---

### Post by Bobbyrne01 on 2010-09-05
sweet got 1.1.3 working by addin the ppa to d repos . . tanx mc4man :)

---

### Post by slumbergod on 2010-09-10
I just tried the lucid-bleed ppa and my mplayer died so maybe it wasn't fixed after all. I had to ppa-purge it then add the one ppa that gives me a perfectly working vlc without messing up ffmpeg, mplayer, or smplayer...

[http://ppa.launchpad.net/ferramroberto/vlc/ubuntu](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu)

---

