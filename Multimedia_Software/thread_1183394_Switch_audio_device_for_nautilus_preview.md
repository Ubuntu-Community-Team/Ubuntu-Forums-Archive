---
title: "Switch audio device for nautilus preview?"
date: 2009-06-10
forum: Multimedia Software
---

### Post by gardener on 2009-06-10
I am trying to change the audio device for audio preview in nautilus. The usual way I do this, by selecting the application in pulse audio volume control and manually assigning it to another device, doesn't work because as soon as I take my mouse off the file icon the application disappears.

There must be a simple answer but I couldn't find it searching.

---

### Post by kruykaze on 2010-07-27
Same problem here :/

---

### Post by mc4man on 2010-07-27
Edit : I think I may have mis understood what audio device was meaning - though a script replacing the default preview may help in that regard or be the only way, if possible

Fairly simple, though to what end I'm not sure, with a little help totem in karmic and lucid  can be pretty capable as far as audio.

totem-audio-preview is a binary in /usr/bin and can be left alone.

All you need to do is copy a binary or executable script to /usr/local/bin and name it totem-audio-preview and it will be used.

Whether and how it  it works is up to the player or script.

Simple Ex.

Am on maverick atm and have a pretty capable vlc - the cvlc script would work well for this. (no player will pop up

Because I built vlc,  cvlc is in /usr/local/bin - if I was using a packaged version it would be in /usr/bin and one would remove the blue

So...
```
sudo cp  /usr/[COLOR="Blue"]local/[/COLOR]bin/cvlc /usr/local/bin/totem-audio-preview
```

That's it - /usr/local takes precedence over /usr so cvlc is now the preview player - see screen (maybe - on a large screen monitor), mouse on an audio file - htop shows cvlc running

Other players binaries or scripts may or may not work - if not just delete the file from /usr/local/bin and the normal totem previewer  will return

Edit 2:
Now that I think about it  - if you can find or create a script that does whatever you wish to happen while hovering over an audio file then you could also just keep it localised in  $HOME if you wish

By default ~/bin comes first (at least here), so an option would just stick the script named totem-audio-preview in ~/bin

---

