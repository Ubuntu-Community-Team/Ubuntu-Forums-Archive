---
title: "Outline of closed windows don't go away"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by hotstovejer on 2006-07-09
Hi all,

I'm having a problem where when a window closes, it leaves either part of the window outline on the screen, grayed out, and lays on top of every other app. Here are some screen shots to show you what I mean.

[IMG]http://www.bowlingkingdom.com/persimages/userupload/ghost.png[/IMG]

[IMG]http://www.bowlingkingdom.com/persimages/userupload/ghost2.png[/IMG]

Any one have any idea what causes this? I have XGL installed, but it did this before I installed it. 

Thanks!

Jeremy

---

### Post by josh22x on 2008-03-12
I am having the same problem with my windows. It usually occurs with Pidgin and putty. With Putty the whole image stays there and with Pidgin, just the outline of the image stays visible. 

They only way to get them to go away is to restart the computer.

Any ideas anyone?????

Thanks
Josh

---

### Post by earthmeLon on 2008-04-20
Same problem here.  Find a solution?


NVIDIA 8800GTX

---

### Post by pseudo-random on 2008-04-20
create a script called refresh.sh on your desktop or linked to a menu.
Put into it just ```
compiz
```
Make it executable (right click, permissions)
Run it (not in a terminal) whenever that happens.

Mine was solved with a driver update and some xorg tweaking but this quick and dirty solution will work for now.

---

### Post by josh22x on 2008-04-20
What kind of script??

refresh.sh - refresh script?? - how do I do that?


Thanks!

---

### Post by earthmeLon on 2008-04-20
Open a terminal and cd to the directory you want the script to be in, so:
```
cd
cd Desktop
```

Then do
```
gedit refresh.sh
```

Now a window will pop up.  just type compiz in it and save the file.  Now you need to make the file executable by runing this:
```
chmod 755 refresh.sh
```

Now you should have a file on your directory called refresh.sh that when you run, will refresh your compiz session, fixing the problem

---

### Post by wesley_of_course on 2008-04-20
gnome-compiz-manager  will do the same thing with an compiz-tray-icon to turn off/on compiz.  Its in synaptic.  Also```
 compiz  --replace 
``` in a terminal  or script it !  Either way hope it works for ya .

              libdecoration0 , "  is responsible for drawing the window borders
and title bar of windows managed by Compiz. It is used by window decorators
like gtk-window-decorator and kde-window-decorator."

---

