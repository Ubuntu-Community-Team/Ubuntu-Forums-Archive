---
title: "Totem player cannot playlist"
date: 2015-08-01
forum: Multimedia Software
---

### Post by baumtopf3 on 2015-08-01
Hello Ubuntu users,

I installed Ubuntu 15.04. I would like to use Totem player for tv streams. To select channels I would like to use playlist menu inside Totem player. In previous versions there were a playlist. But now, I cannot find a playlist inside Totem player. What can I do to find the playlist menu inside Totem player? Is there a shortcut?

Regards, Jürgen

---

### Post by howefield on 2015-08-01
This thread might be of interest.

[http://ubuntuforums.org/showthread.php?t=2278673](http://ubuntuforums.org/showthread.php?t=2278673)

---

### Post by baumtopf3 on 2015-08-02
In the other Thread I asked whether following code re-establish the playlist menu inside totem player, but I get no answer. 
```

gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'

```
Can someone give me an answer?

---

### Post by mc4man on 2015-08-02
> **baumtopf3 said:**
> In the other Thread I asked whether following code re-establish the playlist menu inside totem player, but I get no answer. 
```

gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'

```
Can someone give me an answer?
It could return the **preferences** menu if missing. There is no 'playlist' like before. 
If you add videos then you'll find them in the Videos tab, they can be checkmarked to create a playlist of sorts.
Only 6 of the grilo plugins work (channels) , the majority are non-functional.

---

### Post by baumtopf3 on 2015-08-02
This code I copied in the terminal and pressed enter, but nothing happens, what did I wrong?
```

gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'

```

---

### Post by mc4man on 2015-08-02
> **baumtopf3 said:**
> This code I copied in the terminal and pressed enter, but nothing happens, what did I wrong?
```

gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'

```
That was only for people using gnome-flashback if there was no preferences menu available. There isn't much in that menu anyway, screen

---

### Post by baumtopf3 on 2015-08-02
I repeat. In the preferences there are no options to get back a playlist. The only way to get an overview about my tv streams is the tab "videos". Is that right? :sad:

---

### Post by mc4man on 2015-08-02
> **baumtopf3 said:**
> I repeat. In the preferences there are no options to get back a playlist. The only way to get an overview about my tv streams is the tab "videos". Is that right? :sad:
No playlist like before as mentioned numerous times...

---

### Post by baumtopf3 on 2015-08-02
Is it possible to get an older version of totem player, to get back the playlist

---

### Post by mc4man on 2015-08-02
> **baumtopf3 said:**
> Is it possible to get an older version of totem player, to get back the playlist
To some degree yes, how well it works overall  don't know (don't use totem really & don't use 15.04 though I have an install.

So if you removed the 5 packages in scr. one & replaced with the ones in scr. 1 from utopic then you'd get the 3.10 totem that will install & at least open - scr. 2 (note screen shows the  5 needed for an amd64 install

Note: these urls may 'disappear' shortly, not sure as 14.10 is either eol or will be soon.. - 
[http://packages.ubuntu.com/utopic/gnome/totem](http://packages.ubuntu.com/utopic/gnome/totem)
[http://packages.ubuntu.com/utopic/libtotem0](http://packages.ubuntu.com/utopic/libtotem0)
[http://packages.ubuntu.com/utopic/totem-plugins](http://packages.ubuntu.com/utopic/totem-plugins)
[http://packages.ubuntu.com/utopic/gir1.2-totem-1.0](http://packages.ubuntu.com/utopic/gir1.2-totem-1.0)
[http://packages.ubuntu.com/utopic/totem-common](http://packages.ubuntu.com/utopic/totem-common)

You'd download all 5 for your arch (totem-common is for all arch's), place in a folder, cd to folder & 
```
sudo dpkg -i *.deb
```
if dpkg completes without error then try out, if it errors then address the error...

edit: if you install 15.04's grilo-plugins-0.2-extra package then at least some grilo plugins work - scr.3

---

### Post by cno2 on 2015-11-26
I think I'm suffering from the same problem?
I have many playlists. Files with an .m3u extension that contain a line for each number. In previous versions, those were opened and played by Totem. Now that results in an error message: "The given film cannot be found" (translated from Dutch).
So I have to open file(s) individually or as group.
Filed bug [https://bugzilla.gnome.org/show_bug.cgi?id=758710](https://bugzilla.gnome.org/show_bug.cgi?id=758710).

---

### Post by mc4man on 2015-11-26
> **cno2 said:**
> I think I'm suffering from the same problem?
I have many playlists. Files with an .m3u extension that contain a line for each number. In previous versions, those were opened and played by Totem. Now that results in an error message: "The given film cannot be found" (translated from Dutch).
So I have to open file(s) individually or as group.
Filed bug [https://bugzilla.gnome.org/show_bug.cgi?id=758710](https://bugzilla.gnome.org/show_bug.cgi?id=758710).
Good job filing a bug, fix works here.  So filed on launchpad for 16.04
[https://bugs.launchpad.net/ubuntu/+source/totem-pl-parser/+bug/1520379](https://bugs.launchpad.net/ubuntu/+source/totem-pl-parser/+bug/1520379)

---

