---
title: "PLaylist option in medi player missing 15.04"
date: 2015-05-18
forum: Multimedia Software
---

### Post by welefort on 2015-05-18
Just upgraded to 15.04.  In the default media player is there no playlist option?   It also appears there is no menu bar also.  Im unable to adjust any settings(sound, video, playlist..)   Im using Gnome-flashback and not unity.

[IMG]http://i.imgur.com/SYb9f10.png[/IMG]

---

### Post by SeijiSensei on 2015-05-18
Install smplayer, and all these issues will disappear.
```
sudo apt-get install smplayer
```

---

### Post by mc4man on 2015-05-18
Totem 3.14 in Ubuntu (any session) has become just a video player & maybe a grilo plugin or 2 will work (channels). Otherwise complete garbage & only useful for thumbnails & a/v info in nautilus > properties on media files

---

### Post by monkeybrain20122 on 2015-05-18
> **SeijiSensei said:**
> Install smplayer, and all these issues will disappear.
```
sudo apt-get install smplayer
```

Better add the rvm ppa first for up to date version, in particular the Smplayer youtube viewer from repo won't work

```
sudo add-apt-repository ppa:rvm/ppa
sudo apt-get update
sudo apt-get install smplayer
```

---

### Post by SeijiSensei on 2015-05-18
I've used smplayer for years now and never used the YouTube viewer.  I just use my browser. 

Generally I don't like to encourage users to use PPAs unless they have a really powerful reason to do so.

---

### Post by monkeybrain20122 on 2015-05-18
Does Smplayer from the repo work with mpv?

---

### Post by SeijiSensei on 2015-05-18
> **monkeybrain20122 said:**
> Does Smplayer from the repo work with mpv?

I think the repo version doesn't support mpv, but I don't think that matters much given the issues the OP has asked about.  SMPlayer with mplayer works fine for playlists and similar basic functions.

---

### Post by Vladlenin5000 on 2015-05-18
> **SeijiSensei said:**
> I think the repo version doesn't support mpv, but I don't think that matters much given the issues the OP has asked about.  SMPlayer with mplayer works fine for playlists and similar basic functions.
+1

> **SeijiSensei said:**
> I've used smplayer for years now and never used the YouTube viewer.  I just use my browser. 

Generally I don't like to encourage users to use PPAs unless they have a really powerful reason to do so.
+1 +1

Slightly off-topic: SMPlayer needs a facelift, perhaps botox.

---

### Post by mc4man on 2015-05-19
> **welefort said:**
>  It also appears there is no menu bar also.  Im unable to adjust any settings(sound, video, playlist..)   Im using Gnome-flashback and not unity.

to get a preference menu in totem run this in a terminal, will also give you menus in gedit

```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'
```

With grilo plugins installed some other channels will appear, one is "MyMedia" though have not yet found any way to populate it. It may be possible to improve totem in 15.04 but myself have little interest, was able to somewhat improve it in 14.04 though that is 3.10 version

Overall the + button in Videos section produces what passes for a 'playlist'

---

### Post by welefort on 2015-05-19
Thanks!  This worked out.

---

### Post by baumtopf3 on 2015-08-02
I have the same issue, I would like to get back the playlist inside the totem player. To get back the playlist inside totem player, should I copy following code in the terminal?
```

gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'

```

I tried, but nothing happens. I am a beginner in using Ubuntu.

---

