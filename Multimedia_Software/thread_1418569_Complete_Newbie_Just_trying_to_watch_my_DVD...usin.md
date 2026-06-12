---
title: "Complete Newbie Just trying to watch my DVD...using VLC"
date: 2010-02-28
forum: Multimedia Software
---

### Post by rerednaw on 2010-02-28
Okay I managed to install VLC.  I pop in a DVD...it shows up in the file browser.  I try to get VLC to read it:

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]
 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///media/cdrom0'. Check the log for details.[/COLOR]

[COLOR=#000000]I just installed Ubuntu 9.10 on my x86 (AMD Phenom with ATi HD 4850). 
[/COLOR]
[COLOR=#000000]I cannot even figure out how to get a command line...is that all done from the file browser?[/COLOR]

[COLOR=#000000]Do I need to re-install the restricted bundle? [/COLOR]

[COLOR=#000000]Help!
[/COLOR]

---

### Post by mc4man on 2010-02-28
> cannot even figure out how to get a command line

Applications -> Accessories -> Terminal

Open that up, copy and paste this in , press enter and after try vlc again
(if libdvdcss2 isn't installed from below command then post what release of ubuntu you're using


```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by rerednaw on 2010-02-28
Okay the DVD now plays...only no audio :p

Is there a switch or toggle I need to use to get it to play via the external speakers?

There doesn't seem to be an option to change external audio.  

I'll keep at it, thanks for the help so far!

Okay found sound preferences...there's one for internal audio and one for hdmi.  I am using the on-board 5.1 surround sound.  But I still don't hear any audio...

OKAY found it yay!  Out of 50 different audio options I got lucky and found the right one :p

Bugger Ubuntu says it is using 5.1...but it's only using 2.1  grrrr.

---

