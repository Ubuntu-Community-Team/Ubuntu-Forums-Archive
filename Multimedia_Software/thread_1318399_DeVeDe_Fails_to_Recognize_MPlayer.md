---
title: "DeVeDe Fails to Recognize MPlayer"
date: 2009-11-07
forum: Multimedia Software
---

### Post by PrinceOfDarkness on 2009-11-07
I just recently updated my Ubuntu 9.04 to Ubuntu 9.10 and when I changed the upgrade to simply do a "distro upgrade" I kept my sound.conf or whatever and other .conf files the same because I've done specific stuff with ALSA...

I've also maxed out DeVeDe and MPlayer in terms of updates and they BOTH show up in the synaptic package manager "installed" list

However, DVD's won't encode with "tovid", "qdvdauthor", or "DeVeDe" because of an MPlayer error...

They say I'm missing a shared library that is literally sitting on the "installed list" of my package list

Also, DeVeDe tells me to install MPlayer when I already have it, as I'm an avid user of SMPlayer, so I don't know what DeVeDe's deal is...

Any thoughts?

---

### Post by ticket on 2009-11-07
Maybe you have an old mplayer version installed in /usr/local/bin ?
You can check by typing:
```
which mplayer
```

---

### Post by PrinceOfDarkness on 2009-11-07
> **ticket said:**
> Maybe you have an old mplayer version installed in /usr/local/bin ?
You can check by typing:
```
which mplayer
```

Thanks for the tip, my synaptic package manager says I'm all the way up to date tho:

"Installed Version": 3:1.0~svn-r29485-1

That's also listed as the "Latest Available Version"

---

### Post by mc4man on 2009-11-07
not sure where you got that mplayer package but considering you like/use smplayer maybe add rvm's karmic mplayer repo and update mplayer and mencoder to his latest versions

see here
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)


(many people are having varying issues multimedia wise from upgrades to karmic vs fresh installs

---

### Post by PrinceOfDarkness on 2009-11-07
> **mc4man said:**
> not sure where you got that mplayer package but considering you like/use smplayer maybe add rvm's karmic mplayer repo and update mplayer and mencoder to his latest versions

see here
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)


(many people are having varying issues multimedia wise from upgrades to karmic vs fresh installs

My mplayer came from here:

"Package Created with CheckInstall 1.6.1"

Also, I followed every **exact** instruction on here:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

and have still come up with the inability to use DeVeDe...

---

### Post by andrew.46 on 2009-11-07
Hi Prince,

> **PrinceOfDarkness said:**
> My mplayer came from here:

"Package Created with CheckInstall 1.6.1"

Hmmm... you may very well have 2 versions installed. Could you run:

```
sudo find /usr -iname 'mplayer'
```

All the best,

Andrew

---

### Post by PrinceOfDarkness on 2009-11-07
Thanks for your help, here's what your code suggestion yielded:

[IMG]http://i200.photobucket.com/albums/aa4/angelicusmortis/Screenshot.png[/IMG]

---

### Post by PrinceOfDarkness on 2009-11-07
Don't know if that helps or not but when I took the PPA suggestion no changes occurred...

(To* my* knowledge anyway...)

---

### Post by rvm4000 on 2009-11-07
You have two mplayers installed, one in /usr/bin and another in /usr/local/bin, being the latter the one you compiled yourself. I think you have to uninstall it.

---

### Post by PrinceOfDarkness on 2009-11-07
> **rvm4000 said:**
> You have two mplayers installed, one in /usr/bin and another in /usr/local/bin, being the latter the one you compiled yourself. I think you have to uninstall it.

Thanks so much for that tip, DeVeDe works now :)

However,

Ever since I've done all this with the PPA and such, everybody's skin in every video of mine is blue...

Even in SMPlayer, Kaffeine, and VLC :(

Oh...and all the environments are pinkish...

---

### Post by rvm4000 on 2009-11-07
> **PrinceOfDarkness said:**
> Ever since I've done all this with the PPA and such, everybody's skin in every video of mine is blue...

Sounds like a problem of xv...

See if you can fix it with the video equalizer in smplayer. Otherwise I guess if you use another video driver (gl, x11..) you'll get a good image.

---

### Post by PrinceOfDarkness on 2009-11-07
thanks so much for your time and the advice...

however...

it apparently simply needed a medibuntu update and a reboot :)

all good now...

---

### Post by PrinceOfDarkness on 2009-11-08
Unfortunately, the color and the basic "running" of DeVeDe are fine now...

**However**,

DeVeDe fails miserably when trying to incorporate DVDauthor into the picture and it won't create my dvd titles

it's fine for creating the MPEG but it fails with the titles badly

it says i have maybe not enough free space

i have 150+ GB on an NTFS filesystem (ergo 4+ GB files are fine)

and the project takes like 2GB

any ideas?
[U]
P.S. here's what synaptic says about all three programs...[/U]

**I have:**

*QDVDAuthor* - Version = 1:1.8.0+dfsg-0.0ubuntu2

*DVDAuthor* - Version = 0.6.14-3ubuntu4

*DeVeDe *- Version = 3.14.0-0ubuntu5

*MPlayer* - Version = 2:1.0~rc3+svn20090904-0karmic5

(ALL of my versions MATCH the latest available, btw)

---

### Post by mc4man on 2009-11-08
I know this may seem strange but I think you'll need to force your version of mencoder back to the repo version 

I don't use devede and on my main install the ffmpeg libs, mplayer ect. are my owm versions and a quick test shows devede works. ( and creates the dvd tree, ect.

On a tester with stock stuff and the rvm mplayer I noticed that yesterday but you seemed fine so didn't mention.

You can keep the rvm mplayer which is better than the karmic one but give this a try.

In synaptic, search mencoder and highlight it, click on the 'Package' tab -> force version...
There should be a choice for the repo version ...(20090426-1ubnutu10

Choose it and then click apply. 

 After the forced package is installed synaptic** will immediately mark it for upgrade**, close out synaptic with the "quit and discard changes" or it will upgrade you back


See if that helps

---

### Post by PrinceOfDarkness on 2009-11-08
I will do that right now and see if it works, thanks **very** much for your assistance, it is **much** appreciated 

:)

---

### Post by PrinceOfDarkness on 2009-11-08
> **mc4man said:**
> I know this may seem strange but I think you'll need to force your version of mencoder back to the repo version 

I don't use devede and on my main install the ffmpeg libs, mplayer ect. are my owm versions and a quick test shows devede works. ( and creates the dvd tree, ect.

On a tester with stock stuff and the rvm mplayer I noticed that yesterday but you seemed fine so didn't mention.

You can keep the rvm mplayer which is better than the karmic one but give this a try.

In synaptic, search mencoder and highlight it, click on the 'Package' tab -> force version...
There should be a choice for the repo version ...(20090426-1ubnutu10

Choose it and then click apply. 

 After the forced package is installed synaptic** will immediately mark it for upgrade**, close out synaptic with the "quit and discard changes" or it will upgrade you back


See if that helps


Thank You **SO** Much...

You're officially _awesome_ now what with how beautifully that works, it's fine now :)

---

