---
title: "[SOLVED] MPlayer and SMPlayer work, but mplayerplug-in and gnome-mplayer do not (stre"
date: 2008-06-11
forum: Multimedia Software
---

### Post by tanas on 2008-06-11
I am trying to open the audio stream in [http://tsf.sapo.pt/tsfdirecto.asx](http://tsf.sapo.pt/tsfdirecto.asx), that redirects to [http://srv2.lusomundo.net/tsfdirecto](http://srv2.lusomundo.net/tsfdirecto). Mplayer and SMPlayer work with no problem at all.
**But surprisingly mplayerplug-in (mozilla-mplayer) in firefox and gnome-mplayer do not**! (Actually vlc does not play it either, but it's not based on mplayer). They start buffering for one or two seconds and then stop.

I tried setting different buffer sizes, tried on a clean CaixaMagica (Mandriva based) installation, and the problem is persistent. I algo googled for an entire afternoon and nothing.

The typical log I get from the plug-in is

> 
Cache fill:  0.00% (0 bytes)
Cache fill:  0.00% (0 bytes)
Cache fill:  0.00% (0 bytes)
Cache fill:  1.99% (2567 bytes)   
 
in gtkgui_message
in gtkgui_progress
READ: Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
 

From gnome-mplayer is quite similar, just that it sometimes cuts the text like this:
> 
Cache fill:  0.00% (0 bytes)
Cache fill:  0.00% (0 b


Any clue?

---

### Post by tanas on 2008-06-16
Ok I solved it.. with "some" help.
In the gnome-player forum, Kevin DeKorte (the guy behind both gnome-mplayer and the mplayerplug-in) noticed that the problem was strangely related to an usually inoffensive option when calling mplayer.
-user-agent NSPlayer

So, if you have the same problem just use
-user-agent=none
in the respective .conf files.

---

### Post by lbharti on 2008-09-25
I really do not understand the conf files that you are talking about. If you mean mplayerplug-in.conf, it does not seem to have any option to define -user-agent.

---

### Post by tanas on 2008-09-25
Well, you just have to add it

BTW, it should be 

user-agent=none

instead of 

-user-agent=none

---

