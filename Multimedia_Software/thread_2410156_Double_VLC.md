---
title: "Double VLC?"
date: 2019-01-11
forum: Multimedia Software
---

### Post by Daveski17 on 2019-01-11
Hello,

I have VLC on Ubuntu 16.04 LTS which I recently upgraded from 14.04 LTS. I’ve noticed there are two versions of VLC in Ubuntu Software.

[ATTACH=CONFIG]282178[/ATTACH]

This one (above) 2.2.2-5ubuntu0.16.04.4 and 3.0.6 (below).

[ATTACH=CONFIG]282179[/ATTACH]

I have 3.0.6. installed. I’m just curios as to why there are two different versions in the repo. I'm guessing 3.0.6 is the most recent?

My copy runs fine although occasionally the ‘traffic cone’ icon disappears from the launcher for no reason.

Thanks.

---

### Post by CatKiller on 2019-01-11
2.2.2-5 is the version that's in the 16.04 repository. I'd imagine the other one is a snap package. Snaps have some limitations.

---

### Post by Daveski17 on 2019-01-11
> **CatKiller said:**
> 2.2.2-5 is the version that's in the 16.04 repository. I'd imagine the other one is a snap package. Snaps have some limitations.

Thanks for the reply. Which would be the best for 16.04 LTS?

---

### Post by CatKiller on 2019-01-11
> **Daveski17 said:**
> Thanks for the reply. Which would be the best for 16.04 LTS?

Whichever you like. They're both supported. The limitations of snaps are things like where they can read or write to, stuff like that. To (potentially) make them more portable.

I've not used Unity or snaps, so I don't know which might be causing your vanishing icon.

---

### Post by Daveski17 on 2019-01-11
> **CatKiller said:**
> Whichever you like. They're both supported. The limitations of snaps are things like where they can read or write to, stuff like that. To (potentially) make them more portable.

I've not used Unity or snaps, so I don't know which might be causing your vanishing icon.

OK thanks.

---

### Post by monkeybrain20122 on 2019-01-12
> **Daveski17 said:**
> Thanks for the reply. Which would be the best for 16.04 LTS?

VLC before version 3.0 does not work for 360 degree videos, so the old version does have some limitations. I compile vlc from source so my version is up to date also doesn't have the limitations and bugs of snap. it gives me the best of all worlds. You can  try this [ppa]("https://launchpad.net/~jonathonf/+archive/ubuntu/vlc-3") which provides vlc3.0.6 for ubuntu 16.04 if you don't want to compile from source.
Add the ppa to your source 
```
sudo add-apt-repository ppa:jonathonf/vlc-3
```

then
```
sudo apt update 
sudo apt upgrade
```

Now you can remove the snap version
```
sudo snap remove vlc
```

---

### Post by Daveski17 on 2019-01-12
> **monkeybrain20122 said:**
> VLC before version 3.0 does not work for 360 degree videos, so the old version does have some limitations. I compile vlc from source so my version is up to date also doesn't have the limitations and bugs of snap. it gives me the best of all worlds. You can  try this [ppa]("https://launchpad.net/~jonathonf/+archive/ubuntu/vlc-3") which provides vlc3.0.6 for ubuntu 16.04 if you don't want to compile from source.
Add the ppa to your source 
```
sudo add-apt-repository ppa:jonathonf/vlc-3
```

then
```
sudo apt update 
sudo apt upgrade
```

Now you can remove the snap version
```
sudo snap remove vlc
```

Thanks for the information and the link. 

[ATTACH=CONFIG]282187[/ATTACH]

I have 3.0.6.

---

### Post by monkeybrain20122 on 2019-01-13
> **Daveski17 said:**
> Thanks for the information and the link. 

[ATTACH=CONFIG]282187[/ATTACH]

I have 3.0.6.

I know, but your 3.0.6 is a snap, that is the whole pt about this thread, isn't it?

---

### Post by Daveski17 on 2019-01-13
> **monkeybrain20122 said:**
> I know, but your 3.0.6 is a snap, that is the whole pt about this thread, isn't it?

I'm new to 16.04 so the *snap* version was a bit puzzling. I couldn't understand why two versions in the repo. I only use it to watch DVD's so the icon occasionally disappearing isn't a biggie for me. My default player is SMPlayer. Thanks for the help anyway.

---

### Post by monkeybrain20122 on 2019-01-13
> **Daveski17 said:**
> I'm new to 16.04 so the *snap* version was a bit puzzling. I couldn't understand why two versions in the repo. I only use it to watch DVD's so the icon occasionally disappearing isn't a biggie for me. My default player is SMPlayer. Thanks for the help anyway.

As said deb and snap are different ways to package  and distribute software. deb is the standard way with shared libs and what not. snap is a beta technology, it is a container with bundled dependencies. Deb packages integrate well with the system but as you may notice the .deb packages provided by the repo are usually old. snap on the other hand is supposed to allow easy updates but right now IMO (as well as other reports on the forum) the technology still has glitches and is not mature. ppa is a way to install .deb packages and get updates (as long as the ppa is maintained) through third party repos. There are some here who don't like it, but IMO the risk is exaggerated, as long as you use well known ppas there is rarely any problem in my experience.

If you install software from the Software Centre then you may get a snap or a deb. If both snap and deb versions are available for a software then the Software Centre would give you the snap. On the other hand if you install packages with the terminal (apt) or with the synaptic package manager then you always get the .deb version. Synaptic is a gui package manager with many features (much more flexible than the Software Centre). It is not installed by default, but can be easily installed with the software centre or sudo apt install synaptic. So Software Centre doesn't use the standard repos.

---

### Post by Daveski17 on 2019-01-13
> **monkeybrain20122 said:**
> As said deb and snap are different ways to package  and distribute software. deb is the standard way with shared libs and what not. snap is a beta technology, it is a container with bundled dependencies. Deb packages integrate well with the system but as you may notice the .deb packages provided by the repo are usually old. snap on the other hand is supposed to allow easy updates but right now IMO (as well as other reports on the forum) the technology still has glitches and is not mature. ppa is a way to install .deb packages and get updates (as long as the ppa is maintained) through third party repos. There are some here who don't like it, but IMO the risk is exaggerated, as long as you use well known ppas there is rarely any problem in my experience.

If you install software from the Software Centre then you may get a snap or a deb. If both snap and deb versions are available for a software then the Software Centre would give you the snap. On the other hand if you install packages with the terminal (apt) or with the synaptic package manager then you always get the .deb version. Synaptic is a gui package manager with many features (much more flexible than the Software Centre). It is not installed by default, but can be easily installed with the software centre or sudo apt install synaptic. So Software Centre doesn't use the standard repos.

Thanks, that's a great help and makes a lot of sense. I've considered installing Synaptic in the past.

---

