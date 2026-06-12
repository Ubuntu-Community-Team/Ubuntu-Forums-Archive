---
title: "Hard disk doesn't connect any more"
date: 2014-09-07
forum: Multimedia Software
---

### Post by urkaim on 2014-09-07
Good afternoon every one. As the title said I've experienced a problem whith my 500 gb toshiba hard disk. 
After been disconnected, I've tried to connect it again and that message came out: 
[B]
Sorry, could not display all the contents of “TOSHIBA EXT”: Error when getting information for file '/media/urkaim/TOSHIBA EXT/found.000': Input/output error [/B]

So I've been exploring the web trying to find out if the ubuntu comunity had the solution for me. 
I've foud a topic that said to use this command sudo fdisk -l but them that screen came out:

[ATTACH=CONFIG]256230[/ATTACH]

Have you got any suggestion for me? I have the files inside as I can see them (I've tried several free programs) but I cannot restore them as I would need to buy for 40 or 50 euros the full program. 
Thank you very much
Simone

---

### Post by mooreted on 2014-09-07
Gparted has a function to repair file systems or if you are comfortable with the command line you can use fsck:

[http://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](http://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

You can install gparted from the Ubuntu Software Center or the command line.

---

