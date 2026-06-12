---
title: "Streamtuner2 (2.2.0) on Ubuntu 18.04"
date: 2019-11-13
forum: Multimedia Software
---

### Post by Harix on 2019-11-13
I cannot get the the Record function working. Terminal is not opening.
On 16.04 Streamtuner2 version 2.1.9 works fine.

---

### Post by #&amp;thj^% on 2019-11-13
**"xterm" **needs to be present (Installed), if that is already installed on your system then show the the output of:
```
streamtuner2 -D
```
Works fine in 20.04 alpha here.

---

### Post by Harix on 2019-11-13
Installed xterm. Now the terminal appears 3 seconds if I push the Record button...

```
harix@harix-750:~$ streamtuner2 -D
[PROC] ConfigDict() initialized
[STAT] <GtkProxyModule <IntrospectionModule 'Gtk' from '/usr/lib/x86_64-linux-gnu/girepository-1.0/Gtk-3.0.typelib'>>
[STAT] <GObjectProxyModule <IntrospectionModule 'GObject' from '/usr/lib/x86_64-linux-gnu/girepository-1.0/GObject-2.0.typelib'>>
[PROC] load bookmarks.json
[PROC] bookmarks.current:=favourite &#8592; from ['current', 'gui', 'gui']
[UI] bookmarks.display_categories(), uikit.tree(#1), expand_all(#<20), select_current(=favourite)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.bookmarks.bookmarks object at 0x7f2079cf5a58>>
[UI] reselect .current category in treelist: favourite
[STAT] disabled plugin: dirble
[STAT] disabled plugin: exportcat
[STAT] disabled plugin: filter_bitrate
[STAT] disabled plugin: filtermusic
[STAT] disabled plugin: global_key
[STAT] disabled plugin: history
[PROC] internet_radio.current:=Salsa &#8592; from ['current', 'gui', 'gui']
[UI] internet_radio.display_categories(), uikit.tree(#83), expand_all(#<20), select_current(=Salsa)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.internet_radio.internet_radio object at 0x7f206c08b668>>
[UI] reselect .current category in treelist: Salsa
[PROC] jamendo.current:=radios &#8592; from ['current', 'gui', 'gui']
[UI] jamendo.display_categories(), uikit.tree(#7), expand_all(#<20), select_current(=radios)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.jamendo.jamendo object at 0x7f20613639e8>>
[UI] reselect .current category in treelist: radios
[UI] bookmarks.display_categories(), uikit.tree(#2), expand_all(#<20), select_current(=favourite)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.bookmarks.bookmarks object at 0x7f2079cf5a58>>
[UI] reselect .current category in treelist: favourite
[STAT] disabled plugin: modarchive
[PROC] myoggradio.current:=common &#8592; from ['current', 'gui', 'gui']
[UI] myoggradio.display_categories(), uikit.tree(#2), expand_all(#<20), select_current(=common)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.myoggradio.myoggradio object at 0x7f206099e240>>
[UI] reselect .current category in treelist: common
[STAT] disabled plugin: pluginmanager2
[STAT] disabled plugin: radiobrowser
[STAT] disabled plugin: radionomy
[STAT] disabled plugin: radiotray
[STAT] disabled plugin: reddit
[PROC] shoutcast.current:=None &#8592; from ['current', 'gui', 'gui']
[UI] shoutcast.display_categories(), uikit.tree(#0), expand_all(#<20), select_current(=None)
[STAT] disabled plugin: somafm
[STAT] disabled plugin: specbuttons
[PROC] surfmusik.current:=America &#8592; from ['current', 'gui', 'gui']
[UI] surfmusik.display_categories(), uikit.tree(#22), expand_all(#<20), select_current(=America)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.surfmusik.surfmusik object at 0x7f206005cc50>>
[UI] reselect .current category in treelist: America
[STAT] disabled plugin: timer
[PROC] tunein.current:=Decades &#8592; from ['current', 'gui', 'gui']
[UI] tunein.display_categories(), uikit.tree(#42), expand_all(#<20), select_current(=Decades)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.tunein.tunein object at 0x7f206094fba8>>
[UI] reselect .current category in treelist: Decades
[STAT] disabled plugin: ubuntuusers
[STAT] disabled plugin: ui_cht
[STAT] disabled plugin: useragentswitcher
[PROC] xiph.current:=Oldies &#8592; from ['current', 'gui', 'gui']
[UI] xiph.display_categories(), uikit.tree(#157), expand_all(#<20), select_current(=Oldies)
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.xiph.xiph object at 0x7f2053c2c160>>
[UI] reselect .current category in treelist: Oldies
[PROC] youtube.current:=None &#8592; from ['current', 'gui', 'gui']
[UI] youtube.display_categories(), uikit.tree(#6), expand_all(#<20), select_current(=None)
[PROC] xiph &#8594; first_show() , current= Oldies , categories= 157
[UI] xiph &#8594; first_show(); station list &#8594; load( Oldies )
[PROC] xiph.current:=Oldies &#8592; from ['current', 'load', 'first_show']
[UI] load() &#8594; uikit.columns(xiph.streams[Oldies]) ['load', 'first_show', '__init__', 'main']
[UIKIT_EXEC] <bound method GenericChannel.select_current of <channels.xiph.xiph object at 0x7f2053c2c160>>
[UI] reselect .current category in treelist: Oldies
[UIKIT_EXEC] <bound method GenericChannel.columns of <channels.xiph.xiph object at 0x7f2053c2c160>>


```

