---
title: "How do I play a normal DVD bought at a store?"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by michaelfougnie on 2008-03-11
What do I need to install or do to get it to play an encrypted DVD?

---

### Post by crjackson on 2008-03-11
Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by uberlube on 2008-03-11
Or go into the Synaptic Package Manager and search 'restricted' and activate the ubuntu restricted extras. This will give you DVD playback as well as other good stuff.

---

### Post by sekinto on 2008-03-11
For me VLC has been the best program for DVD playback, Totem never shows the menus.

If I were you I would open up Synaptic Package Manager and download "vlc" and "libcss".

---

### Post by klick.here on 2008-03-11
I can play only one dvd from the store that i have tried and it works in any of the players but about five others that I have tried wouldn't even mount or show up as anything was in the dvd drive.  I have tried almost all of the suggestions i can find.  VLC didn't help me but it played the one that would work for me fine.  I'll keep trying and see what I can figure out.  I will see if the first suggestion works. or activating restricted extras.  I think I did that when i installed drivers for my nvidia card.

---

### Post by sekinto on 2008-03-11
EDIT: Sorry, gave you the wrong package names. Install these:
libdvdcss2
libdvddread3

---

### Post by ubuntu27 on 2008-03-11
[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") - How to instal Codecs (DVD Playack, etc)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by freebios on 2008-03-11
to play a dvd you have to enable css there are many ways to do this such as these links

[http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)

hope this helps. it worked for me (ubuntu 7.10)

---

### Post by klick.here on 2008-03-12
Finally... i have been playing with this for a week and uberlube's suggestion finally worked.  Synaptic package manager and search restricted drivers and install ubuntu restricted extras.  Beautiful :):popcorn: Thanks

---

