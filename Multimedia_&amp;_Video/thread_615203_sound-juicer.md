---
title: "sound-juicer"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by trak87 on 2007-11-16
I think it is wrong to tie ubuntu-desktop to sound-juicer. This forces a choice on the user in a way that is unnecessarily hard for the user to remove or correct.

I can uninstall sound-juicer but this also removes the ubuntu-desktop. How do I get rid of this thing and make my own choice and not lose any potential updates that might occur in ubuntu-desktop? 

I've tried creating a symbolic link from sound-juicer to gnome-cd. This works when a cd is inserted into the drive, but if I double clink on the audio cd icon on the desktop, sound-juicer starts anyway. How do I change the properties for the cd icon? And I have changed the default preferred multimedia application for audio cd from sound-juicer to gnome-cd.

And then when sound-juicer is updated with an upgrade the symbolic link to gnome-cd is destroyed.

I'm beginning to resent any decision to force media player choices on the user, especially ones that aren't easily reversed. This smacks of Microsoft type control.

---

### Post by nick_h on 2007-11-16
Have you tried the Multimedia section of System->Preferences->Removable Drives and Media ?

There should be no need to create a symbolic link.  I wouldn't uninstall Sound Juicer - just remove it from the menu - right click on the menu then select Edit Menus.

---

### Post by trak87 on 2007-11-16
But there is a need. When I've got an audio cd in the drive and double click on the CD icon that appears on the desktop, how do I get gnome-cd to launch?

As I stated in my first message I've already specified gnome-cd in "Removable Drives and Media Preferences", but sound-juicer still comes up when double clicking on the cd icon that automatically appears on the desktop when an audio cd is in the drive.

Please Ubuntu, don't act like Microsoft!

---

### Post by nick_h on 2007-11-17
"Removable Drives and Media Preferences" should select the application when a new disk is inserted.

If you want to associate a different application with the desktop icon then you need to change the url-handler.  In a terminal type:
```
gconf-editor
```
Then change the entry under desktop->gnome->url-handlers->cdda

---

