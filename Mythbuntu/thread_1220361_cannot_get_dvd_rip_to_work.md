---
title: "cannot get dvd rip to work"
date: 2009-07-22
forum: Mythbuntu
---

### Post by Troy Pearce on 2009-07-22
Hello all,

Totally brand new to ubuntu and linux in general.

I have installed mythbuntu and everything appeared good.

tried to rip a dvd and goes for a bit (10 mn or so) then poops out.

been searching for all the help I can get through the forums but have problems trying to follow the directions as i am nooby.

I have figured that any helpers need to know something about my system.

my hardware
      Motherboard ASUSTeK Computer INC. A7V266-C
    ASUS A7V266-C ACPI BIOS Rev 1013
AMD Athlon(TM) XP2400+
DVD PLEXTOR DVDR   PX-504A
op sys 
mythbuntu jaunty
hauppage 500

and i have also through the forums figured that the mtd log might be helpfull.

I have tried to rip both a production dvd mary poppins 
and a home copied dvd toy story
both play in the player

the mtd log

mtd started at Wed Jul 22 09:33:52 2009
mtd is running on a host called troy-tvpvresktop
09:33:52: Waiting for connections/jobs
09:33:52: mtd is listening on port 2442
09:33:58: DVD inserted: TOY1
09:33:58:             : Title 1 is of type 2 (dvdinput table)
09:33:58:             : Title 2 is of type 4 (dvdinput table)
09:33:58:             : Title 3 is of type 4 (dvdinput table)
09:33:58:             : Title 4 is of type 4 (dvdinput table)
09:33:58:             : Title 5 is of type 2 (dvdinput table)
09:33:58:             : Title 6 is of type 0 (dvdinput table)
09:33:58:             : Title 7 is of type 0 (dvdinput table)
09:33:58:             : Title 8 is of type 2 (dvdinput table)
09:33:58:             : Title 9 is of type 2 (dvdinput table)
09:33:58:             : Title 10 is of type 4 (dvdinput table)
10:11:52: DVD removed
10:12:55: DVD inserted: TOY1
10:12:55:             : Title 1 is of type 2 (dvdinput table)
10:12:55:             : Title 2 is of type 4 (dvdinput table)
10:12:55:             : Title 3 is of type 4 (dvdinput table)
10:12:55:             : Title 4 is of type 4 (dvdinput table)
10:12:55:             : Title 5 is of type 2 (dvdinput table)
10:12:55:             : Title 6 is of type 0 (dvdinput table)
10:12:55:             : Title 7 is of type 0 (dvdinput table)
10:12:55:             : Title 8 is of type 2 (dvdinput table)
10:12:55:             : Title 9 is of type 2 (dvdinput table)
10:12:55:             : Title 10 is of type 4 (dvdinput table)
10:13:21: DVD removed
10:14:39: DVD inserted: TOY1
10:14:39:             : Title 1 is of type 2 (dvdinput table)
10:14:39:             : Title 2 is of type 4 (dvdinput table)
10:14:39:             : Title 3 is of type 4 (dvdinput table)
10:14:39:             : Title 4 is of type 4 (dvdinput table)
10:14:39:             : Title 5 is of type 2 (dvdinput table)
10:14:39:             : Title 6 is of type 0 (dvdinput table)
10:14:39:             : Title 7 is of type 0 (dvdinput table)
10:14:39:             : Title 8 is of type 2 (dvdinput table)
10:14:39:             : Title 9 is of type 2 (dvdinput table)
10:14:39:             : Title 10 is of type 4 (dvdinput table)
10:19:45: a client socket has been opened
10:19:53: DVD removed
10:19:54: DVD inserted: TOY1
10:19:54:             : Title 1 is of type 2 (dvdinput table)
10:19:54:             : Title 2 is of type 4 (dvdinput table)
10:19:54:             : Title 3 is of type 4 (dvdinput table)
10:19:54:             : Title 4 is of type 4 (dvdinput table)
10:19:54:             : Title 5 is of type 2 (dvdinput table)
10:19:54:             : Title 6 is of type 0 (dvdinput table)
10:19:54:             : Title 7 is of type 0 (dvdinput table)
10:19:54:             : Title 8 is of type 2 (dvdinput table)
10:19:54:             : Title 9 is of type 2 (dvdinput table)
10:19:54:             : Title 10 is of type 4 (dvdinput table)
10:20:50: launching job: job dvd 1 1 -1 0 -1 /var/lib/mythtv/videos/TOY1
10:20:50: Using DVD source: /dev/scd0
10:20:50: ISO DVD image copy to: /var/lib/mythtv/videos/TOY1_001of
10:21:03: Final file name is not useable. File exists? Other Pending job?
10:32:43: Error: DVDISOCopyThread dvd device read error
10:32:45: job failed: job dvd 1 1 -1 0 -1 /var/lib/mythtv/videos/TOY1
10:51:34: a client socket has been closed
11:21:14: a client socket has been opened
11:21:27: launching job: job dvd 1 1 0 0 -1 /var/lib/mythtv/videos/TOY1
11:21:27: job thread beginning to rip dvd title
11:31:57: Error: DVDPerfectThread read failed for 298 blocks at 1432910
11:31:57: job failed: job dvd 1 1 0 0 -1 /var/lib/mythtv/videos/TOY1
12:29:28: a client socket has been closed
12:31:41: DVD removed
12:32:18: DVD inserted: POPPINS
12:32:18:             : Title 1 is of type 0 (dvdinput table)
12:32:18:             : Title 2 is of type 4 (dvdinput table)
12:32:18:             : Title 3 is of type 4 (dvdinput table)
12:32:18:             : Title 4 is of type 4 (dvdinput table)
12:32:18:             : Title 5 is of type 4 (dvdinput table)
12:32:18:             : Title 6 is of type 4 (dvdinput table)
12:32:18:             : Title 7 is of type 4 (dvdinput table)
12:32:18:             : Title 8 is of type 4 (dvdinput table)
12:32:28: a client socket has been opened
12:32:49: launching job: job dvd 1 1 0 0 -1 /var/lib/mythtv/videos/POPPINS
12:32:49: job thread beginning to rip dvd title
12:39:45: Error: DVDPerfectThread read failed for 121 blocks at 1140258
12:39:45: job failed: job dvd 1 1 0 0 -1 /var/lib/mythtv/videos/POPPINS
13:31:41: a client socket has been closed
13:33:31: a client socket has been opened
13:33:40: launching job: job dvd 1 1 -1 0 -1 /var/lib/mythtv/videos/POPPINS
13:33:40: Using DVD source: /dev/scd0
13:33:40: ISO DVD image copy to: /var/lib/mythtv/videos/POPPINS_001of
13:45:20: Error: DVDISOCopyThread dvd device read error
13:45:21: job failed: job dvd 1 1 -1 0 -1 /var/lib/mythtv/videos/POPPINS
13:51:29: a client socket has been closed

