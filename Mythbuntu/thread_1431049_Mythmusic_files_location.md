---
title: "Mythmusic files location"
date: 2010-03-16
forum: Mythbuntu
---

### Post by AlecJ on 2010-03-16
Hi I'm having a problem with mythmusic with keeps dumping me back to the desktop.

As soon as I enter the music menu there is much hard disk activity and myth becomes un-responsive, If I do manage to get as far as scan for new music, it appears to start scanning and the light in the USB drive starts to flash activity, but soon stops responding or sit's there "scanning" over night with no effect.

I have removed and re-installed mythmusic with no effect, but I notice the settings stay during the re-install. So I would like to know where to find these files.

It is important to know that this was working fine untill I tried to change the display from artist to albums. I have sice changed this back but no joy.

I have updated myth to daily rebuilds in an attempt to fix, but with no effect.

Thanks in advance.

---

### Post by nickrout on 2010-03-16
Are you on trunk or 0.22-fixes?

Not sure what you mean by the 'location of the files' - if you are looking for the settings, they are in the database. The place where myth will look for the music files is in the settings table.

```
select * from settings where value like '%musiclocation%';
```

---

### Post by AlecJ on 2010-03-17
Hi was on 0.22-fixes, now on trunk as a bid to fix problem.

I was hoping that was not the case, but it makes sense as these fields would not be erased on removal of mythmusic, I've checked these from mythweb, there correct.

I'm wondering weather to re-install the whole frontend as the backend, via mythweb, shows the music files and I can build a playlist? I realize this is a very windows approach but I have run out of ideas.

---

### Post by kja999 on 2010-03-17
Hi,

Have you run mythfrontend from a terminal and seen what the activity is before it goes wrong ?

---

### Post by AlecJ on 2010-03-17
No. thats a good idea, I will try that

thanks

---

### Post by nickrout on 2010-03-18
> **kja999 said:**
> Hi,

Have you run mythfrontend from a terminal and seen what the activity is before it goes wrong ?

Why not simply watch the log file. My favourite method is to sit in front of the mythbox with a laptop. ssh into the frontend and run ```
tail -f /var/log/mythtv/mythfrontend.log
```

---

