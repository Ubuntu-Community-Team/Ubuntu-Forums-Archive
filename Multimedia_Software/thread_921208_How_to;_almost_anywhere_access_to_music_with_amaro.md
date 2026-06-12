---
title: "How to; almost anywhere access to music with amarok"
date: 2008-09-16
forum: Multimedia Software
---

### Post by mc4man on 2008-09-16
In working on another thread this developed, I find it kind of handy. (see edit if tracks aren't ordered in folders

The idea is to gain access and playback to any or as many music folders from right clicking on the desktop or *any file browser* screen.
Works with amarok, audacious and vlc. (with correct launch comm.) Once it's setup very easy to add or delete 'entries' (scripts 
(audacious commands and alternate amarok commands #'s 8 & 9

[http://ubuntuforums.org/showthread.php?p=5287915#post5287915](http://ubuntuforums.org/showthread.php?p=5287915#post5287915)

First install this

```
sudo apt-get install nautilus-open-terminal
```

This provides a right click - 'open in terminal' on any directory (folder
Useful to run a command or get proper path to a folder without typing errors.

EX.
I have a mp3 music folder - 'derek and the dominos' somewhere. (red is path
Browse to the folder, r. click 'open in terminal'

```
doug@doug-desktop:[COLOR="Red"]~/mp3/Derek And The Dominos (1970) Layla And Other Assorted Love Songs[/COLOR]$
```

Copy the *path only* and then browse to home dir. -> .gnome2 -> nautilus-scripts.
Inside create a new text docu., name it whatever you want (I used layla - note; *must be lowercase*

Use this as a template, replace my path by pasting in copied path. **Leave quotes** for paths with spaces and or oddities
The file extension must match format of music files

```
#!/bin/bash
 cd [COLOR="Red"]~/mp3/[COLOR="Blue"]"[/COLOR]Derek And The Dominos (1970) Layla And Other Assorted Love Songs[COLOR="Blue"]"[/COLOR][/COLOR]
amarok --load --play *[COLOR="DarkOrchid"].mp3[/COLOR]
```

Save and backspace to .gnome2,  r/ click, 'open in terminal' and run (adjusting name
```
chmod +x [COLOR="Red"]layla[/COLOR]
```

Now a r.click will show a 'Scripts", mouse over and click name chosen. If Amarok is open the folder will load and begin playing, it it isn't Amarok will open, ect.

EX. of flac
```
#!/bin/bash
 cd ~/Music/"Quicksilver Messenger Service (1968) Quicksilver Messenger Service"
amarok --load --play *.flac
```

Ex. of vlc (running 0.9.3 from build folder, use just vlc -remove blue (only really suitable for vlc 0.9.x - which allows 'only one running instance'
```
#!/bin/bash
 cd "/media/test1/Music/Quicksilver Messenger Service (0) Happy Trails"
[COLOR="Blue"]/home/doug/vlc-0.9.3/[/COLOR]vlc *.m4a

```
You can also create subdirectories in nautilus-scripts if wanted, a right click 'collection' of sorts.
I made a couple based on sub dir. = artist, script = album or mix.
see screen, only took about 15 min to set up using a script template and chmoding in bulk

```
#!/bin/bash
 cd 
amarok --load --play *.[COLOR="Red"]flac[/COLOR]
```

[COLOR="Red"]Edit:[/COLOR] I use rubyripper which orders the tracks so when using any of the above they will load and play in the correct order. I've noticed some other rippers don't. If there is a .m3u in the album folder you can use that instead. (must be in the album folder
Or get grip to order track or hand edit (01-trackname, 02- , ect.) 

 

Ex. of using .m3u

```
#!/bin/bash
 cd ~/flac/"Quicksilver Messenger Service (1968) Quicksilver Messenger Service"
amarok --load --play *.m3u
```

'MU3 file format' for grip to place .m3u in album folder (with songs

```
[COLOR="Red"]~/ogg[/COLOR]/%A/%d/%d.m3u
```

adjust red to save folder name (in this case it's home /ogg

 'Encode file format' to get grip to order tracks
```

[COLOR="Red"]~/ogg[/COLOR]/%A/%d/%t- %n.%x
```

'Encode file format' to get grip to order tracks (**for m4a only** - above will turn them into mimetype - video
```

[COLOR="Red"]~/ogg[/COLOR]/%A/%d/%t%n.%x
```


Orig. grip for comparison
```
~/ogg/%A/%d/%n.%x 
```

---

