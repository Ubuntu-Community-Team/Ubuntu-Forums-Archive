---
title: "Rhythembox, play queue"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Dadsgé on 2008-11-14
is there any hotkeys to add a song to the play queue?
or can I add them manually to the system?

greetz
D.Dadsgé

---

### Post by Dadsgé on 2008-11-14
bump

---

### Post by Dadsgé on 2008-11-15
bump

---

### Post by mc4man on 2008-11-15
You can do that with a nautilus-action. While other players like Amarok are better suited for nautilus actions or nautilus scripts you can use this only [B]if the tracks/folders are in your rhythmbox library.
[/B]
(for instance Amarok can have several different actions and no need to have a 'library', will work on anything.

Easier with a screen shot

Tested with single files and whole folders

For copy and paste - parameters

```
--enqueue %M
```

This may also be possible, queue and start playback. ( I'd make 2 actions - the above (queue in Rhythmbox) and this - ( clear, queue and play in Rhythmbox)
Edit: the play doesn't work right

Fool around a little, I don't use or know Rhythmbox, but a quick look suggests if these are used on folders they'll work but the track order is 'random', files though are properly queued in order added...

```
--clear-queue --enqueue %M
```

---

### Post by Dadsgé on 2008-11-16
where can i find that nautilus option?

so if i did all that, then i will have a hotkey to add a song to the queue
but which key will it be, and can i change that one if it might be to complicated?

---

### Post by mc4man on 2008-11-16
nautilus-actions is a package you can install, then it's found in System -> preferences.
It is used by right clicking on a file and or folder.

I was just giving you an option to 'hotkeys' which I didn't see any info forthcoming.

You could do this thru custom file associations also, using available commands. (double left click on files
see in terminal
rhythmbox-client --help

Whether you could tie a command to a 'hotkey' I haven't tried.
While I thought maybe you could include a --play parameter, it seems to confuse rhythmbox and when the 'play queue' is done it starts up playing your library, experimentation would be needed.

While i don't like rhythmbox if I find a good solution I'll post it.

---

