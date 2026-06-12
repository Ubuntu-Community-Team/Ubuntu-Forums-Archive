---
title: "Daily iso + zsync"
date: 2010-08-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-08-20
I've using zsync to update the daily image for the last week or so, how do you tell if the image has been updated, aside from paying attention while doing the update. My iso is still dated 2010-08-12 13:25, even though it has been updated several time.

---

### Post by kansasnoob on 2010-08-20
Where do you see the iso date?

I just did mine this AM:

[ATTACH]167043[/ATTACH]

How I zsync:

1) cd my Download directory (your iso may be in a different directory)
2) zsync + copy zsync link location from daily page
3) check md5sum (even though it's done automatically)

Example:

```
lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ zsync http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso.zsync
#################### 100.0% 297.5 kBps DONE     

reading seed file maverick-desktop-i386.iso: ***********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read maverick-desktop-i386.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 769069056 local, fetched 0
lance@lance-desktop:~/Downloads$ md5sum maverick-desktop-i386.iso
e0dc7efebe9e4975ab475e53859ad66f  maverick-desktop-i386.iso
lance@lance-desktop:~/Downloads$ 

```

---

### Post by ronacc on 2010-08-20
start a terminal in the directory where the iso is and run

```
zsync http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync
```  

adjust that if you are i386 .

I zsync'd this AM and my iso date is  today .

@ kansasnoob  in nautilus rt click on the iso and select properties , that will show the date and time it was modified .

---

### Post by cariboo on 2010-08-20
I do the zsync in a terminal, using nautilus I get this:

[IMG]http://imgur.com/tL7TTl.jpg[/IMG]

---

### Post by cariboo on 2010-08-20
I just ran zsync again copying and pasting from ronacc's post, and the date on the image was updated. 

What I did was create an executeable file, and just run it. 

Now that I had a look at the script, I see it's pointing to the wrong location, the actual iso that was updated does have the correct date.

I guess I should quit multitasking, trying to do several things at once, and pay attention to what I'm doing. :lolflag:

I'll mark this thread solved.

---

### Post by ronacc on 2010-08-20
I always create a separate directory for the Iso I am going to use for zsyncing and run my script from a terminal started in that directory, to avoid possible confusion with other iso's I may have d/l'd directly .

---

### Post by cariboo on 2010-08-20
That's what I've done, my script was pointing to the download directory, where it should have pointed to the iso directory.

---

### Post by VMC on 2010-08-20
I use my ".bash_aliases" a lot. Here is my zsync part of that file:

```
alias MAV='zsync -i /media/NTFS/maverick-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-amd64.iso.zsync'
alias MAV32='zsync -i /media/NTFS/maverick-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso.zsync'
alias LUC='zsync -i /media/NTFS/lucid-desktop-amd64.iso http://cdimage.ubuntu.com/lucid/daily-live/current/lucid-desktop-amd64.iso.zsync'
alias LUC32='zsync -i /media/NTFS/lucid-desktop-i386.iso http://cdimage.ubuntu.com/lucid/daily-live/current/lucid-desktop-i386.iso.zsync'
alias KUB='zsync -i /media/NTFS/kubuntu-lucid-desktop-amd64.iso -o kubuntu-lucid-desktop-amd64.iso http://cdimage.ubuntu.com/kubuntu/lucid/daily-live/current/lucid-desktop-amd64.iso.zsync'
```

All my previous zsync'ed ISO's redies on a partition named NTFS. Then after loggin into that partition , from my home partition and a terminal I type either MAV, LUC32, etc. Once I determine that the md5sums match I move them to NTFS. I usually save the older ISO's somewhere's else. I have lost to many ISO's by over writing them.

Case in point. You'll notice that KUB for Kubuntu once written into my home directory takes on the same name of Ubuntu's. That's why I use the *-o output* file option. To rename it to kubuntu so ubuntu doesn't get over written or visa-versa.

---

