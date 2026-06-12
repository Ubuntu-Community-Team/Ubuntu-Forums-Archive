---
title: "how do i make VLC default player?"
date: 2009-07-08
forum: Multimedia Software
---

### Post by nacho32 on 2009-07-08
how do I make jaunty 9.04 have vlc as my default player everything always wants to open with Totem player I want it to auto open with the VLC.

thanks

---

### Post by starcraft.man on 2009-07-08
Easy. Right click the file type (the video file) and then go to the open with tab. There you should see listed totem, VLC and any other video players. Just select VLC and close, then all the same types of files will open with it forever. If you want to change again just repeat. If you have several different types of video files repeat for each, like say avi's, mkv, mp4...

---

### Post by nacho32 on 2009-07-08
the odd part is it dose not show the vlc player to be a option just shows the totem player

---

### Post by RD1 on 2009-07-08
quick edit ....

> Easy. Right click the file type (the video file) [COLOR="Red"]SELECT PROPERTIES[/COLOR] and then go to the open with tab. There you should see listed totem, VLC and any other video players. Just select VLC and close, then all the same types of files will open with it forever. If you want to change again just repeat. If you have several different types of video files repeat for each, like say avi's, mkv, mp4...

---

### Post by starcraft.man on 2009-07-08
> **RD1 said:**
> quick edit ....

Hahah! Sorry Fry and the Professor were distracting me on the other screen. 

RDI is correct with his insertion, you right click the video file then > Properties > open with... tab and then select the player of your choice. It should be in the selection pane unless something funky happened during installation.

---

### Post by mc4man on 2009-07-08
For removable media (cd, dvd, ) you can set in file management -> media
from terminal
```
nautilus-file-management-properties
```

For single files off of the d. left click as mentioned set once per file type from r.click -> properties -> open with

For vlc 0.9.x and 1.0 there is a option in tools -> preferences to " Allow only one instance' which you'd want to set.

Unfortunately the companion setting " Enqueue files in playlist when in one instance mode" doesn't work

Without that when adding add. files they will be queued and start playing, bypassing current and other files.

A more useful choice atm for the right click -> properties -> open with would be to continue on and click add -> use custom command

For a custom command use
```
vlc  --playlist-enqueue 
```

Back on the add screen you'll see a new choice 'vlc' in small letters (though there may be more than one

What you should do now is give your custom command a unique name

To do so immediately  go to home folder -> .local/share/applications. The custom command is actually a userapp.desktop seen as a blue diamond icon with a display name in this case of vlc.

Right click on it -> properties and give a new display name - I used Vlc Enqueue. You can give it a vlc icon if desired.

Then when r. clicking -> properties .... on other file types you'll see Vlc Enqueue as a choice. 
Screen one shows that, the highlighted one shows how it would look before the renaming. (vlc)

screen 2 show the properties of the custom command (userapp.desktop) in case you find a couple in `/.local/share/applications

You only need to set up one custom command, can be used on any file type you wish from d. left click or the r. click menu

---

### Post by nacho32 on 2009-07-09
work like a charm thanks guys

---

### Post by Flimm on 2009-07-09
You might also want to set your preferred multimedia application to VLC:
Open System, Preferences, Preferred Applications, then change to Multimedia tab, choose Custom, and enter vlc.

---

### Post by furqanbhai on 2010-05-31
Thanks a lot all u guys.....

---

### Post by EduardoMartins on 2010-12-16
I'm unable to set VLC as my default player for MP4. Neither right-clicking and choosing "Open with Other Application" nor using Preferences > Preferred Applications is working.

It only works if I delete Totem (which is not what I want, as I prefer it for MP3 files).

Also, since a fresh install last week, Totem has been acting strange, not letting me browse to different points on video files (they are not corrupted, working fine on VLC), but that's an issue for another topic, I guess.

I am using Ubuntu 10.04 64-bit.

Thanks,

Eduardo

---

