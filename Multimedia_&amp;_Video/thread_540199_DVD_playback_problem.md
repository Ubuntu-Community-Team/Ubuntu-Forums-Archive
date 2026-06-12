---
title: "DVD playback problem"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by abhilash82 on 2007-09-01
I have installed all the plugins required to play dvd and other restricted formats but I am not able to play DVDs in any of the movie players. I have tried using MPlayer, gxine amd Totem movie player and all give me different errors. I have attached the screenshots of all these errors from different players.

---

### Post by abhilash82 on 2007-09-03
Has anyone faced a similar problem? Should I try with any other alternate player?

---

### Post by dexjul on 2007-09-11
I have same problem, but im using dapper drake. Any one can be help. Thank you.

---

### Post by abhilash82 on 2007-09-11
I still haven't got a solution for it but some of them have given workarounds [here]("http://ubuntuforums.org/showthread.php?t=542599").
:popcorn:

---

### Post by orange2k on 2007-09-11
To play rented DVD-s, I use VLC...
Usually, to skip the menus, I select "open disc" and then "DVD" (instead of "DVD menus")...
Thus I instantly start to watch the main feature movie, instead of watching commercials and different warnings...

---

### Post by dexjul on 2007-09-13
Thanks for the link. I'll try it.

How can I install VLC. Thanks in advance.

---

### Post by abhilash82 on 2007-09-14
**orange2k:** Thanks for your suggestion. My DVDs played well when I selected the DVD option instead of DVD Menu. But is it a bug or a compatibility issue?

**dexjul:** You can install VLC player by following the steps below.

_***Graphical way***_

Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).

_***Command line way***_

You need to check that you have a "universe" mirror in your /etc/apt/sources.list.

```

     sudo apt-get update
     sudo apt-get install vlc vlc-plugin-esd

```

In order to stream video via vlc, you also need to install the following packages. 

```

     sudo apt-get install avahi-daemon
     sudo apt-get install avahi-utils

```
  
A VLC plug-in for Firefox can also be installed 

```

    sudo apt-get install mozilla-plugin-vlc

```

To run VLC - Applications -> Sound and Video -> VLC Media Player

---

### Post by orange2k on 2007-09-14
> **abhilash82 said:**
> **orange2k:** Thanks for your suggestion. My DVDs played well when I selected the DVD option instead of DVD Menu. But is it a bug or a compatibility issue?



I have no idea...
But you really dont miss much by not having to view the menu. Usually you also have to watch some trailers, commercials and all kinds of copyright warnings when you do manage to view the menu...:)

---

