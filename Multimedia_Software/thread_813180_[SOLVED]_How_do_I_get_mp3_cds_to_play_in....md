---
title: "[SOLVED] How do I get mp3 cds to play in..."
date: 2008-05-30
forum: Multimedia Software
---

### Post by captainsixxx on 2008-05-30
How do I make the proper changes to get my mp3 cds to play in my standard music player and not TOTEM Movie player.

---

### Post by cariboo on 2008-05-30
Right click on an mp3 file and choose Open With and then choose Open with Other Application, select the application you normally use. It will be located in /usr/bin.

Jim

---

### Post by captainsixxx on 2008-05-30
Well that worked, but i was looking a little more towards a default and it completely opening the cd. But thanks again. 

Edit---Sorry--- I am using Ubuntu hardy 8.04.

---

### Post by ubuntu-freak on 2008-05-30
If you can't set it in Nautilus > Edit > Preferences > Media or System > Preferred Applications, try:
 
**gksudo /etc/gnome/defaults.list** 
 
Search for "audio" or "mp3", then change it from "totem.desktop" to whatever application you want, "rhythmbox.desktop" for example. Up to you, but be careful with that configuration file.
 
Nathan

---

### Post by captainsixxx on 2008-05-30
> **reassuringlyoffensive said:**
> If you can't set it in Nautilus > Edit > Preferences > Media or System > Preferred Applications, try:
 
**gksudo /etc/gnome/defaults.list** 
 
Search for "audio" or "mp3", then change it from "totem.desktop" to whatever application you want, "rhythmbox.desktop" for example. Up to you, but be careful with that configuration file.
 
Nathan
Ok? before I try the [B]gksudo[B] command... I cant even find Nautilus. So I would have to ask what it is and where to find it.

---

### Post by cariboo on 2008-05-30
Click on Places on the upper panel, assuming you're running gnome, then click on edit|preferences then the last tab to the right labeled media. You can set your prefered programs there.

Jim

---

### Post by ubuntu-freak on 2008-05-30
Any folder or location you open is shown in Nautilus, it's the default file browser.
 
Nathan

---

### Post by pdadad on 2008-05-30
In Gutsy the following worked somewhat for me:  System -> Preferences -> Removable Drives and Multimedia Preferences -> Multimedia then type "rhythmbox" in the command line for audio CDs.

The problem is that the player opens but the CD does not play.  You have to select the CD in the left window then click play.

---

### Post by captainsixxx on 2008-05-31
Sorry everyone I forgot to mention that I am using Ubuntu 8.04 hardy.

---

### Post by captainsixxx on 2008-05-31
> **reassuringlyoffensive said:**
> Any folder or location you open is shown in Nautilus, it's the default file browser.
 
Nathan
Thank you for that info, I did not know that, so now I know

---

### Post by mcduck on 2008-05-31
To set the default program for opening files don not use the right-click->Open With. That only works for that time, and doesn't change the default program.

Instead use right-click->Properties->Open With. This will change the default application for opening all files of that type.

---

### Post by ubuntu-freak on 2008-05-31
You didn't post how you solved it. Someone else might be interested. Was it /etc/gnome/defaults.list, File > Properties > Open with or Nautilus media preferences?
 
Nathan

---

### Post by captainsixxx on 2008-05-31
> **mcduck said:**
> To set the default program for opening files don not use the right-click->Open With. That only works for that time, and doesn't change the default program.

Instead use right-click->Properties->Open With. This will change the default application for opening all files of that type.
This is the route that seemed to work for me, thanks again for everyones help.

PS. The only downside to using Rhythmbox Music Player is that you have to go through and tell it to scan and add the cd, other than that it what I was wanting. Thanks again.

---

### Post by ubuntu-freak on 2008-05-31
Give Exaile a try, it's a great music player.
 
Nathan

---

### Post by Unix_Slayer on 2008-05-31
I use Amarok. Works great. You need to download the MP3 codec/add on for it to work.

---

### Post by Unix_Slayer on 2008-05-31
BTW..... Winamp also works in Ubuntu.

---

### Post by ubuntu-freak on 2008-05-31
> **Unix_Slayer said:**
> I use Amarok. Works great. You need to download the MP3 codec/add on for it to work.

 
Exaile is a GTK fork of Amarok. It's coming along nicely too.
 
Nathan

---

### Post by Unix_Slayer on 2008-05-31
> **reassuringlyoffensive said:**
> Exaile is a GTK fork of Amarok. It's coming along nicely too.
 
Nathan

How about Amarok Nightly? Did you try it yet?



Dude..... Exaile is really cool. Thanks for the shot!

---

