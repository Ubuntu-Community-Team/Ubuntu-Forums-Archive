---
title: "Mythbunut and home server in same box???"
date: 2010-11-08
forum: Mythbuntu
---

### Post by chipppy on 2010-11-08
Good morning

I am looking a building a system for the new house.
I want to have a single dedicated mythtv backend and also a server for all the computers in the house, including print server for our 1 printer.

Is it possible to use the one box and therefore 1 set of HDD's to do this???
I am assuming a decent power PC setup will be required.

If yes where could i find a good guide on how to do this.  I am new to server type setups and this would be my first real system design.

Could this system also be used for our Internet entry point to the home LAN.  Yes it is wired as I am not a fan or wireless security.

cheers
chipppy

---

### Post by elgordo123 on 2010-11-08
I do this. I created a new directory on my mythbox (where videos, music etc are kept).   Inside of that are other directories and I use samba to share them.   
As far as the printer server goes, just make sure that your printer is compatible with linux and if it is you'll be fine. 
Just be careful about drive space. As soon as my kids found out they could put stuff on their "Z" drive (shared) they put everything there - fills up full of kids junk pretty fast if you dont keep an eye on it. 
You can even share your music or video directories (I recommend read only) so they can listen to music or watch movies.

---

### Post by uncle hammy on 2010-11-08
Sure.  My myth backend serves as a fiel server, vpn server, dns server, etc.  If it's got the juice, no problem.

---

### Post by nickrout on 2010-11-08
File and print serving needs next to no cpu power, so you don't really need a machine any more powerful than you would otherwise use for a backend.

---

### Post by teet on 2010-11-09
As others have stated, just create a samba share for your "file server".  I would suggest installing the utility called "system-config-samba".  It makes setting up your samba shares MUCH MUCH easier.

Try this for your printer server:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

You won't need a very powerful machine to act as a file/print server.  

-teet

---

