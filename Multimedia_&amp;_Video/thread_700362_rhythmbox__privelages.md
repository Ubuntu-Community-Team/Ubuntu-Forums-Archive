---
title: "rhythmbox  privelages"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by Saghaulor on 2008-02-18
I use Rhythmbox to read the data/songs on my Ipod. Unfortunately, it doesn't play well with the database on my Ipod, as it was written by Anapod Explorer in Winxp. Everytime I mount my ipod with Rhythmbox, I have to remount my ipod in Anapod so that the database can be rebuilt, otherwise, the songs are inaccessible from the ipod menu.

What I would like to do is to change the privelages to Rhythmbox so that it can only read and not write, thereby, it cannot corrupt my ipod database anymore.

I've already read how to rebuild your ipod database so that Rhythmbox will not corrupt it, but that is not an option I have available to me presently due to time/hard drive constraints. I just want to modify the privelages given to Rhythmbox so it doesn't corrupt my ipod database any longer.

Can I do a "chmod XXX" command to the Rhythmbox bin or is something more involved required?

---

### Post by nick_h on 2008-02-19
You will need to change the permissions for the mounted media not the rythmbox binary.

---

### Post by Saghaulor on 2008-02-22
Okay, I just read something that alluded to that.

However, for the sake of clarity, if I change the permissions to the media to read only, then I won't be able to write to my ipod with HIPO. HIPO works fantastic for adding and removing data/songs to my ipod, but Rhythmbox doesn't. So I want HIPO to have write permissions but not Rhythmbox. 

There's got to be a way to do this.

Can I make a group that contains certain program access rights and add that group to the permissions?

---

### Post by nick_h on 2008-02-22
Normally permissions in Linux relate to the user running the program.  However, you could look at giving the executable [setuid](http://en.wikipedia.org/wiki/Setuid) which would cause the program to execute with the uid of the program rather than the user running it.

---

