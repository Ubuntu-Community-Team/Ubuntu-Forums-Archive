---
title: "ipod grrrrrr....fstab?"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Immolatus on 2007-04-24
I was wondering if anyone could tell me why it is that gtkpod can't load my ipod ( fifth generation 30G video). I have installed gtkpod, xmms. I also installed Banshee and that at least has imported all my music but I need to be able to add music to it. Do I need to edit Fstab?

Any thoughts??:confused:

---

### Post by mlind on 2007-04-24
When you plug-in your ipod, hal-daemon should make it available automatically. Your ipod should be mounted in /media directory somehere. My ipod is mounted as /media/IPOD MINI (I guess hal creates the mount point from the name of my ipod).

You can observe whats happening like this:
[LIST]
[*]watch /var/log/syslog using
```

tail -f /var/log/syslog

```
[*]Plugin your ipod and watch the messages from hald process
[/LIST]

In my case, kernel sees my ipod, sets it as /dev/sdc and passes control to hal daemon which mounts it as /media/IPOD MINI.
No /etc/fstab edit should be necessary. What Ubuntu version are you using btw?

---

### Post by Swarms on 2007-04-24
> **mlind said:**
> When you plug-in your ipod, hal-daemon should make it available automatically. Your ipod should be mounted in /media directory somehere. My ipod is mounted as /media/IPOD MINI (I guess hal creates the mount point from the name of my ipod).

You can observe whats happening like this:
[LIST]
[*]watch /var/log/syslog using
```

tail -f /var/log/syslog

```
[*]Plugin your ipod and watch the messages from hald process
[/LIST]

In my case, kernel sees my ipod, sets it as /dev/sdc and passes control to hal daemon which mounts it as /media/IPOD MINI.
No /etc/fstab edit should be necessary. What Ubuntu version are you using btw?
> 
Ubuntu 7.04 Feisty Fawn User

When I try to sync all, it says: > Please specify the command to be called on the 'Tools' section of the preferences dialog.


I thought it was because I haven't submitted which command to run for syncing contacts, calendar and notes, but I tried searching and couldn't find anything.

Its a 2nd. gen, 6gb. Ipod.

---

### Post by mlind on 2007-04-24
> **Swarms said:**
> When I try to sync all, it says: 

I thought it was because I haven't submitted which command to run for syncing contacts, calendar and notes, but I tried searching and couldn't find anything.

Its a 2nd. gen, 6gb. Ipod.

Does gtkpod's reference document help here?
[http://www.gtkpod.org/README](http://www.gtkpod.org/README)

---

### Post by Immolatus on 2007-04-24
[QUOTE=mlind;2524989]When you plug-in your ipod, hal-daemon should make it available automatically. Your ipod should be mounted in /media directory somehere. My ipod is mounted as /media/IPOD MINI (I guess hal creates the mount point from the name of my ipod).

You can observe whats happening like this:
[LIST]
[*]watch /var/log/syslog using
```

tail -f /var/log/syslog

```
[*]Plugin your ipod and watch the messages from hald process
[/LIST]

In my case, kernel sees my ipod, sets it as /dev/sdc and passes control to hal daemon which mounts it as /media/IPOD MINI.
No /etc/fstab edit should be necessary. What Ubuntu version are you using btw?[/QUOTE

It shows up as in /media/myname ipod  and is mounted at "/dev/sdb2 on behalf of uid 1000"
I'm assuming this is all correct. The problem I've got is that gtkpod asks me if I wont it to create a directory structure for my pod, when I say go ahead it spits out and error:

Error initialising iPod: Problem creating iPod directory or file: '/media/ipod/iPod_Control'.
What do you think of this?

---

### Post by mlind on 2007-04-24
It looks normal yes. I think you should not use gtkpod to initialize your ipod. Does amaroK handle this? I initialized my ipod with iTunes long ago so I don't really know what applications support this, but I've heard some strong opinions about gtkpod.


Even though amaroK is a KDE application, it requires only very minimal set of KDE dependencies
```

sudo aptitude install amarok

```

To remove amarok
```

sudo aptitude purge amarok

```

---

### Post by Immolatus on 2007-04-24
> **mlind said:**
> It looks normal yes. I think you should not use gtkpod to initialize your ipod. Does amaroK handle this? I initialized my ipod with iTunes long ago so I don't really know what applications support this, but I've heard some strong opinions about gtkpod.


Even though amaroK is a KDE application, it requires only very minimal set of KDE dependencies
```

sudo aptitude install amarok

```

To remove amarok
```

sudo aptitude purge amarok

```

No my ipod is initialized from a previous wintrash installation, so it has music on it and is formatted vfat.
I managed once to put a song on it when I ran fedora but could never find the song in the ipods own menus to play it just from the pod. I could however play it off the ipod. I assume this is a labelling issue. And yes I accomplished this using Amarok.
But I would like to be able to use gtkpod as it seems to be the most liked by the community and probably for a reason unbeknownst to me as of yet.
Do you think there is a setting in gtkpod that I have overlooked that will allow free exchange between my ipod and gtkpod?
Either way I'll install Amarok and give it a go.

---

### Post by mlind on 2007-04-24
> **Immolatus said:**
> No my ipod is initialized from a previous wintrash installation, so it has music on it and is formatted vfat.
I managed once to put a song on it when I ran fedora but could never find the song in the ipods own menus to play it just from the pod. I could however play it off the ipod. I assume this is a labelling issue. And yes I accomplished this using Amarok.
But I would like to be able to use gtkpod as it seems to be the most liked by the community and probably for a reason unbeknownst to me as of yet.
Do you think there is a setting in gtkpod that I have overlooked that will allow free exchange between my ipod and gtkpod?
Either way I'll install Amarok and give it a go.

I don't use gtkpod much myself so I can't help you there. The song you're looking for is probably orphaned (not in ipod's itunesDB, but exists in the device). Some programs rely on the itunesdb, some read the information from physical files instead and some can do both.

gtkpod (and I guess amarok too) can search for orphaned songs and remove those. I had similar orphaned songs issue, when rhythmbox contained (maybe still has) a bug where it didn't properly write the info in to ipod's itunesDB file.

I know these things are matter of taste, but I've found amaroK the most reliable so far to play with ipod. It's the only KDE app I happily install along with my gnome stuff.

---

