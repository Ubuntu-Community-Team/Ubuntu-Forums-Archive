---
title: "Transferring video off linux"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by TomFumb on 2007-02-15
Hi, I think this should be a relatively simple question, so hopefully someone can help me out - 

I have xubuntu on my very small thinkpad, which I often take into the computer lab at uni (some idiot there forgot to a: use mac address access control on the network, and b: firewall bittorrent ports...). 

I can download videos and music and play them fine on the linux laptop, but when I try and transfer them to my xbmc-enabled xbox over the network, somewhere along the way the files either get corrupted or the file system gets screwy or something. 

I can't play the files on the xbox, and if I pull them off the xbox onto my xp computer they're still all messed up. 

Is this simply a file system incompatibility problem?
Is there anything I can do to make files 'exportable'?
Is it just a feature of moving stuff to my xbox? (so far I haven't managed to give my linux laptop a shared folder, so I can't just pull stuff straight off there).

Any help with this would be greatly appreciated

tomfumb

---

### Post by Yoooder on 2007-02-15
Hmm, answer a couple questions for me:

If you transfer the files straight to your XP machine do they play alright?

What about transferring them to the XBox then back to your Linux box?

---

### Post by TomFumb on 2007-02-16
Hi, thanks for your interest

from xp I can play files fine over the network
from the xbox I can play files fine over the network
if I transfer an mp3 to the xbox, then transfer it back to linux, it plays fine,

but when I try to play on the xbox from the xbox drive, it's all screwed up

Now that I know I can access shared files on linux from xp I suppose this is no longer a linux forum question, and more of an xbmc issue, but it would still be good to know if anyone has any ideas  -  what goes wrong when I transfer from xubuntu to xbox???

---

### Post by fallscrape on 2007-02-16
It's the special linux DRM! = )

Only joking... I've got the same problem I think - I copied across a 2.8GB movie file using FTP from my ubuntu box (6.10) to my xbox and it plays parts and crashes.  I've tried transferring it a few times and the same thing happens.  Plays fine on the ubuntu box though.  Might be a codec issue if it plays fine in VLC.

---

### Post by fallscrape on 2007-03-02
I have recently tried transferring files from ubuntu PC to my xbox via GFTP.  They get corrupted unfortunately and I have no idea why.

Copying them onto a thumbstick and accessing them on XP works fine.  Is there a specific setting in GFTP that might be causing this?

---

### Post by TomFumb on 2007-03-04
Hi, I have no idea why, but I can now upload files to my xbox via GFTP with no problems. I'm using the default setup in GFTP, so I can't help you with the settings. 
The only thing I've changed in xubuntu since having this problem is installing fuse, but I don't think that should've had any effect on my initial problem. 

I don't run an ftp server on xp so I don't know if I can transfer straight to xp from xubuntu, but if it works on the xbox I see no reason why it wouldn't now work on xp

---

