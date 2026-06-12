---
title: "I/O error while trying to copy VCD's onto HDD"
date: 2006-09-09
forum: Multimedia &amp; Video
---

### Post by binary_goofy on 2006-09-09
[SIZE="2"]hi,
  i'm using ubuntu 6.06 onto my system, am unable to copy any VCD's using a direct copy, paste onto my HDD :(  but the VCD's play just fine. i don't think there's problems with the cd's itself as so many cd's cud not be bad, especially d ones i bought new and never watched before. also the same cd's copy fine in windows. using dd also gives an I/O error and terminates the copy. is there some sort of copy protection dat ubuntu has in place due to which this is happening?:-k my drive is a 1 week old sony dru-820A, so i doubt there are probs with it. googling didn't bring up much. any suggestions?[/SIZE]

---

### Post by makadam on 2006-10-19
Hi

Use CDFS filesystem to mount the CD-ROM.

---

### Post by 3rdalbum on 2006-10-19
Windows seems to have a built-in ripper, whereas Ubuntu doesn't. Try using Acidrip or a program like that.

---

### Post by makadam on 2006-10-20
Hello.

You can install the CDFS kernel module like this:

First install the "module-assistant" which helps you compiling and installing the modules.
```
sudo apt-get install module-assistant
```

Use the the "module-assistant" command to prepare your system.
```
sudo module-assistant prepare
```

Install from universe repositories following package "cdfs-src" and all dependencies. Also you can use the "module-assistant" to install the *.dep package.
```
sudo apt-get install cdfs-src
```

Use the the "module-assistant" command to compile and install the module.
```
sudo module-assistant
```

Follow these steps to accomplish the installation:
1) Select SELECT and confirm with OK
2) Select the module you want to install. In this case the module cdfs. Select and confirm with OK.
3) Select BUILD to compile the module and confirm with OK.
4) Confirm with OK the installation.
5) The end. You can leave the "module-assistant"

Now mount your CD-ROM, to access directly to the movie files (*.mpg / *.mpeg).
```
sudo mount -t cdfs /dev/hdx /media/cdrom
```

Have fun!

---

### Post by binary_goofy on 2006-11-01
hey guys thanks a lot for responding. thanks a lot makadam. ur solution worked like a darling. am only trying to figure out how to give users mount rights now. God bless.

---

### Post by rykel on 2006-12-17
Hi Makadam,

Do I have to reboot?

After following your instructions, I still get the following error:

[INDENT][B]sudo mount -t cdfs /dev/scd0 /media/cdrom0
mount: unknown filesystem type 'cdfs'
[/B][/INDENT]

P/S 1. I tried rebooting, and I still get the same error message... can someone up there do something about this frustrating Linux "bug"? VCD is a big thing in the Asian parts of the world, and it is a shame if we have to go through so much trouble just to copy what can be dragged-and-dropped in Windows XP.   =P

P/S 2. OK, now it "works"! BUT, I am a bit confused... it seems like all the folders are now displayed as an iso file with a mpeg file.... I simply copy the mpeg file over, riiite?

---

### Post by hyperair on 2007-08-28
I'm using Feisty, and I followed those instructions exactly, but it just won't compile! Nevermind, I got the source from CDFS's official site.

---

### Post by manmath on 2007-11-27
I copy the disc to the hard disk as a raw/iso (dd if=/dev/cdrom of=/tmp/image.iso) then I use vcdgear to extract the dat to mpg:

vcdgear -raw2mpg /tmp/image.iso movie.mpg


This is pretty much the method I would recommend as well, the one change I would add is that I use readcd as it handles copying from the CD medium much better than dd, IMHO.

"vcdgear -fix -cue2mpg" has been reliable in extracting a working mpg from a standard image file set.

Just tried with DD and had an issue. readcd is a good tool, I prefer cdrdao myself and this command line should get you a lovelly bin/cue to use vcdgear on:

cdrdao read-cd --device ATA:1,1,0 --driver generic-mmc-raw --read-raw image.cue

Change the device for whatever is your reader!

OR

install readvcd and then 

# readvcd 2 > mv.mpg

OR

Install vcdimager
# vcdxrip

OR

install cdfs
mount -t cdfs /dev/cdrom (or whatever your drive is) /home/movie (or whatever your destination)

---

