---
title: "Flashplayer not working properly after upgrade to 8.10"
date: 2008-11-08
forum: Multimedia Software
---

### Post by lashi on 2008-11-08
G'day. 

So, I've upgraded to 8.10, but Flash 10 seems to be distinctly more faulty than Flash 9. When it does work, it sometimes screws up audio, not giving me audio out until I push the audio control in flash to the highest position. This happens on [http://www.abc.net.au/7.30/](http://www.abc.net.au/7.30/)

The second issue is that it sometimes crashes, crashing Firefox/Galeon with it. This happens quite frequently on Youtube.

Anyone else in the same boat as me, and does anyone know how to fix it?

---

### Post by gandaran on 2008-11-08
okay. you upgraded, do you still happen to have flash 9 and libflashsupport installed?
post here the output of **locate libflash**

---

### Post by lashi on 2008-11-08
Hey mate. 

So, I figured out what was wrong. There were two issues:  

(1) I had followed the directions given by:  

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

to install Flash 10 on 8.04. I did that because I thought my player broke for a second, found it it didn't, and I didn't think it was necessary to degrade back to Flash 9. I thought that install was "clean" but it wasn't - it didn't install a deb and so during the upgrade to 8.10, it left files behind in /usr/lib/mozilla/plugins, which prevented flashplayer-nonfree and nspluginwrapper from installing correctly. By this I mean that nspluginwrapper -l didn't list /usr/lib/mozilla or /usr/lib64/mozilla. 

(2) swfdec-mozilla and swfdec-gnome was installed, and the player that was loading wasn't Flash 10 at all!

This is a big more of a problem and not my fault, unlike (1). If a user installs the gnome package (as I had done, for reasons I cannot recall), then it installs swf as a dependency, then even after installing flashplugin-nonfree, SWF is loaded as the default player. So, all my complaints in the first post were for the SWF player - I didn't even realise that this was installed! I usually use galeon, so I went into Firefox, disabled SWF player, and it still didn't seem to work. I found this rather dissatisfactory. 

Anyway, I wasn't interested in doing a patchy, band aid solution of deleting symlinks pointing to swfdec. So, I removed swfdec-mozilla and swfdec-gnome (thereby also removing a gnome, gnome-desktop-environment and a whole lot of other packages, some of which I'll have to reinstall). This got things working again.

---

### Post by gandaran on 2008-11-08
you can keep swfdec-gnome installed if you like it ( I don't, I prefer the adobe stand alone player), it's just a stand alone player won't interfere with firefox

---

### Post by lashi on 2008-11-08
Well, you see, I don't really care for it. I didn't even know it was installed. I just checked, swfdec-mozilla and swfdec-gnome were added as dependencies for the gnome package in 8.10, they weren't there in 8.04. So, you see, I didn't even realise they were installed!

---

