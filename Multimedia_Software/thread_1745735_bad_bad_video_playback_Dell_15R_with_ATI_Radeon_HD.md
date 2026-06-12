---
title: "bad bad video playback Dell 15R with ATI Radeon HD 5470 Graphics card"
date: 2011-05-01
forum: Multimedia Software
---

### Post by sinbaddd on 2011-05-01
hi,

i just bought a new Dell inspiron 15 R laptop with ATI RADEON HD 5470 graphics
card. i installed lastest version ubuntu. i am using vlc to play video files. 
the video playback is not smooth especially when the movements are fast. 
it is really irritating to watch movies. i don't think there is any problem with vlc.
i couldnt find the drivers for graphic card, but ubuntu showed an option
to download the ATI/AMD proprietary FLGRX drivers. after installing those
drivers i got the screen resolution of 1368/768. but the video play back is bad
i think it has something to do with the drivers.i  couldnt find the relevant drivers
anywhere not even with ati/amd official website. because of this i am thinking of
switching back to windows. i hope someone helps me find a solution.

thanks

---

### Post by sinbaddd on 2011-05-01
has anyone faced the same problem. Does anyone know where to get
ATI Radeon HD 5460 Graphics card drivers ? please share.

thanks

---

### Post by inobe on 2011-05-01
sinbad, ati seems to be releasing better drivers than they did in the past, be grateful, because back when it was horrid to state the least.

personally i only purchase nvidia graphics or laptops with it.

but as i stated, ati/amd is getting better at it.

things you can try [http://ubuntuforums.org/showpost.php?p=10566446&postcount=1](http://ubuntuforums.org/showpost.php?p=10566446&postcount=1)

and you can add the swat repo to get the latest and greatest ati drivers, unlike those found in hardware drivers now.

basically, add the ppa, reload sources, then load hardware drivers, choose most recent then activate.

or in terminal do

```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

you should then see all that will be upgraded.

---

### Post by inobe on 2011-05-01
oops forgot to provide link to swat ppa

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by beew on 2011-05-02
> **inobe said:**
> 
personally i only purchase nvidia graphics or laptops with it.



Unfortunately many new Nividia laptops don't work on Linux because of Optimus.

---

### Post by sinbaddd on 2011-05-03
> **inobe said:**
> oops forgot to provide link to swat ppa

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

hi inobe, thanks i will give it a try.
i really hope ati will do better to provide good drivers.
that's the least expected of from them.
i did not know about the ati linux drivers issue otherwise
i would've gone for nvidia as well :(

thanks

---

