---
title: "My music collection"
date: 2009-02-17
forum: Multimedia Software
---

### Post by theozzlives on 2009-02-17
I'm tired of having my music collection on several computers. Besides keeping it updated, it's a waste of space. I want to have my music on one computer and access it through my network and I'd like to use Amarok to do it but I don't see how, any ideas?

---

### Post by mikewu on 2009-02-17
I would suggest using mpd(Music Player Daemon). Once you move all your music to one computer, mpd creates a database and you can manage everything with a remote shell. In order to hear the music from other computers you would need to install icecast or pulseaudio, both of which work nicely with mpd.

Searching around a bit, the generally accepted solution for amarok is to mount the remote folder with samba and play the files.

I don't use amarok so can't really help you much further, but here's their site which guides you through the steps.

[http://amarok.kde.org/wiki/Samba](http://amarok.kde.org/wiki/Samba)

---

### Post by theozzlives on 2009-02-17
So do I install mpd on the computer with the music?

---

### Post by mikewu on 2009-02-17
> **theozzlives said:**
> So do I install mpd on the computer with the music?
Yes.
> sudo apt-get install mpd 
on the main computer. 

In order to control the main computer, you need a client on each one. mpc is a nice command line program.

[http://wiki.archlinux.org/index.php/Mpd#Client_Install_Procedure](http://wiki.archlinux.org/index.php/Mpd#Client_Install_Procedure)

Has a couple other clients as well as instructions for installing.

---

### Post by theozzlives on 2009-02-17
CRAP! I can't get it to work, I can port forward Real Audio on my router and have Real Player 11. Would that do anything? I'm trying to use Amarok, and you have to mount the share in the fstab, but my wireless don't kick in until after I'm at my desktop.

---

### Post by theozzlives on 2009-02-18
bump

---

