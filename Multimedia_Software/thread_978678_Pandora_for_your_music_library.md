---
title: "Pandora for your music library"
date: 2008-11-11
forum: Multimedia Software
---

### Post by unknownmosquito on 2008-11-11
Anybody know of a music player or a plugin for a music player that allows dynamic smart playlist generation a la Pandora or the Genius feature on the new iPods? It'd be nice to choose something like the Shins whilst on shuffle and not get Metallica as the next song, but still not have to choose manually, if you catch my drift.

---

### Post by aeiah on 2008-11-11
i dont know but there should be. that'd be rather clever. i think some of the leading players like amarok will show suggestions grabbed from last.fm and perhaps add it to a smart playlist. there's also things such as genre and tags of course but these are less clever. have you investigated the newest amarok and banshee? i havent, but thats where id look if i wanted that feature.

---

### Post by unknownmosquito on 2008-11-11
I've played with banshee, and I'm waiting anxiously for Amarok 2.0, although it frustrates me to use a KDE player in Gnome; it looks so bad.
Banshee has its own weird issues; It doesn't group albums w/ multiple artists as one albums, so I have a soundtrack listed umpteen times, and while it reports your listening habits to last.fm and lets you listen to last.fm, it doesn't do anything dynamic within your own library.

---

### Post by ichi@YUKI on 2008-11-11
there are a lot of music players out there.. i tried exaile and i enjoyed it. ^_^

---

### Post by aeiah on 2008-11-11
im pretty sure exaile doesnt have this feature, although it is a nice player, yes.

---

### Post by unknownmosquito on 2008-11-11
Exaile always seemed unstable to me. It would crash if I skipped a bunch of songs, which I end up doing when it's on shuffle....
(and so it goes :P )

---

### Post by aeiah on 2008-11-11
oh, perhaps it does actually, sorry.
recent changes:
"A dynamic playlist which fetches similar tracks from last.fm was implemented."

now whether this streams similar tracks or uses local tracks but last.fm metadata is unclear. i use exaile but havent updated. its a nice player, especially if you consider amarok cumbersome in a gnome environment

---

### Post by unknownmosquito on 2008-11-11
First of all, the Last.FM plugin for Banshee streams music; it doesn't pull from the local library, so that is not what I want. If I want to stream music, I'll just listen to Pandora. 

But I found something that seems to do what I want, but I can't get it to install.

It's called Mirage, and it's a plugin for Banshee: [http://hop.at/mirage//](http://hop.at/mirage//)

It should be a simple
```
sudo apt-get install banshee-extension-mirage
```
but when I run banshee from the terminal I get this error:
```
Assembly not found: Banshee.Services, Version=1.2.1.31134, Culture=neutral
WARNING: [Banshee.Mirage,0.3] Could not load some add-in assemblies: Could not load file or assembly 'Banshee.Services, Version=1.2.1.31134, Culture=neutral' or one of its dependencies.

```

and I'm not sure what that all means, except that the extension doesn't show up in Banshee. I'm running Banshee v1.4 and it looks like Mirage v0.3 is in the Banshee PPA repo, which you install by putting 
```

deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main

```
in your /etc/apt/sources.list.

Any ideas?

[EDIT]
Turns out this is because .3 is only compatible with Banshee v1.2; .4 is compatible with Banshee v1.4; I compiled version 0.4 from source but am having trouble making it run. Console output:

```
[Warn  14:14:27.246] Extension `/Banshee/ServiceManager/Service/__nid_13' not started: Could not load type 'Banshee.Mirage.MiragePlugin' from assembly 'Banshee.Mirage, Version=0.4.0.0, Culture=neutral'.

```

---

### Post by Mr. Picklesworth on 2008-11-22
You can get the latest Banshee from the Banshee team PPA. I just noticed that I have that in my Software Sources; probably confused a lot of people when I posted about Mirage myself. Indeed, after that repo is added it all "just works" without any magic tricks.

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

And indeed, Mirage is pretty awesome, although best results seem to require a huge music library. (It would be nice if it sometimes streamed things for those with small hard drives like myself, rather than suddenly playing MC Hawking when it runs out of ideas).

---

### Post by unknownmosquito on 2008-11-30
Yeah I got it working; I popped over to the Google group: 
[http://groups.google.com/group/mirage-list](http://groups.google.com/group/mirage-list)
and got help directly from the developer.
It's pretty nice; not exactly what I wanted, but close enough to tide me over :)

---

