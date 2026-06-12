---
title: "People with unrecognized radeon cards..."
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by SilverTab on 2005-10-15
I know at least 2 other people in here that had the same problem as I have with the ATI Radeon 9550 (maybe 9600 too)  and breezy/kernel 2.6.12

I got this reply from the Rage3D forum:

> 
I have exactly the same problem as you since Kernel 2.6.12. The previous kernel 2.6 was fine. The way I fix it is by assigning MTRR manually and reload fglrx through a script just before the X start.


Apparently this solved the issues with the Radeon 9550 not being recognized by the kernel
( 0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173)

Now I have no idea how to do that myself (hehe) but I hope this can help anyone fixing the issue! :)

---

### Post by mlomker on 2005-10-15
> Now I have no idea how to do that myself (hehe) but I hope this can help anyone fixing the issue! :)

Apparently [these are the commands]("http://www.rage3d.com/board/showthread.php?t=33810638").  If you figured out the correct memory start/end points then you could add it toward the end of the /etc/init.d/bootmisc.sh file.

I don't know what MTRR does, though.

---

### Post by SilverTab on 2005-10-15
[QUOTE=mlomker]Apparently [these are the commands]("http://www.rage3d.com/board/showpost.php?p=1333615107&postcount=2") for a card with 128 MB of RAM.  You could try adding them toward the end of your /etc/init.d/bootmisc.sh file and see if it makes a difference.[/QUOTE]


I have a Sapphire Radeon 9550 (256mb)...Bought it for cheap on eBay...so i'm not sure if these commands would work (considering you mention 128ram...and I have 256)...

I know that in hoary the card was recognized as a radeon 9550 with 256mb...just like it should...

---

### Post by mlomker on 2005-10-15
> I know that in hoary the card was recognized as a radeon 9550 with 256mb...just like it should...

Have you searched for bug reports or filed one?  The Bugzilla link is at the top of every page.

---

### Post by SilverTab on 2005-10-15
[QUOTE=mlomker]Have you searched for bug reports or filed one?  The Bugzilla link is at the top of every page.[/QUOTE]


I searched bugzilla for "9550" and nothing came up....

I thought about filing one but decided to wait to get more feedback from the ATI forum first...

---

