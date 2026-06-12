---
title: "Rhythmbox repeat one???"
date: 2008-12-19
forum: Multimedia Software
---

### Post by 11010110 on 2008-12-19
Hey is there any way for rhythmbox to repeat one song only? the repeat button makes it repeat whatever is on the screen and if im browzing albums and i want to play one song a few times i dont want to have to make a playlist of just that song... There has to be a way. I like the interface (im an itunes veteran) and its inconceivable for a music player not to have repeat one. Is there some sort of plugin or something?

Thanks in advance all.

---

### Post by 11010110 on 2008-12-20
ok well i found a plugin that supposedly allows for one song repeat but i cannot figure out how to install it. anyone know how?

---

### Post by 11010110 on 2008-12-20
hey all actually never mind i got songbird and i could not be happier!

---

### Post by eduardo-mucelli on 2010-05-29
The [Repeat One Song]("https://launchpad.net/repeat-one-song/") plugin solve this.

---

### Post by tsg1zzn on 2010-12-21
I have this problem as well. The repeat one plugin works, but repeating a single song breaks last.fm scrobbling (which is the only reason I would bother with Rhythmbox in the first place).

---

### Post by say.hello.to.anna on 2011-07-11
Dear all struggling with this silly problem. 

**STEP ONE: **go here, [https://launchpad.net/repeat-one-song/](https://launchpad.net/repeat-one-song/), click green download button. Watch the file download.
[B]
STEP TWO: [/B]Right click on downloaded file (should be in downloads folder if you've lost it) and chose to extract. Try and extract it in the same location. Keep this window open, you will need it later.

**STEP THREE:** open your terminal (applications>accessories>terminal) if its not there, you are looking for that black boxy window where you can type stuff and it looks like computing from when you were a kid/when your parents were kids. It will open and say something like name@name-blah;-$

**STEP FOUR.** Type in 

**sudo nautilus**

you will be asked for your password. Type your password and hit enter/return. It wont show you are typing as you type, no stars or anything like usual ( just concentrate on the keyboard and ignore the screen, its a bit disorienting.).

When you hit return a window should open saying root. Its very important you** don't mess about** now, because you have total access to everything fragile and sensitive. So... 

**STEP FIVE **- using this special window, go into your FILE SYSTEM (on the side bar) 
then go 

**USR > LIB > RHYTHMBOX** (click the letter R on your keyboard to jump to the R's) > **PLUGINS**. 

**STEP SIX:** grab the file from the old window, the file named  "repeat-one-song" (not the orange with tar.gz at the end, the normal looking one) Then drag it and drop it into this plugins file. Close both windows now.

**STEP SEVEN:** open/reopen rhythmbox, click EDIT, PLUGINS, and tic/check the REPEAT ONE SONG box.
then click close.

**FINISHED:** you should now have a new button that looks like your normal loop but had a number 1 on it.

**ONE LAST THING:** write down the** sudo nautilus **phrase and remember what it does. Every time people in the forums talk about root files and adding files or detesting them to make stuff work/change how it work, and you end up being told you don't have **permission**, use this to open up your special window and move the files in the way you have been instructed. Remember, its a serious matter and be careful only to use it in the manner your have been told on the forum.

Love from

Anna [www.okaycompuer.org](www.okaycompuer.org) and [www.flossie.org](www.flossie.org)

---

### Post by ubuntukid on 2012-02-20
Am I the only one thats slightly bewildered by the fact that a modern music app doesn't have this out of the box? Sounds like a prime candidate should the ubuntu team do another 100 paper cuts thing again.

---

### Post by mkt1971 on 2012-05-23
> **ubuntukid said:**
> Am I the only one thats slightly bewildered by the fact that a modern music app doesn't have this out of the box? Sounds like a prime candidate should the ubuntu team do another 100 paper cuts thing again.


No, you're not the only one bewildered. It hasn't been implemented as of 12.04 (as far as I can tell.) Moreover, the latest 'repeat-one-song' plug-in (v0.2) from launchpad doesn't seem to work either.... But, why need a plug-in at all? This is basic media-player 101 stuff. I rated it with one star on the software center citing this as the reason.

---

### Post by oldos2er on 2012-05-23
Old thread closed.

---

