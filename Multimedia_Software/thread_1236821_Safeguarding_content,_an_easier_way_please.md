---
title: "Safeguarding content, an easier way please"
date: 2009-08-10
forum: Multimedia Software
---

### Post by afrodeity on 2009-08-10
I am tired of losing content to my audio players. Is there a way to safeguard my music folder, without having to chmod:confused: the files by opening a terminal and selecting the file etc etc? What I am actually looking for is a permissions manager. Something which will catalog my music and safeguard the valueable files at the same time.

Please help.

---

### Post by ajgreeny on 2009-08-10
I don't understand, how do you lose content to your music players?  Are you loosing the files completely or is it some other problem?  I don't see a problem of any sort on my system, so feel you must have yours set up very differently in some way or other.  Perhaps your music files have different permissions to normal; a chmod is certainly never needed normally.

---

### Post by afrodeity on 2009-08-11
Yes, I am losing files, and its probably one of the audio players which is destroying them for some reason. Don't know which one it is. Real pain. I need to stop the files from being deleted somehow. And was wondering if there was a manager, or do I have to do this manually?

---

### Post by Crunchy the Headcrab on 2009-08-11
I've never had any music player delete files.  I've used Rhythmbox, Exaile, Audacious, Banshee, Amarok, and XMMS.

The problem is probably that your music player is set to delete songs when they are removed from a library/playlist so you are unwittingly deleting your own files.  I'm not saying this is definitely the case, but it is certainly the easiest way for music files to disappear in general.

Just a few questions about your library.  Where is it stored?  Is it on the same hard drive and partition as your Ubuntu installation?  If not where is it (external hard drive, etc)?

---

### Post by Barafu Albino Cheetah on 2009-08-11
It may be the problem of your filesystem. It may be the problem of anything else. And I don't know an easier way to make files read-only than ```
chmod -R a-r /home/music
```

---

### Post by afrodeity on 2009-08-14
> **Barafu Albino Cheetah said:**
> It may be the problem of your filesystem. It may be the problem of anything else. And I don't know an easier way to make files read-only than ```
chmod -R a-r /home/music
```

Now I can't see or read what's in the folder!!!

---

