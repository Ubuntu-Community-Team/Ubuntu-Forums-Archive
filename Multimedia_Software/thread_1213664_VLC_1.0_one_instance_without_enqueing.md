---
title: "VLC 1.0 one instance without enqueing"
date: 2009-07-15
forum: Multimedia Software
---

### Post by Krister Hallergard on 2009-07-15
I would like my one instance of VLC to switch straight away to playing a new file when I click on it, rather than await for me to exit the other one already playing. That is how I understod ticking "Allow only one instance" and unticking "Enque files when in one instance mode". I thought this would function with the final version of 1.0.

I am very pleased with the Windows version - which functions in this respect, but not Ubuntu: vlc-1.0.0-1ubuntu1 (karmic) (nor the two available launchpad versions).  What can be done?

---

### Post by mc4man on 2009-07-15
I actually found just the opposite, the button won't stay checked and vlc immediately starts the file clicked on. (tried on 0.9.9, 1.0, 1.1, hardy thru jaunty

Are you using karmic which has some newer qt4 , dbus, qt4-dbus libs?

So in lieu of some add. setting or squaring itself away you could try what I use as a workaround except use the opposite vlc launch command for your custom definition  

Described here
[http://ubuntuforums.org/showthread.php?p=7584086#post7584086](http://ubuntuforums.org/showthread.php?p=7584086#post7584086)

So you'd use this instead ( if so, do give a new name to distinquish
```
vlc --no-playlist-enqueue
```

---

### Post by Krister Hallergard on 2009-07-15
Thanks, what I actually want to do is to use the remote control with lirc sending irexec commands like Button 1 "config = vlc /path/playlist1" and Button 2 "config = vlc /path/playlist2".  And I would like to be able to switch immediately from the current playlist1 to the new playlist2.

This works with Windows and also with the Mandriva version of Goldeneye, but not with the Ubuntu, SuSe and Fedora versions of Goldeneye.

Sorry if I was using the word "click" incorrectly.  When clicking with the mouse on a clip or a link, vlc will change to the new one immediately.

Will try Button 2 "config = vlc --no-playlist-enqueue /path/playlist2" and let you know

---

### Post by mc4man on 2009-07-15
Just read your post over on vlc than explained your use of the term "click"

That seems to explain why you 'seemed' to have the "enqueue files when in one instance mode" working when it doesn't (when the term click means d.left click file association or a r. click 'open with'

Have no idea how the above mentioned would work/effect in your use (multiple rc buttons

edit: Off topic
 am curious about if in karmic, if you check the enqueue box, save, close vlc and then reopen, is the box still checked?

---

### Post by Krister Hallergard on 2009-07-16
First, I am using Jaunty - only enabled the Karmic repositories to be able to install VLC Goldeneye.  There were some dependencies that probably were installed at the same time.

Tried the command "config = vlc --no-playlist-enqueue /path/playlist2" but did not notice any effect.

As to checking the enqueue box:  The box is not checked anymore after restart.

---

