---
title: "New install, AMD E-Series (APU) and other dilema's"
date: 2011-03-23
forum: Mythbuntu
---

### Post by beardos on 2011-03-23
Morning All.
I've finally decided to dip my feet into the wonderful world of Linux based Media centre's and after some careful consideration I bought the following components:
-Asus AMD E350 PRO motherboard (new APU system with dual core and graphics integrated onto chip)
- 4 GB DDR3 RAM
- 1x OCZ Vertex 2 60GB SSD HDD
- 1x 3 TB HDD (SATA 3 flavour)
- 1x DVD (Mostly for install and ripping my DVD's)

I know that going with an AMD based CPU is risky as the drivers are not as good as Nvidia's for linux but it seems (on my first test run anyway) that it runs fine. However, there is a graphic overlay saying "Graphics card not supported" in the bottom right hand corner (Even though the restricted driver install process saw it as an AMD graphics chip, weird). How often do they update there drivers (Monthly?).
My second part of my question is how to change partitioned drives from having the owner as Root only (Can't write to drive's even though I'm loggin in with the only account that I created which I was under the impression would be the root owner).

Anywho, even though I'm fairly computer savvy, I know my linux skills are not quite up to scratch (even though I have it installed on an old lap top for 2 years or so, I've never really done too much with it other than use it as a web browser).

I'm looking forward to this new linux media future with great excitement and any advice would be greatly appreciated)

PS (SSD Drive partitions in to /root(20GB), /tmp(10GB), /swap(4GB), /home(20GB) and /personal(9GB)
2nd HDD has /music(300GB), /video(2.7TB), /personal(20GB) (All partitions apart from swap are EXT4)
would I have to run gparted as sudo in terminal? Unfortunately I'm at work so can't solve my own query but would really like to know for when I et back so I can get a move on with it all.

Cheers in advance

---

### Post by jmeads on 2011-03-23
> **beardos said:**
> 
My second part of my question is how to change partitioned drives from having the owner as Root only (Can't write to drive's even though I'm loggin in with the only account that I created which I was under the impression would be the root owner).


I assume you've mounted the filesystems - you just need to change the owner of the mount point once mounted, eg assume mounted under /media/partition, then

sudo chown useraccount  /media/partition

If you want to change the owner of all the files/directories too, then

sudo chown -r useraccount  /media/partition

where useraccount is the account you created, you can found out more about chown using man, eg

man chown

---

