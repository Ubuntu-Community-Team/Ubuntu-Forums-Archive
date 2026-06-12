---
title: "How come I can't use DD command to make an .ISO Disc Image"
date: 2009-09-18
forum: Multimedia Software
---

### Post by OzzyFrank on 2009-09-18
I'm wondering if someone can explain why using **DD** to create an .**ISO disc image** ends up with a 0-bytes file?

When I use **[COLOR="Indigo"]dd if=/media/cdrom of=whatever.iso[/COLOR]** I get the following a few nanoseconds later:

[B]dd: reading `/media/cdrom': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000390544 s, 0.0 kB/s[/B]

It doesn't seem to be the path to the disc drive, as **[COLOR="#4b0082"]/media/cdrom0[/COLOR]** gives the same result, and using **[COLOR="#4b0082"]/dev/cdrom[/COLOR]** or **[COLOR="#4b0082"]/dev/dvd[/COLOR]** gives me:

**dd: opening `/dev/cdrom': No such file or directory**

So, obviously **[COLOR="#4b0082"]/media/cdrom[/COLOR]** is fine, yet the command does nothing (but produce a blank file).

And YES, I do have a disc in the drive, hehe! Any ideas what I need to do here?? Cheers.

---

### Post by mc4man on 2009-09-18
dd the device

ex.
```
dd if=/dev/scd0 of=whatever.iso
```

note that even 1 read error will halt dd

What are you trying to dd?

Edit:
If there may be read errors that you don't mind missing then add  to command
```
dd if=/dev/scd0 of=whatever.iso conv=noerror
```

If it's an encrypted dvd then the dd above will work, but will probably take a long time 

dvddisaster is better for all dumps to .iso than dd, for data disks it will fast skip errors on the 1st. pass. You can run it over again and it will only read the missed sectors. Can be done multiple times.
The default is 1 read try per sector, for a 2nd pass you up to 5, for a 3rd, 10.

For a misuse of dvddisaster to dump an encrypted dvd to .iso see here (cannot be burned, just for hdd playback

[http://ubuntuforums.org/showthread.php?p=6365060#post6365060](http://ubuntuforums.org/showthread.php?p=6365060#post6365060)

---

### Post by OzzyFrank on 2009-09-18
Yeah, thanks man, that fixed it. It wouldn't recognise **/dev/cdrom** (or **/dev/dvd**) so I just thought the mount point had to be used. Didn't realise my device was actually **[COLOR="Indigo"]/dev/scd0[/COLOR]** - now I know what to do for programs that want to access **/dev/cdrom** and can't. Cheers. Frank

PS: Glad the Ubuntu Forums finally reinstated the option to mark threads as **[SOLVED]** - I could never understand why they thought it was a good idea to remove it in the first place.

---

