---
title: "DVDs won't play, even after following instructions."
date: 2011-01-27
forum: Multimedia Software
---

### Post by windyweather on 2011-01-27
Just built a new mini-ITX system. Installed 10.04 x64 and then spiffed it up. Now to play DVDs, I followed instructions here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Including the troubleshooting item about chmod / chgrp. I wasn't clear whether this would be saved across reboots. And rebooted.

```
xxx@atomic-breeze:~$ sudo chmod 660 /dev/sr0
xxx@atomic-breeze:~$ sudo chgrp cdrom /dev/sr0
xxx@atomic-breeze:~$ 
```


Unprotected DVDs play just fine. Protected ones give this error:
[IMG]http://www.windyweather.net/wp/wp-content/uploads/2011/01/DVD_Play_MoviePlayer_Error.png[/IMG]

Any ideas why I can't play protected DVDs?
Any other ideas about what to try?

Thanks,
Windy

---

### Post by ajs1980 on 2011-01-28
If its any consolation I'm having the same problem. though its not all my dvds so far just the seasons of futurama and american dad everything else plays fine. how many dvds have you tried? It may be one difficult dvd.

---

### Post by windyweather on 2011-01-28
I wondered whether the problem was the region code, since I purchased the laptop sata drive as "refurbished". Here is the output from regionset.

```
l@atomic-breeze:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!
darrell@atomic-breeze:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:


```

Looks like it's set for no region. I set it to region 1 and so now I'll see what happens.

- windy

---

### Post by windyweather on 2011-01-28
:popcorn:

Looks like you need to set the region code!! :guitar:

Here's a little list of DVDs and the results:
[LIST]
[*]ok Lake Placid
[*]failed Ultraviolet - very odd. Lots of noise, but some frames came through.
[*]ok Solaris 2002
[*]ok Matrix 1999
[*]ok Basic Instinct Direct Cut 1992
[/LIST]

I'm using gxine 0.5.904, which plays with menus. Movie player gives errors on some disks.

- Whoopee...  :lolflag:

- windy

---

### Post by BicyclerBoy on 2011-01-28
If you need to regionset then the libdvdcss is not installed correctly.

I suggest you rerun the script & study the output..

---

