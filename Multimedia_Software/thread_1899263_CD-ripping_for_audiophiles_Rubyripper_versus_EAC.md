---
title: "CD-ripping for audiophiles: Rubyripper versus EAC"
date: 2011-12-23
forum: Multimedia Software
---

### Post by DutchDude on 2011-12-23
Unfortunately I learned the hard way that even though .flac is a lossless format, the process needed to create a .flac file is no necessarily lossless as well. So I lost a few days making backups of my CD collection, using the standard SoundJuicer application before I found out that a number of the resulting .flac files were damaged. 

Anyway, I looked for alternatives and two applications that are frequently suggested on the internet are Rubyripper and Exact Audio Copy (EAC). EAC is a Windows application ([with a bug under Wine]("http://bugs.winehq.org/show_bug.cgi?id=25340")). I liked the results with Rubyripper that I have heard, but, as I want to backup a large CD collection, I really want to be sure that I'm not loosing data and sound quality.

Does anybody know if EAC and Rubyripper produce different quality .flac files? And if so, is any of them better than the other?

---

### Post by shantiq on 2011-12-23
well both are good but for extreme quality copy EAC is still better
apparently RR does not go to the same level of depth in comparing both rips [they rip twice and check both rips are identical]


there is no bug with EAC on Ubuntu if you use a version like [**0.99**]("http://www.exactaudiocopy.de/en/index.php/resources/download/older-versions-for-download/")



as regards RR which l love to use too here are [**lossless coding **]("http://ubuntuforums.org/showpost.php?p=9630448&postcount=26")for other line in setup


a tip for RR


use from command line    enter


```
rrip_gui
```    and set your choices


then enter ```
rrip_cli
```   and follow easy instructions



if you do it all from gui it might go pear-shaped:KS


to sum up     EAC slightly better; but RR is linux

---

### Post by Silverflyer on 2011-12-23
Are you saying that I can run EAC on Linux if I use ver. .99?

---

### Post by shantiq on 2011-12-23
> **Silverflyer said:**
> Are you saying that I can run EAC on Linux if I use ver. .99?


yes install Wine [in your synaptic]first then install EAC under Wine. 

1. download 0.99 right-click on it make executable
2. right click again choose install with Wine. Follow instructions...


  works perfect


More recent versions do not seem to install [on my system at least; maybe others have managed it]

---

### Post by DutchDude on 2011-12-26
@shantiq

I'm running version 0.99 of EAC under Ubuntu/Wine and I ripped the first CD with it! :)

Thanks for your advice! :) :)

---

