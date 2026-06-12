---
title: "rhythmbox not playing when double click a music file"
date: 2008-11-13
forum: Multimedia Software
---

### Post by zero777zero on 2008-11-13
when i double click on a flac or mp3, it just adds it to the current playlist, but does not play it unless i click 'play'. i listen to a lot of music and find this really annoying, i get the same issue in amarok too, but i don't see any option to change this.

8.10

---

### Post by mc4man on 2008-11-13
In regards to amarok

Edit: It just dawned on me that maybe your talking about d. left clicking on tracks *inside of amarok's gui*, if so you can safely ignore this post in that regard (I almost never see amaroks gui and don't know much about it

What you can do is set a 'custom' file association. Amarok has several useful launch commands so all you need to do is decide what you want to happen when d. left clicking on a track.

Two most useful commands for d. left click (there are others see amarok --help or first link below

```
amarok --play
```  Will load track and begin immediate playback, if a playlist exists will leave in place and append clicked track to list.

```
amarok --load --play
```
Will remove current playlist if any, load track and begin immediate playback of clicked track (in other words each d. left click creates a new, single track playlist.

To set a custom file association 
right click ->  properties -> 'open with' on any music file (ext. is irrelevant

Click 'add' and the choose 'use a custom command'. Enter your chosen command in box, click 'add' and exit out.
Whatever file extension you used the properties of will now be set to the chosen command.

To add additional file extensions
right click on another ext. -> properties -> 'open with'. Look for amarok in lowercase letters (vs Amarok). Click the radio button and your set for that ext. (if not there go one level deeper by clicking 'add' and look there

If you happen to set 2 or more custom file associations for amarok then the right click menu (properties or straight up) will show 2 or more lowercase amarok entries. If that becomes the case you'll need to give them names to tell apart. Easy to do, let me know.
see screen


What you may find useful is using the right click menu to control amarok when you want.

It adapts very well to nautilus-actions using any available commands. (Audacious above

[http://ubuntuforums.org/showthread.php?p=5287915#post5287915](http://ubuntuforums.org/showthread.php?p=5287915#post5287915)

What i do also is use nautilus scripts to access my music collection and playback in various players. (bit more involved than nautilus-actions

[http://ubuntuforums.org/showthread.php?p=5797640#post5797640](http://ubuntuforums.org/showthread.php?p=5797640#post5797640)

---

### Post by zero777zero on 2008-11-13
i understand the file association thing, i was looking for the latter part of your post about the nautilus setup. i find it painfully disappointing ubuntu doesnt implement this kind of thing by default. incredibly basic!

thanks for your help

---

