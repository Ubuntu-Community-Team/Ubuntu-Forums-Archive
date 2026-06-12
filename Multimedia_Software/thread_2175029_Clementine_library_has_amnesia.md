---
title: "Clementine library has amnesia"
date: 2013-09-17
forum: Multimedia Software
---

### Post by huxley2 on 2013-09-17
Hi, everybody

Everytime I restart ubuntu the clementine library is empty and won't recognise the music folder so I have to delete and re-add it. My music files are stored in Data Disk - storage partition HPFS/NTFS -  and my ubuntu also has its own partition seperate from the windows drive. Both Date Disk and Ubuntu partitions are set to automatic mount.

It's only a slight convenience to have to re-add the music folder each time but it would be nice if I didn't have to so any top tips would be much appreciated.

Regards

Huxley

---

### Post by speartip on 2013-09-17
Just a thought, it may have something to do with permissions & ownership.
After I created a partition that I called "storage" & added the uuid to fstab to mount it, I then had to run this:
```
sudo chown -R username:username /storage
```
and then:
```
[SIZE=2][COLOR=#000000][FONT=DejaVu Sans]sudo chmod -R 755 /storage[/FONT][/COLOR][/SIZE]
```
then reboot.
Obviously you will need to change "username" for your own username & "storage" for whatever you have called your partition.
I can't find the tutorial I got this from, but it has always worked for me, & my Clementine Library has always worked correctly.
Hope this helps.

ps my storage partition is ext4 though not NTFS, Whether that is relevant or not i'm not sure.

---

### Post by huxley2 on 2013-09-18
Thanks for the reply, Speartip.

I had a good look into uuid's and after about an hour's research I came to the dual conclusion that what you say makes good sense and that I have no idea how to go about making it happen. 

I'm still only into my 2nd week of ubuntu / linux coding and during initial set-up I unknowingly mangaged to prevent both windows and ubuntu partitions from booting. Luckily I still had ubuntu on my memory stick so was able to start up through that and eventually rectify the situation but I think it's wise for me to stay well away from anything to do with partition changes for the time being.

I've bookmarked this page and will attempt to make the changes in a month or so when I'm a bit more competent - I'm keen to learn more about computers but no point getting ahead of myself - until then I'll be content with having to reload my music library after every start up...

Thanks, again

Huxley

---

### Post by Yellow Pasque on 2013-09-18
How are you "automounting" the NTFS partition? Do you have a line in /etc/fstab file? (If so, maybe you could share it here.)

---

### Post by huxley2 on 2013-09-19
Hi, Temujin

Against my better judgement I looked into /etc/fstab - [http://ubuntuforums.org/showthread.php?t=2175332](http://ubuntuforums.org/showthread.php?t=2175332) - and about the only good thing to come out of it was realising just how inept I am at this sort of thing.

 I almost certain the solution lies in formating the data drive to ext4 and addding the uuid to /etc/fstab. The posts in the above thread would be more than helpful to anyone with half a clue but each time I try it it ends in a nose bleed.

If I decide to have another stab at it in the future and succeed I'll post the results, for sure

Hux

---

### Post by Yellow Pasque on 2013-09-19
> I almost certain the solution lies in formating the data drive to ext4 and addding the uuid to /etc/fstab. 
Yes, but then Windows won't read it..

---

### Post by huxley2 on 2013-09-19
In that case I'll definitely leave things how they are. Thanks for the info, Temujin

---

### Post by huxley2 on 2013-09-20
Sorted.

Turned out all I needed to do was configure the partition using ntfs configuration tool

---

