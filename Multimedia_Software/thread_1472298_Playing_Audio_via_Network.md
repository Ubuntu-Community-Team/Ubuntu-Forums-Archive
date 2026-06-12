---
title: "Playing Audio via Network"
date: 2010-05-04
forum: Multimedia Software
---

### Post by Kai Summers on 2010-05-04
OK, so I have a samba share on my Ubuntu server that holds my mp3 files, and I can play these files from which ever PC in the house whether its my Laptop (Linux) or Desktops (mix of Windows, Linux & Mac) At the moment my Windows Desktop PC has a sound system connected to it and I vnc to that computer to change tracks create playlists etc to play through the nice sound system, however I want to be able to play through local rhythmbox or similar and play the sound via the networked windows (xp) pc.

So is this possible???

Any help or advice would be appreciated!!

---

### Post by nothingspecial on 2010-05-04
> **Kai Summers said:**
> OK, so I have a samba share on my Ubuntu server that holds my mp3 files, and I can play these files from which ever PC in the house whether its my Laptop (Linux) or Desktops (mix of Windows, Linux & Mac) At the moment my Windows Desktop PC has a sound system connected to it and I vnc to that computer to change tracks create playlists etc to play through the nice sound system, however I want to be able to play through local rhythmbox or similar and play the sound via the networked windows (xp) pc.

So is this possible???

Any help or advice would be appreciated!!

Do you mean you want to synchronise it.

Have a look at [[COLOR="Magenta"]squeezebox server[/COLOR]]("http://www.logitechsqueezebox.com/support/download-squeezebox-server.html")

It`s software that`s supposed to run their hardware but they have an emulator plugin which you can put on both computers and synchronise that way.

There`s probably a better way without the hardware, but it would work.

---

### Post by Kai Summers on 2010-05-04
No sorry, I don't mean to sync as all clients to the samba share auto sync with the tracks which is fine if I'm working locally, but what I am trying to do is play the song on my laptop (Ubuntu 10.04) but have the sound come from an xp machine on the network. ATM I am VNCing to a windows machine to change tracks which is a little annoying everytime.

---

### Post by Kai Summers on 2010-05-04
SOLVED: I have just found a solution that looks like it should work pulseaudio.org. From what I read it should do exactly what I want, as it has been ported for windows. Thank you greatly anyway!!

---