---

### Post by #&amp;thj^% on 2019-11-13
Sorry I should have been a bit clearer, when you hit record issue that command again.
If by chance we are not able to solve this for you, there is always "streamripper"
```
sudo apt install streamripper
```

---

### Post by Harix on 2019-11-14
As I thought that I mixed up some settings in Streamtuner2, I removed and re-installed it.
Now Streamtuner doesn't start at all.
On the terminal I get:

```
harix@harix-750:~$ streamtuner2
Traceback (most recent call last):
  File "/usr/bin/streamtuner2", line 12, in <module>
    import st2
  File "/usr/share/streamtuner2/st2.py", line 55, in <module>
    from config import *
  File "/usr/share/streamtuner2/config.py", line 374, in <module>
    conf = ConfigDict()
  File "/usr/share/streamtuner2/config.py", line 85, in __init__
    self.defaults()
  File "/usr/share/streamtuner2/config.py", line 116, in defaults
    "audio/mpeg": self.find_player(),
  File "/usr/share/streamtuner2/config.py", line 179, in find_player
    if find_executable(bin.split()[0]):
  File "/usr/share/streamtuner2/compat2and3.py", line 72, in find_executable
    exists = [os.path.exists(dir+"/"+bin) for dir in os.environ.get("PATH").split(":")+["/"]]
NameError: name 'os' is not defined
harix@harix-750:~$ 

```

---

### Post by Harix on 2019-11-14
Removed Streamripper2 again and installed .deb file from

[URL="https://sourceforge.net/projects/streamtuner2/"]https://sourceforge.net/projects/streamtuner2/
[/URL]
Now it starts and plays stations!
Recording did not work but now it does after changing:

Edit - Properties - RECORDING application - audio/*   
into:  gnome-terminal -e "streamripper %srv"

Do Enter and Save!



[URL="http://sourceforge.net/projects/streamtuner2/"]





[/URL]

---

### Post by #&amp;thj^% on 2019-11-14
Yep "streamripper %srv", and Nicely Done! :)
It's odd to me you had to go a version down though.
```
apt policy streamtuner2
streamtuner2:
  Installed: 2.2.1+dfsg-2
  Candidate: 2.2.1+dfsg-2
  Version table:
 *** 2.2.1+dfsg-2 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal/universe i386 Packages
        100 /var/lib/dpkg/status

```
And Depends:
```
streamtuner2
  Depends: <python3:any>
    python3:i386
    python3
  Depends: python3
  Depends: python3-lxml
  Depends: python3-pil
  Depends: python3-pyquery
  Depends: python3-gi
  Depends: python3-requests
  Depends: python3-distutils
  Suggests: audacious
  Suggests: vlc
  Suggests: totem

```
Tips for anyone interested:
Each application may optionally use placeholders such as "%pls" for Shoucast playlists, and "%m3u" for older players, and "%xspf" for newer, and "%srv" for direct streaming URLs.
You may want to mark this as "SOLVED" to help others with this issue.
Regards

---

### Post by Harix on 2019-11-15
Is it useful to add several placeholders %pls %m3u %xspf? In both audio player and recording?

---

