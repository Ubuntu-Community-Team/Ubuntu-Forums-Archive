---
title: "[SOLVED] Linus Torvalds froze my computer!"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by thedaylights on 2008-01-28
So I went to the Wikipedia page for[ Linus Torvalds]("http://en.wikipedia.org/wiki/Linus_Torvalds") and, curious about the correct pronunciation of his name, I clicked on the "pronunciation" link. A wikimedia screen displaying an .ogg file opens and my OS freezes solid as a block of solid frozen coffee. Why did this happen? Why would you do this to me Linus Torvalds? Is your very name kryptonite to your eponymous OS?

---

### Post by disturbed1 on 2008-01-28
Do you dual boot with Windows? :):):):)



Sounds like a plugin issue with Firefox. Are you using mplayer, vlc, or the default Totem plugin.

Also, right-click on the link and choose save as. I just went to the website, and the link played fine. I'm using the default Totem plugin for Firefox.

---

### Post by thedaylights on 2008-01-28
:lol: Ha ha ha. I'm a total beginner with linux. But no, not dual-boot.

I haven't added vlc or any other plugin for firefox except flash. In fact, I just removed Gnash and reinstalled Flash from adobe's site to fix a bug in youtube playback. So maybe when I removed Gnash it did something? I guess I'm using default Totem plugin. I'm running Firefox 2.0.0.11 from a fresh install of Gutsy.

---

### Post by picpak on 2008-01-28
Try installing totem-xine? My media files work properly with it. Run this in the terminal and try going back to the site:

```
sudo apt-get install totem-xine
```

---

### Post by thedaylights on 2008-01-28
Thanks picpak! You rock! And also, Linus Torvalds sounds funny.

On a related note, anyone know how to cancel a process that has frozen the OS? Like ctrl-alt-del in Windows.

---

### Post by doorknob60 on 2008-01-28
Press ALT-F2 and type xkill and the next program you click on will be killed. I even added it to my Gnome panel :)

---

