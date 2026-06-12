---
title: "Problem opening AVI VIDEOS (Avi Document) with every media Player"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by abhijitkarmokar on 2007-09-06
Hello Folks !!

I am facing this real nagging problem since last few days .... a lot of searching resulted in basically nothing ... so here goes ...

Whenever I double click on any AVI Video File i get this real nagging error message box pop up saying the following 

> 
The filename "asdfasdf.avi" indicates that this file is of type "avi document". The contents of the file indicate that the file is of type "AVI video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "AVI video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


If i do as the message box says it works fine .. meaning if I right click and say open with VLC it plays fine .... 

I am attaching a screenshot for reference !! 

Would really appreciate some help !!

~ Abhijit

---

### Post by JungleJoker on 2007-09-26
I'm having the same problem, anyone have a solution?

---

### Post by JungleJoker on 2007-09-30
So I found a solution (sort of). You have to rename .avi to .AVI If you do this, vlc or whatever default program you're using will play it without any trouble...

(I still think it's kinda weird, 'cause a few days ago i had no troubles with .avi files at all...)

---

### Post by emwine on 2007-11-29
I had this exact issue and solved it by messing around in ~/.local/share/mime.

I don't know exactly which step fixed it, but I was using grep -R and carefully doing backups and moving files containing "avi document".  Just be careful what you do in there and that you can restore if you goof up.

---

### Post by Cheesecurry on 2007-12-19
Hi,

I had this problem and was able to resolve it as follows:

Go to ~/.local/share/mime (thanks emwine!)
Open file **globs**
Replace the text
```
application/x-extension-avi
```
with the text
```
video/avi
```
Repeat for the files **application/x-extension-avi.xml** and **packages/override.xml**.

I made copies of these files first in case!

When I rebooted everything started working again fine.

I haven't worked out what the application update-mime-database does (which claims to have made these files) but these seems to be where the problem is coming from.

Renaming the extensions to .AVI from .avi also worked for me, but this is the nearest to the root cause that I could find.

---