I tried each of these in both perfect and iso image with different errors for each


any suggestions..... please be very specific as I dont know many commands and am very unfamilular with linux but hope to learn

Thanks for any help you can lend



Troy

---

### Post by Nobodyspeshul on 2009-07-24
I had this same problem and ended up resorting to a third party software to decode and rip my DVD's.

[www.slysoft.com](www.slysoft.com) get AnyDVD and CloneDVD Mobile (if you want different encodings)

I burn those on my windows box, then transfer them over to my mythbox with winscp.

Hope this helps.

---

### Post by David Grigor on 2009-07-24
In your logs Toy / Poppins sound like they could be Disney DVDs. They are harder to copy. Likely the reason. If you have an older non-Disney to try and see what happens.

k9copy works pretty well but that too has trouble with some particularly Disney.

---

### Post by cgb on 2009-07-24
For troublesome discs, although old and must be run through wine, Dvd Decrypter is pretty reliable.

---

### Post by stinger30au on 2009-07-24
> **Troy Pearce said:**
> 
13:33:40: ISO DVD image copy to: /var/lib/mythtv/videos/POPPINS_001of
13:45:20: Error: DVDISOCopyThread dvd device read error


Troy


Troy,

mate this error says it has a read error

try giving the disc a good clean

do you have another dvd drive kicking round somewhere so you can replace the current one with and try again?

k9copy i have found will copy anything you throw at it

---

