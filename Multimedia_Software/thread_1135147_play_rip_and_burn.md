---
title: "play rip and burn"
date: 2009-04-24
forum: Multimedia Software
---

### Post by cloudbounce with LED's on 2009-04-24
here is a link to the page I'm interested in

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html) 

What I  don't understand is   ( First add the sources.list entries in a separate file, depending on your Ubuntu release use the appropriate command. )

what is the sources.list entries
and the  separate file  what and where ??  .no Idea .

(I have no problem with the copy and paste  the red command into the terminal)

---

### Post by hansdown on 2009-04-24
Hi cloudbounce with LED's.

The apt sources.list is used to retreive updates for these particular programs. 

Just copy and paste the red commands that belong with the distro you are using. example, hardy, intrepid, jaunty.

---

### Post by cloudbounce with LED's on 2009-04-24
thanks for the reply

---

### Post by cloudbounce with LED's on 2009-04-24
my next problem is


 I am using ubuntu 8.10 how do I make VLC my default DVD player?

---

### Post by Mze on 2009-04-24
Go to System >>> Preferred Applications >> Multimedia

Select Custom then type **vlc** into the Command box

---

### Post by Mze on 2009-04-24
if the command above doesn't work,

check out tagra123's solution on this [thread]("http://ubuntuforums.org/showthread.php?t=333714")

---

### Post by mc4man on 2009-04-24
> I am using ubuntu 8.10 how do I make VLC my default DVD player? 
In 8.10 it's set in file management -> media

Many ways to access (in terminal
```
nautilus-file-management-properties
```

Enable it (file management) -> in edit menus under system -> preferences (in terminal go
```
alacarte
```

When inserting a dvd hold down shift button, you'll get a popup

or

nautilus -> edit -> preferences

---

### Post by cloudbounce with LED's on 2009-04-24
> **mc4man said:**
> In 8.10 it's set in file management -> media

Many ways to access (in terminal
```
nautilus-file-management-properties
```

Enable it (file management) -> in edit menus under system -> preferences (in terminal go
```
alacarte
```

When inserting a dvd hold down shift button, you'll get a popup

or

nautilus -> edit -> preferences

This is the response I get note  the WARNING should I be worried about that? 
file management preferences is displayed.


alan@alan-desktop:~$ nautilus-file-management-properties
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus-file-management-properties:5803): WARNING **: Unable to add monitor: Not supported

---

### Post by cloudbounce with LED's on 2009-04-24
> **Mze said:**
> if the command above doesn't work,

check out tagra123's solution on this [thread]("http://ubuntuforums.org/showthread.php?t=333714")

Performed your two suggestions.  
VLC now starts when disk is inserted
but I cant get it to play the dvd .

---

### Post by Mze on 2009-04-25
The thread I posted had other solutions too, you might want to go through some of the other options.

mc4man's solution also didn't work for you? Nautilus>>Edit>>Preferences>>Media

Another thing, did the DVD play in another media player before?

Make sure your [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository is enabled

---

### Post by cloudbounce with LED's on 2009-04-25
> **Mze said:**
> The thread I posted had other solutions too, you might want to go through some of the other options.

mc4man's solution also didn't work for you? Nautilus>>Edit>>Preferences>>Media

Another thing, did the DVD play in another media player before?

Make sure your [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository is enabled

no this is the  first time dealing with movie players 

Medibuntu link has helped 
and can now play the movie.

---

