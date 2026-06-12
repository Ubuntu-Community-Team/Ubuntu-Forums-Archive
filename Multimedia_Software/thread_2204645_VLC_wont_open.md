---
title: "VLC wont open"
date: 2014-02-09
forum: Multimedia Software
---

### Post by typos1 on 2014-02-09
VLC wont open, nothing happens at all. I ve uninstalled it and re-installed, still have the same problem, anyone got know what could be wrong ?

---

### Post by ajgreeny on 2014-02-09
Try to open it in terminal with command **vlc** and report back any errors that appear.

---

### Post by fdrake on 2014-02-09
+1 ajgreeny

also tell us what is your system too.

---

### Post by typos1 on 2014-02-09
:~$ vlc
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x1cfaa38] fbosd interface error: cannot open /dev/fb0 (No such file or directory)
[0x1cfaa38] main interface error: no suitable interface module
[0x1ccb108] main libvlc error: interface "default" initialization failed

How you mean "my system" ? - Hardware is on my signature, I m using 13.10, 64 bit

---

### Post by fdrake on 2014-02-09
tools -> preferences -> check or uncheck "integrate video in interface"

see if that make a difference

---

### Post by typos1 on 2014-02-09
Whereabouts is "tools" ?

Cant find it in ubuntu system settings and VLC wont open so cant do it via VLC's gui.

---

### Post by ajgreeny on 2014-02-09
Try command ```
vlc -I ncurses
``` to see if it starts in commandline interface.

If it does we need to look at other installed packages than the single vlc one. It might be worth trying purging all *vlc* packages (7 of them on my Xubuntu 12.04) and reinstalling all of those in case one of them is corrupted in some way.

Search for all *vlc* packages with synaptic for easiest way, in my opinion.

---

### Post by typos1 on 2014-02-09
It does, but I cant find anything marked as "tools" or any way to get into preferences

---

### Post by andrew.46 on 2014-02-09
You can try allowing the creation of a new vlc config file by running:

```

mv $HOME/.config/vlc/vlcrc $HOME/.config/vlc/vlcrc_bak

```

and then starting vlc...

---

### Post by fdrake on 2014-02-09
hold a second ! this may not be relate to vlc, only. how are totem and mplayer behaving ? any problem there?

---

### Post by typos1 on 2014-02-09
Well, I use smplayer and umplayer and theyre a bit crap with some file types - they play them and then they dont, I think thats down to being based on crappy mplayer, but could be wrong. 

Cant remember what totem does - is it play flash videos in the browser ?

Any how, just had a problem with totem video thumbnailer (kept taking up up to 60% of my cpu usage), which I have had before, but not for a long time, maybe something to do with stating VLC in the commnad line ?

Just posted that script in a terminal as per andrew.46's suggestion and all is fine - now VLC works !!

Although on some mp4 files the title is "avidemux - video title - video codec", which is strange as I m using VLC to play the file, I do have avidemux on my system.

---

### Post by andrew.46 on 2014-02-09
> **typos1 said:**
> Just posted that script in a terminal as per andrew.46's suggestion and all is fine - now VLC works !!

Great news :). Sometimes there is a snarl-up in the vlc configuration file and vlc will not start at all, it is a great pity that vlc does not keep a backup and thus could volunteer to restore the last known working configuration. Fortunately if the config file is moved or deleted vlc generates a clean copy.

---

### Post by typos1 on 2014-02-09
Well, thanks for all your helpp getting it working !

Is there some relationship between avidemux and VLC ?

---

### Post by andrew.46 on 2014-02-09
> **typos1 said:**
> Is there some relationship between avidemux and VLC ?

Not sure what that is all about, hopefully somebody cleverer than me can work that one out. BTW there is a neat cvlv command that resets the config from the cvlc commandline which escapes me at the moment. This would be neater than the small command I have suggested...

**Edit: **Easy enough to find:

```

andrew@ilium~$ cvlc --help | grep -A 1 'reset'
VLC media player 2.1.3 Rincewind (revision 2.1.3-0-ge6a71cc)
     **[COLOR="#FF0000"] --reset-config[/COLOR]**, --no-reset-config
                                 reset the current config to the default values (default disabled)
     **[COLOR="#FF0000"] --reset-plugins-cache[/COLOR]**, --no-reset-plugins-cache
                                 resets the current plugins cache (default disabled)
      --version, --no-version    print version information (default disabled)


```

---

