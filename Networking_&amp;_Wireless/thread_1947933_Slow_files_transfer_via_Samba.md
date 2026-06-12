---
title: "Slow files transfer via Samba"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by wampirek on 2012-03-27
Hello 

I've got 2 computers at home. One has Ubuntu 11.10 installed, another one has Win7. 
Ubintu is connected with wire to Linksys WRT160NL router (N, 300Mb/s), Win7 is connected via wireless card (full N speed - 300Mb/s). 

In Ubu I created a bookmark smb://192.168.1.4/media/ to get access to Win folder "media" - it's enough to click it and Nautilus opens the folder. 
When I copy files (working on Ubu) from Ubu to Win, the speed is around 2,8-2,9MB/s (that's what Nautilus shows). Kind of slow for me, but I thought - OK, let it be, maybe it should be like this. 

But today I had to work from Win station. I wanted to copy some files, so added network drive \\192.168.1.2\pliki Then I picked some files and started to copy them and the speed was TWICE faster then before - I got 6,5MB/s (that's what Win files manager showed). 

Files wre approximately the same size (1 file around 500MB) so it's not the problem with thousands small files being copied. For sure it's not hardware problem because it would be the same in both directions. 
So i think it might be something with Samba settings, but I have no idea what it could be. I haven't configured anything manually, everything was done automaticaly by the system.  

If anyone had similar issue and managed to solve it or just has some good idea how to solve mine - please help.

---

### Post by kid1000002000 on 2012-06-21
Same issues. There's a bug filed [here]("https://bugzilla.samba.org/show_bug.cgi?id=7699") but it doesn't look like much has been done recently on the problem. If anyone has suggestions for this I'd be curious.

This is also pertinent: [http://www.overclockers.com/forums/showthread.php?t=683188](http://www.overclockers.com/forums/showthread.php?t=683188)

---

