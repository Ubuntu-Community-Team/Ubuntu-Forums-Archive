---
title: "No multimedia tab in System -&gt; Preferences -&gt; Removable drives and media"
date: 2008-04-22
forum: Multimedia Software
---

### Post by happymonkey on 2008-04-22
I have just installed Hardy and am trying to get it configured. Everything has gone really well and I can't say enough good things about this release. However, I'm trying to get VLC to be set up as the default video player and I'm having a bit of a problem. Normally, I'd go to System -> Preferences -> Removable drives and media and choose the multimedia tab and enter the vlc %m command for the DVD option. Has something changed in Hardy that I've not seen? I don't see any way to specify an application to be the default player for DVD videos. Any help on this would be really appreciated as it's the last thing I need to do before I consider the install/setup complete.

---

### Post by cor2y on 2008-04-22
Search the hardy heron section to see how to pick your default dvd player app.
The tab is now located in the Nautilus browser under Edit->Preferences in the media tab.

---

### Post by SimonJones on 2008-04-24
How does this allow me to set mplayer instead of totem? All I can do is choose "movie player" which is not doing it.

---

### Post by cor2y on 2008-04-24
If you want to set mplayer or vlc etc to be the default media player.
You can either set this by right clicking on the file type and selecting properties and adding you media player of choice as the default player or edit ~/.local/share/applications/mimeapps.list
Want all avi files to open with mplayer then ```
gedit ~/.local/share/applications/mimeapps.list
```
And replace```
video/x-avi=totem.desktop;
``` with ```
video/x-avi=mplayer.desktop;
```
Do this for the media file types you desire vlc would be vlc.desktop note that this is the only way at present to select a different default dvd player than totem-xine or totem-gstreamer.
There is no gui way of doing this in 8.04 yet or if there is i and others have not found it.

---

### Post by SimonJones on 2008-04-25
Thank you for that! :-)

---

### Post by happymonkey on 2008-04-26
Glad to see that you got the information that you needed. There is a way to get VLC to open automatically when you put a DVD into your computer but I cannot find the forum entry where I found the instructions. If you search the forums here for vlc default dvd player in hardy herron you should be able to find a tutorial on what files to edit in order to have VLC be the default DVD player and to have it open automatically when a DVD is inserted.

---

### Post by ubuntu-freak on 2008-04-27
> **happymonkey said:**
> Glad to see that you got the information that you needed. There is a way to get VLC to open automatically when you put a DVD into your computer but I cannot find the forum entry where I found the instructions. If you search the forums here for vlc default dvd player in hardy herron you should be able to find a tutorial on what files to edit in order to have VLC be the default DVD player and to have it open automatically when a DVD is inserted.

 
Part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683) has those instructions, I discovered an easy method last week. The thread is now a sticky by the way, it's in this very section of the forum.
 
Just a note: If you edit:
 
**gksudo gedit /etc/gnome/defaults.list**
 
and change the DVD/VCD player to vlc.desktop or mplayer.desktop, it will show up for all user accounts. It's detailed in my sticky if you need more info.
 
Nathan

---

