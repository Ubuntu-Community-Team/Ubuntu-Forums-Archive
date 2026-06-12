---
title: "[SOLVED] Rhythmbox - wrong save path"
date: 2008-08-10
forum: Multimedia Software
---

### Post by Bucky Ball on 2008-08-10
Not urgent but annoying and unexplained ... 

After I moved my Music folder, Rhythmbox Music Player is working fine, except when I go to import anything. It is checking the old path to my Music folder, naturally throwing an error, even though I have been to preferences and changed the path to the new, correct one. 

Tried uninstalling and reinstalling Rhythmbox but no different. When I click ok and close the error window, it then lets me import what I want from where I want. 

Any ideas ? A terminal tweak or am I right off the money with a wild guess?

Thanks in advance ... :)

---

### Post by wdaniels on 2008-08-10
Run gconf-editor and take a look at the "add_dir" setting under /apps/rhythmbox/state (if it's set to your old music directory you can just change/delete it there).

Also, note that you can change the default location for music in the file ~/.config/user-dirs.dirs if you want.

---

### Post by Bucky Ball on 2008-08-10
Thanks for that wdaniels. I'm looking at /apps/rhythmbox/state/add_dir, and it in fact has no value. Do I edit key and add the desired path, in my case;

 /media/bigboy/MUSIC

?

* Update: Indeed you do. Just made the value the correct path and worked a treat. Thanks again. BBall discovers gconf-editor, look out! :)

---

### Post by wdaniels on 2008-08-10
Yes, you might as well (it won't hurt), though I wonder where the old path is coming from in that case so I'm not sure that will fix your problem...let's see if add_dir makes a difference...it may be that when it's empty the path gets taken from the default...

---

### Post by Bucky Ball on 2008-08-10
Solved, check my last post wdaniels :)

---

### Post by wdaniels on 2008-08-10
> **Bucky Ball said:**
> BBall discovers gconf-editor, look out! :)

Mostly it just contains settings that you can access in the relevant preferences dialogs, but it can be handy for fixing bad "state" settings such as window sizes/positions, plus there's the odd hidden setting to be found in there.

However, I think I can assume now that the "old" path to the music location was simply the original default "Music" under the home directory. So the problem was that it was defaulting to this location, which as I mentioned before you can correct by editing the file ~/.config/user-dirs.dirs and you should do that to avoid similar errors in other music programs in the future:

```
sudo pico ~/.config/user-dirs.dirs
```

(fix the XDG_MUSIC_DIR variable to point to your new music folder, or just set it to "$HOME/")

This should also stop Gnome from recreating the ~/Music folder each time you log in (perhaps you noticed that happening?).

---

### Post by Bucky Ball on 2008-08-10
[quote=wdaniels]I think I can assume now that the "old" path to the music location was simply the original default "Music" under the home directory.[/quote]

Well, yes, but not sure what to put there instead (do I need to put everything after home? Add 'skulker' first?

```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

Is how things currently look. This path;

```
XDG_MUSIC_DIR="$HOME/Music"
```

Doesn't seem to relate to this one which was the original problem ...

```
/media/skulker/bigboy/Music
```Which, from memory, was the error I was getting.

The command from you last post;

sudo pico ~/.config/user-dirs.dirs
... gives me a great utility, when I learn to use it that is.

Do I change;

```
XDG_MUSIC_DIR="$HOME/Music"
```to

```
XDG_MUSIC_DIR="$HOME/media/bigboy/MUSIC"
```... which is where I actually want the music files to go?

Thanks for yet another tip!

---

### Post by wdaniels on 2008-08-11
> **Bucky Ball said:**
> Do I change;

```
XDG_MUSIC_DIR="$HOME/Music"
```to

```
XDG_MUSIC_DIR="$HOME/media/bigboy/MUSIC"
```... which is where I actually want the music files to go?

Presumably /media is not mounted under your home directory (usually it is directly under the root of the filesystem) so rather than "$HOME/media/bigboy/MUSIC" you should change it to "/media/bigboy/MUSIC/". However, if /media/bigboy/MUSIC is not always mounted then perhaps it would be best to leave this set to the home folder "$HOME/" to avoid errors.

So we don't seem to have gotten to the bottom of exactly where Rhythmbox was picking up the old music path from on import, but without reading through the code I'm out of ideas. So long as it's working now, let's leave it at that :D

---

### Post by Bucky Ball on 2008-08-11
[QUOTE=wdaniels]So long as it's working now, let's leave it at that[/QUOTE]

My sentiments exactly. I'll keep tweaking (as usual) and thanks for your help. :)

---

