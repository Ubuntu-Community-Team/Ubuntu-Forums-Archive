---
title: "Annoying DVD problem using VLC or Internal"
date: 2008-06-05
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-06-05
I was using xine before upgrading to 8.04 but that stopped working (I think I need to recreate my symlink or something like that) and so I changed it to use internal.  It seems the internal player has been improved with the upgrade (it didn't use to work at all for me with 7.10).  

However, my actual problem follows. On several DVDs the movie just quits and it exits back to mythfrontend.  When it does this it always happens at the same time.  It'll be at a different time for a different DVD but it's consistent for each DVD when this happens.

I tried watching the DVDs with VLC and the same thing would happen with VLC too.  I've even tried watching those DVDs with VLC on a Windows machine and it still happens.  On a set top player the movies play all the way through.

This seems to be specific to VLC and the myth internal player.  I don't remember this ever happening with xine before I upgraded.  Anyway, has this ever happened to anyone else?  And is there a reason why?

---

### Post by uopjohnson on 2008-06-06
My bet is copy protection.  There are lots of new DVDs that I can't play in myth.  Hopefully some fixes will get made upstream to libdvdcss or realted to solve this problem.

---

### Post by nasha on 2008-06-07
Check your MythTV logs after the crash :)
They will tell you exactly why it crashed no doubt

---

### Post by Trollslayer on 2008-06-09
> **uopjohnson said:**
> My bet is copy protection.  There are lots of new DVDs that I can't play in myth.  Hopefully some fixes will get made upstream to libdvdcss or realted to solve this problem.

I think it would take a firmware change to the DVD drive, hope not though.

---

### Post by uopjohnson on 2008-06-09
I doon't think it would take a firmware change.  I don't have any dual boot machines anymore, but I bet if you booted into windows the same DVD would play (assuming you have DVD playing software for windows PowerDVD or whatever they call it). Any chagnes to the actual drive would imply that the DVD no longer plays in stand alone DVD players, which doesn't seem to be the case.

---

### Post by Meph1st0 on 2008-06-12
Actually, uopjohnson, you're right. If I play the dvd through Cyberlink PowerDVD in Windows it plays through without a problem.  However, if I play it through VLC in Windows it will crash.  So it's almost definitely a VLC specific problem despite the OS that it's running in.

---

### Post by Mister.Vash on 2008-06-12
Start vlc from a terminal session.  That way you can see if vlc throws an error when it crashes.

---

