---
title: "Does the &quot;Audio&quot; Dash work for anyone of you?"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bazon on 2011-04-19
When rightclicking "files and folders" in the Unity launcher, the dash only displays that I have no audio files in my homefolder. 
But I have!

So I wonder, what went wrong?

1. It doesn't work in general?
2. It doesn't work because I have the files not directly on my Homefolder, but in my Music folder (which is called "Musik" in the german Version)?
3. It doesn't work because it can't deal with other languages/foldernames ("Musik" instead of "Music")?
4. It doesn't work because my Music-Folder is mount-binded via /etc/fstab?
```
/mnt/sda5/username/Musik	/home/username/Musik	  none  bind  0  0
```
*(I make this because I want to use contents from my maverick homepartition....)*

Does it work for you?

---

### Post by tlcstat on 2011-04-19
Greetings,
I'm not a music person but I downloaded a mp3 to my home folder and no go! I expect this is on their todo list.  Everything else seems to get fixed so I'm sure this will also.
tlcstat

---

### Post by donniezazen on 2011-04-19
Mine shows audio files based on default zeitgiest sorting which is kind of cool.

---

### Post by mc4man on 2011-04-19
At least here Files & folders will show audio (and any other file), but _only files that have been opened_

---

### Post by Bazon on 2011-04-19
But playing them in Banshee (by libary) doesn't seem to "open" them?
So only files opened by doubleclick get there?

---

### Post by mc4man on 2011-04-19
> **Bazon said:**
> But playing them in Banshee (by libary) doesn't seem to "open" them?
So only files opened by doubleclick get there?

Fool around and see .. At least here only audio files (and or folders) opened _From_ nautilus are seen or returned in a search.
(like a r. click 'open with ...' or d. l. click, ect.

---

### Post by seeker5528 on 2011-04-20
> **Bazon said:**
> 3. It doesn't work because it can't deal with other languages/foldernames ("Musik" instead of "Music")?

If you chose the german language/locale while installing I would expect that stuff to be done correctly.

Not sure if you change the locale after the fact or choose a different language for the session on the login screen.

To change where programs expect the music to be, edit the file 'user-dirs.dirs' in '~/.config/'.

Sidenote: according to [http://www.freedesktop.org/wiki/Software/xdg-user-dirs](http://www.freedesktop.org/wiki/Software/xdg-user-dirs) > To disable a directory, point it to the homedir. If you delete it it will be recreated on the next login.

Later, Seeker

---

