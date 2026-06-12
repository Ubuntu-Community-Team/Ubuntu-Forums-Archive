---
title: "[Solved] Unable to print files via samba or lpd"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by poltr1 on 2012-03-26
I have two systems in my home network -- my Ubuntu desktop ("orac") and my daughter's Windows XP desktop ("zen").  I have an HP LasertJet 4MP connected to zen.  I've been trying to print files to the LaserJet from orac.  It can find the printer when I search for it, but I had problems authenticating.  I had to enter my user ID and password for zen every time I printed.  While that worked, it was a hassle.  And some times, it didn't work at all, keeping my printouts in limbo.

I tried to recreate the print queue, but it still wouldn't verify the connection.  After searching online for similar problems, I noticed that the spaces in the queue name on zen -- "HP LaserJet 4MP" -- weren't properly getting translated by Samba on orac -- HP20LaserJet204P.  It somehow dropped the % characters I needed to properly escape the spaces.  So I brought up cups via [http://localhost:631](http://localhost:631), examined the print queue, and edited the smb:// string to add the % signs and properly escape the spaces.  I then printed a test page, and lo and behold, it worked!

So, a word of caution if your print queue has spaces in it.  Either change the queue name to remove the spaces, or go into cups to fix the address.  (I'm running Samba 3.5.8 and Natty on orac.)

---

