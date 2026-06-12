---
title: "Creating ISO image from CD"
date: 2009-09-15
forum: Multimedia Software
---

### Post by capinlarry on 2009-09-15
After I insert the CD I right click, tell it to Copy Disc. Then I tell it to create an ISO image. It starts then always freezes after it gets to 3MiB. I prefer to use GUI (i always forget the terminal commands) but any help is appreciated.
 
Thanks

---

### Post by joshuachad on 2009-09-15
Not sure what program you are using or why it is happening. First what program? 

If you want a gui to copy a CD try k3b. That one works best for me. to install type *sudo apt-get install k3b* in a terminal. If you want a program to create an iso from cd TRY acetoneiso. It is a gui and you can find it here [http://www.getdeb.net/release.php?id=4721](http://www.getdeb.net/release.php?id=4721)

---

### Post by Ganymedes on 2009-09-15
I do know why it freezes, but if you want to try another method, here we go.

Maybe if you know what a command is doing, it would be easier to remember it ... just a thought ... in Linux you do not really "create an Iso image" per se ... cd IS ALREADY an ISO image. You just need to "dump" the image elsewhere.

You can use disk dump (dd) for getting the iso image from cd to your disk. So:

dd if=/dev/sr0 of=somename.iso

"if" is for input file and "of" is for output file. The trick there is to know what device your cd/dvd is. You can do it easily by having the cd in the bay and giving a command "df", which displays all your disks. There you might see "/dev/sr0" or something else for you cd/dvd.

So, this works basically the same for cd and dvd. You only need to "remember" that the concept of "dumping disks" exists in Linux (/in Unix already).

---

### Post by capinlarry on 2009-09-15
> **Ganymedes said:**
> I do know why it freezes, but if you want to try another method, here we go.

Maybe if you know what a command is doing, it would be easier to remember it ... just a thought ... in Linux you do not really "create an Iso image" per se ... cd IS ALREADY an ISO image. You just need to "dump" the image elsewhere.

You can use disk dump (dd) for getting the iso image from cd to your disk. So:

dd if=/dev/sr0 of=somename.iso

"if" is for input file and "of" is for output file. The trick there is to know what device your cd/dvd is. You can do it easily by having the cd in the bay and giving a command "df", which displays all your disks. There you might see "/dev/sr0" or something else for you cd/dvd.

So, this works basically the same for cd and dvd. You only need to "remember" that the concept of "dumping disks" exists in Linux (/in Unix already).

i get the following:

 dd: reading `/dev/sr1': Input/output error
6624+0 records in
6624+0 records out
3391488 bytes (3.4 MB) copied, 0.0910701 s, 37.2 MB/s

i was using brasero disc burner but it always froze at 3MiB

---

### Post by capinlarry on 2009-09-15
sorry, i should also have mentioned that it freezes when i tell it to create an iso from a disc (whether it is to my desktop or directly to another CD), not on the actual burning.

---

### Post by Ganymedes on 2009-09-16
> **capinlarry said:**
> sorry, i should also have mentioned that it freezes when i tell it to create an iso from a disc (whether it is to my desktop or directly to another CD), not on the actual burning.

Yes, that seemed likely already based on your first question and now DD seems to verify that.

So, it cannot read the disk, nothing wrong software-wise. Could you try with another disk? I guess what you can try is now obvious:
- clean the CD
- "clean" the CD-unit (try to blow the dust away, if applicable and if nothing else :-))
- try with another CD-*reader* ... it might still burn it, in theory

You seem to have another unit in your system (because you are using "sr1"), but if you try a regular reader, be careful. I mean that a reader might read it without giving an error, when a reader/writer refuses to read. But the output from the reader might be corrupted data. That happens easily when reading bad audio records. So, you need to verify the contents (after burning) if you use a regular reader.

I had a few months ago a CD/DVD-RW unit which did not work with CDs no matter what I tried, but it worked perfectly OK with DVDs ... so anything is possible.

---

### Post by capinlarry on 2009-09-16
yes, i have two drives, a cd burner and another dvd player. ive tried to create a .iso from both drives to no avail but both seem to read the disc just fine, i can open it and see all of the files. ive tried creating iso from both DVD and program CDs and both freeze after 3mb. maybe i should try powerISO instead of Brasero.

---

### Post by Ganymedes on 2009-09-17
Very good. 

The thing is that both ways stop at 3 Mb, including DD, and both drives do the same, so it is slightly unlikely that a third method would work any different (or then it does something else completely).

So the disk seems to work in an interactive way, well, it can still be faulty, because it is rather difficult to test the disk completely just by browsing it. I admit, still you would normally spot problems.

Still, the most likely scenario is that the disk is faulty. We have not really discussed what that disk is - it might not be "faulty for the regular user", but it might be "copy-protected by disk faults".

Can you try with another disk or disks, which you know are good (and not copy protected)?

If it is copy-protected, you may need to use a "ripper" application, which is capable of handling that situation. Copying a copy-protected disk is legal or illegal depending on where you live.

---

