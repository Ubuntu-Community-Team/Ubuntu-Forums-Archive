---
title: "Sound-juicer rises from the dead"
date: 2009-10-28
forum: Multimedia Software
---

### Post by Randypan on 2009-10-28
Hello

Whenever I'm trying to acces an audio-CD from the Places menu, it gives me the following error message:

"Failed to run sound-juicer, no such file or directory" (- roughly translated from greek, not the actual text, it also says something about it being a daughter-process or something)

The thing is I uninstalled sound juicer ages ago. Also I have set up nautilus into opening audio-CDs as regular directories and this works in a nautilus window ( I right-clicked on the cd icon in the Computer Directory and selected 'open with') . The Places menu is the only thing that gives me trouble.

Sound juicer was properly installed and completely uninstalled via Synaptic, but this configuration persists in existing and I dont know how to change it.

---

### Post by vinutux on 2009-10-28
known...issue thats happen with uninstalling of pre-installed apps....

---

### Post by Randypan on 2009-10-28
So, isn't there any way of making it go away?

---

### Post by Boondoklife on 2009-10-28
Check under nautilus and click on edit -> prefs -> media
then see if there is an auto run for cds that is set.

---

### Post by Randypan on 2009-10-28
I have set Alsaplayer to autorun audio CDs in the media tab and it worked all along. The problem is focused solely in the audio-cd entry of my Places menu. Other than that autorun works fine- audio CD acces through the 'Computer' directory also works fine. It's just the Places menu that gives me trouble. Weird isn't it?

---

### Post by mc4man on 2009-10-29
Came up recently, here is short explanation
[http://ubuntuforums.org/showthread.php?t=1304005](http://ubuntuforums.org/showthread.php?t=1304005)

if wanted, you can set clicking on that entry to do whatever you wish

(even easier if you have a ~/bin, then the sound-juicer 'whatever' can go in there (a link, exec, or script, ect.
Atm here links to cd rip script

---

### Post by Randypan on 2009-10-29
It worked. I created a link named 'sound-juicer' in usr/bin pointing to alsaplayer. Thanks.

---

### Post by cosmic-cloud on 2010-06-10
People, I think I found the best solution to this problem. Many suggest to create a dummy link to sound-juicer, but it's not a proper solution. I went into the System Tools --> Configuration Editor and searched there for "juicer". It found a key "/desktop/gnome/url-handlers/cdda/command". Change its value from "sound-juicer %s" to "rhythmbox %s", for example, and the Places menu will work as desired. Hope this info helped someone

---

