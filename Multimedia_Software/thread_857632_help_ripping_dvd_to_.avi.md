---
title: "help ripping dvd to .avi"
date: 2008-07-12
forum: Multimedia Software
---

### Post by bc54 on 2008-07-12
hi. i am looking for an easy way to rip dvd into an .avi format and nothing i try seems to work. i have acces to three different setups right now:
     ubuntu 8.04 with a dvd reader (main computer)
     ubuntu 7.10 with dvd reader (same computer but a different hard drive)
     Windows xp on a laptop with dvd reader/writer
in 8.04 i can't even get dvds to mount (encrypted and non-encrypted), but i can mount and watch all my dvds on 7.10. the windows machine can play and burn dvds. i need to rip my movies to .avi so i can watch them on the 8.047 installation. i have dvd::rip, acidrip, k9copy,and ogmrip and nothing is working, most of them won'tmove the progress bar. on windows i have tried handbrake, alcohol 120%, and others but they don't work either. could someone please explain to me the easiest way to do this?
Edit- also, before i upgraded to 8.04 i was able to play dvds and was able to rip 1 (only attempted 1) chapter off "tom and jerry" greatest hits dvd.

---

### Post by rbprogrammer on 2008-07-12
I think it might be safe to say you won't get to far with this issue here.  Since ripping DVD's is a controversial topic, even though you may own the DVD's, this would be illegal in most countries.

I made the mistake on one of my earlier posts, and an admin told me this:
> 
**Do not ask about illegal rom/movie/software downloads on Ubuntu Forums.**
I believe your question was innocent, so search google and mention nothing more of it here.


Sorry, I think may people would love to have such an answer.  But you won't get that answer here.

---

### Post by sdowney717 on 2008-07-12
k9copy will copy DVD from the large version to a smaller version where it will fit on a single sided DVD. 
I think a lot of people want to protect their DVD and therefore make usable copies to play in the machine. I know people with kids who destroy DVD and CD and parents want to keep the original pristine and undamaged.

Just what do you think most people do with CD's and DVD's they buy at the store?  
The copyright rules have become fairly extreme nowadays.

---

### Post by Vivaldi Gloria on 2008-07-12
bc54,

you are asking simultaneously about three operating systems and it is confusing.

Let's stick with 8.04 and a single problem: Can you play encrypted DVDs? If not first enable that as follows:

1) Enable medibuntu repos following the "Repository HowTo" here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

2) Then install the following programs using the command

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 build-essential ubuntu-restricted-extras
```

3) Check if encrypted DVDs work. If not try this command in a terminal:

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

That should do it.

---

### Post by bc54 on 2008-07-13
sorry, i did not know that talk about dvd ripping was not allowed, but if i could get dvd play back to work then i would not have to worry about it.

Vivaldi Gloria, to clarify: my 8.04 setup is what i use most often but i can't even mount dvds on it so therefore i cannot play them. so in order to play dvds i must reboot to my 2nd hard drive (7.10). my reason for wanting to rip was so i don't have to reboot to watch a movie. i only mentioned the windows in case that was the only solution to rip a dvd.

now, i had medibuntu repos enabled before but i repeated it anyways.
then i ran your apt-get command and all of them were previously installed. i put in a dvd and it didn't mount. then i tried your install-css.sh command.
this is what it said> sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found
i noticed that it should read > sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh
that gave me > sh: Can't open /usr/share/doc/libdvdread3/examples/install-css.sh
instead i had to run > sudo sh /usr/share/doc/libdvdread3/install-css.sh and libdvdcss was downgraded. is this right?
the dvd stil won't mount but i will reboot and edit my post.
-thanks
Edit- still won't mount, ideas anyone?

---

### Post by Vivaldi Gloria on 2008-07-13
Hmm. If dvd's don't mount then this is probably an /etc/fstab issue. Can you copy and paste your /etc/fstab from both your 7.10 and 8.04 so that we could compare them.

Btw, you are using the same dvd player with 7.10 and 8.04, right?

---

### Post by bc54 on 2008-07-14
ok. yes, 8.04 and 7.10 both use the same dvd player (exact same computer).
the /etc/fstab for 8.04
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=85b2099d-7787-48a4-9145-f4e5c8a00b08 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=10ce73b2-2c4b-4295-9988-11ece4172d80 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

and 7.10
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=2f77ebdb-0865-4c59-b598-9686953e4dc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=35eeb2de-04f4-434b-abe3-0c6c63a7f37a none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

edit- now i can't get dvds to mount in gutsy. i jsut ran a partial upgrade to fix apt, could that be a problem?

---

### Post by Vivaldi Gloria on 2008-07-14
I'm looking at your fstabs and I cannot see a problem. This is beyond my knowledge. Your subject line of this thread is misleading and I suggest you open a new thread in "hardware & laptop" subforums with a title like "cannot mount dvds" so that the right people can have a look at it.

---

### Post by bc54 on 2008-07-14
thanks for your help anyway. by the way for some reason 7.10 can mount dvds again. go figure.
-thanks
ps. sdowney717- thanks for tip about k9copy. (no .avi but vlc can open a dvd backup folder)

Edit- here the link to the new thread [http://ubuntuforums.org/showthread.php?t=859846]("http://ubuntuforums.org/showthread.php?t=859846") & BTW i think it was maybe a driver problem (updated drivers weren't able to communicate as well with the reader).

---

### Post by Vivaldi Gloria on 2008-07-15
```
thanks for your help anyway. 
```

Your welcome mate. If you decide to open a new thread then please paste its link here.

---

