---
title: "iPod not connecting with Exaile"
date: 2008-05-12
forum: Multimedia Software
---

### Post by LonelyTraveler on 2008-05-12
I'm trying to use Exaile to add and remove tracks on my iPod, but get the following error everytime I try and connect:

"Error connecting to iPod. Make sure you specify the right mount point in the plugin configuration."

I worked once I think, but now it doesn't anymore.

In Rhythmbox I use to be able to add tracks but not delete. Now, it looks like it adds but doesn't. 

I'm not too worried about Rhythbox, but I really want Exaile to work.

Thanks in advance for the help.

---

### Post by LonelyTraveler on 2008-05-13
I must be the only one having this problem. Anyone here using Exaile on Hardy?

---

### Post by aeiah on 2008-05-13
you arent the only one, but i cant help right now im afriad. i did try it briefly and got the same error as you, but i dont transfer stuff that often so i just use gtkpod now. is the plugin looking in a different place to where the ipod is mounted?

---

### Post by LonelyTraveler on 2008-05-13
> **aeiah said:**
> you arent the only one, but i cant help right now im afriad. i did try it briefly and got the same error as you, but i dont transfer stuff that often so i just use gtkpod now. is the plugin looking in a different place to where the ipod is mounted?

It tries to look in /media ,but I changed it to IPOD. I also use gtkpod at the moment, but would like to have all my music things in one program.

---

### Post by aeiah on 2008-05-13
according to [the code](http://www.exaile.org/files/plugins/0.2.12/ipoddriver.py) the default destination is /media/ipod

perhaps it is an upper/lowercase issue? does it even give you the chance to specify a different path?

---

### Post by LonelyTraveler on 2008-05-13
> **aeiah said:**
> according to [the code](http://www.exaile.org/files/plugins/0.2.12/ipoddriver.py) the default destination is /media/ipod

perhaps it is an upper/lowercase issue? does it even give you the chance to specify a different path?

It does. And I have selected /media/IPOD. The ipod is in caps though.

---

### Post by mixtri on 2008-05-19
Hello guys. I'm aware this post is 6 days old, The trail seems to have gone cold.
No resolution or fix recorded in this post. Where you able to resolve your problems?

Anyway, I seem to have the same problem. Exhaile does not even detect my Ipod. i.e Ipod does not appear in the devices tab in Exaile.

I have the gtkpod pluggin installed and configured as per exaile. 

I also pointed exaile to the /mnt folder but that didn't work. I have since tried pointing to the /media and media/ipod folders to no avail.
is there a reason for this behaviour?

I just upgraded exaile to the current release in the hope that my problem may have been a flaw in the previous release which might have been fixed in the current. But No! that is not the case. the problem still persists.

Can anyone help?

---

### Post by mixtri on 2008-05-19
Just to add.. My ipod is recognised by rythmbox which promptly lunches when i connect the ipod.

:)

---

### Post by LonelyTraveler on 2008-05-19
> **mixtri said:**
> Just to add.. My ipod is recognised by rythmbox which promptly lunches when i connect the ipod.

:)

Same thing here, but my Rythbox doesn't delete anything off my ipod.

I've been using gtkpod now, but none of my music programs are indexing my music properly. It is like it doesn't see all my albums.

---

### Post by mixtri on 2008-05-19
I thought gtkpod was a pluggin for exaile. Or am i mistaken? is it also a standalone player?

I have tried many of the music players available and Exaile fulfills most of my requirements, which is its ability to easily record streaming music at the click of a button. Not forgetting its simple interface and ease of use. However it still lacks some desirable features usually present in windows based players such itunes and Winamp.

If only I could solve this problem with the ipod then I would be happy to stick with exaile.

I currently rip music off my fave radio stations using exaile and save to disk.
import tracks to rythmbox then to my ipod where i then have to search for each track to transfer into a faves folder. I do this becuase there is no recently added tracks tab in ipod i could use to locate added tracks.
This is arduous work indeed.

:confused:

---

### Post by LonelyTraveler on 2008-05-19
I also love Exaile and that is what I use to play music on my laptop. That is why I would have loved for the iPod to work. I'm trying aTunes at the moment. It is a copy of iTunes as you can probably figure out yourself, but I'm having trouble adding any song databases. I can't get it to scan my folders!?!?!?

---

