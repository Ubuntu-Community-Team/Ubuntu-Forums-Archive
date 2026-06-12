---
title: "Prompt for a password before each song is played"
date: 2009-07-08
forum: Mythbuntu
---

### Post by acastaneda on 2009-07-08
Good morning everyone,

I have a Mythbuntu box (that acts as both the backend and frontend), and I've enabled the MythWeb plugin.

I'd like to add a bit more security to this box, but if I enable a MythWeb password, then I get prompted to enter said password before each song. If I don't set a password for it, I am able to stream music to another computer without any problems.

My host machine is running Windows XP, and I'm using VLC to listen to the stream. Using Windows Media Player also errors out.

I'm sure this is a simple solution, but any guidance would be appreciated.

Thank you,

-angel

---

### Post by theophile on 2009-07-08
No, this is a major limitation of the built-in Mythweb authentication. My solution is to turn off authentication and make the Mythweb subdirectory un-guessable.

---

### Post by bcgrown on 2009-12-31
Has anyone found a solution for this?

Mythbuntu 9.10 doesn't seem to use the .htaccess file,  so where is the authentication configured?  It should be possible to add an exemption for certain directories.

---

### Post by bmoafmuta on 2010-01-12
[http://wiki.archlinux.org/index.php/MythWeb](http://wiki.archlinux.org/index.php/MythWeb)

---

