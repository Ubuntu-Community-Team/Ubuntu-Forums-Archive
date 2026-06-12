---
title: "missing catalyst control center + sluggish unity"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by xgt001 on 2011-04-17
hey everyone!!!
i just installed natty beta 2 and i liked it very much but i still have some major and minor irritants :(
i have a slow net connection.. i manually downloaded the latest ati proprietary drivers from ubuntu site and installed it successfully..(gdebi installed the missing dependencies) i also installed the fgrlx-ccle package 
BUT
1) unity is VERY sluggish in prop drivers..(classic desktop runs fine)... i tried turning of the sync to vblank in compiz config but no avail
2) i cant find the catalyst control center anywhere even though it shows as properly installed.. i tried terminal too but no avail :(

any ideas/solutions??

---

### Post by ranch hand on 2011-04-17
Did you use "amdcccle" to call Catalyst in your terminal.  If not you may want to try that.

I think it should be working now.  It is in Debian testing using the 26.38 kernel.

---

### Post by xgt001 on 2011-04-22
now its fixed!!!!! \\:D/

a) I removed the installed drivers through jockey , restarted ubuntu , then i installed the downloaded driver deb files again, restarted, THEN i went to jockey where i selected the proprietary drivers, it activated the installed drivers and then upon reboot i got catalyst control center :D

b) to get rid off the unity slowness in compizconfig i un-selected "sync to vblank" in opengl :) 

now unity is rocking :D

---

### Post by screaminj3sus on 2011-04-22
install ccsm and turn off sync to vblank should fix slow compiz with fglrx.

EDIT: NVM for some reason your post didn't load when I first opened this thread lol.

They really need to turn sync to vblank off by default.. It doesn't even work on most card and causes issues.

---

