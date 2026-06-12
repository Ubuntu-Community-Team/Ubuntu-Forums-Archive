---
title: "Help with online video/flash/shockwave in mozilla ff3.5"
date: 2009-11-10
forum: Multimedia Software
---

### Post by rinky on 2009-11-10
I just wanted to add this, because I couldn't find any help on this issue that I could understand, so I wanted to add my personal "resolution tale" for the benefit of all...

On my edubuntu (just upgraded from 9.04 to 9.10) I’ve never had any trouble with online audio/video (e.g.: iplayer); but on another 9.04 installation, I get no joy!
 The edubuntu one says it’s got Shockwave Flash 10 r32 plugin on it; this one says it’s got 0.9 r999 – what’s going on?!
I’ve been scouring all the online help, to no avail!

[...1 hour-ish later!]

I found the solution!
 After first doing this:
 ```
sudo apt-get remove  adobe-flashplugin flashplugin-nonfree flashplugin-installer
```
 (in a terminal window)

I saw that I had no flash on the system (and was confusing Shockwave with Flash perhaps?); so I installed it:

```
sudo apt-get install  adobe-flashplugin flashplugin-nonfree flashplugin-installer
```

Seeing no difference, I went to Synaptic Manager, and searched for swf, and found "swfdec mozilla" ticked as installed; so I ticked to remove it completely.

After doing so, I restarted FF3.5 and checked the addons, and saw that the previous listing as Shockwave v0.9 r999 had changed to v10.0 r32 (looking not only correct, but a lot less like an error version display).

Went to iplayer... clicked on an Attenborough documentary - sorted! 


Perhaps someone can put this in some kind of FAQ, because I just couldn't find anything helpful on the pages, and I'm supposed to be an engineer - so what hope has anyone who isn't got (stretching the grammar there a bit!).

---

