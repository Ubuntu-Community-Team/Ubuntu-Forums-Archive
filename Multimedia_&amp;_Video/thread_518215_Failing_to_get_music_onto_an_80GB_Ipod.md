---
title: "Failing to get music onto an 80GB Ipod"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by asktoby on 2007-08-05
I have just set a friend up with a new Feisty Fawn distro.
He's bought an 80GB ipod and is having difficulty getting music to go onto it.
I'm getting him to use Rhythmbox and follow the instructions at:
[http://www.simplehelp.net/2007/07/03/how-to-manage-your-ipod-using-rhythmbox-in-ubuntu/](http://www.simplehelp.net/2007/07/03/how-to-manage-your-ipod-using-rhythmbox-in-ubuntu/)

It all works fine until the final step:

The Ipod icon appears on his desktop,
Rhythmbox loads up
The ipod shows up down the left hand side in Rhythmbox
He can drag music to it, and it shows up on the ipod in Rhythmbox
He closes rhythmbox
Doubleclicking on the Ipod desktop icon shows the music on there in the nautilus window.
Closing that window brings him back to the desktop
He right-clicks on the ipod icon and chooses "eject"
The "Do not remove" logo disappears from the Ipod and the Ipod returns to it's menu
But: ***The songs are not on the ipod***.

Does anyone have any idea where this might be going wrong?

---

### Post by joe.turion64x2 on 2007-08-05
> **asktoby said:**
> I have just set a friend up with a new Feisty Fawn distro.
He's bought an 80GB ipod and is having difficulty getting music to go onto it.
I'm getting him to use Rhythmbox and follow the instructions at:
[http://www.simplehelp.net/2007/07/03/how-to-manage-your-ipod-using-rhythmbox-in-ubuntu/](http://www.simplehelp.net/2007/07/03/how-to-manage-your-ipod-using-rhythmbox-in-ubuntu/)

It all works fine until the final step:

The Ipod icon appears on his desktop,
Rhythmbox loads up
The ipod shows up down the left hand side in Rhythmbox
He can drag music to it, and it shows up on the ipod in Rhythmbox
He closes rhythmbox
Doubleclicking on the Ipod desktop icon shows the music on there in the nautilus window.
Closing that window brings him back to the desktop
He right-clicks on the ipod icon and chooses "eject"
The "Do not remove" logo disappears from the Ipod and the Ipod returns to it's menu
But: ***The songs are not on the ipod***.

Does anyone have any idea where this might be going wrong?
I have an LG MP4 which does not display in its screen files which playback is not supported, although the files ARE THERE. Are the files supported ones?

Joe.

---

### Post by rbprogrammer on 2007-08-05
_i'm not sure if this is the route to go since i have **no experience** with Rhythmbox_, but i use amarok and uploading mp3's to my 80gb video iPod worked right out of the box, i have to do very little configuring. 

the only actual configuring that i did was when i plugged in the iPod to the computer, a message box in amarok asked what to do with the new media.  i clicked "iPod" or something along those lines, and bam! i was up and running.

---

### Post by joe.turion64x2 on 2007-08-05
> **rbprogrammer said:**
> _i'm not sure if this is the route to go since i have **no experience** with Rhythmbox_, but i use amarok and uploading mp3's to my 80gb video iPod worked right out of the box, i have to do very little configuring. 

the only actual configuring that i did was when i plugged in the iPod to the computer, a message box in amarok asked what to do with the new media.  i clicked "iPod" or something along those lines, and bam! i was up and running.
I don't have an Ipod but, is it possible to also copy files as in a Flash drive?

---

### Post by asktoby on 2007-08-06
> **joe.turion64x2 said:**
> I have an LG MP4 which does not display in its screen files which playback is not supported, although the files ARE THERE. Are the files supported ones?


They are ordinary mp3 files which the iPod supports.

---

### Post by zach12 on 2007-08-06
hmm did you sync with itunes after you put the mp3s on it

---

### Post by asktoby on 2007-08-06
> **rbprogrammer said:**
> _i'm not sure if this is the route to go since i have **no experience** with Rhythmbox_, but i use amarok and uploading mp3's to my 80gb video iPod worked right out of the box, i have to do very little configuring. 

the only actual configuring that i did was when i plugged in the iPod to the computer, a message box in amarok asked what to do with the new media.  i clicked "iPod" or something along those lines, and bam! i was up and running.

Did you ever connect your iPod to a Windows/MacOS machine running iTunes? I've heard tales that, if it's connected to iTunes once, it builds the database it needs or somesuch and can then be used on other devices without iTunes.

I could certainly install Amarok. I would have to give him the root password over the phone since he has no internet, which is a bummer, but it's something to try.

---

### Post by asktoby on 2007-08-06
> **zach12 said:**
> hmm did you sync with itunes after you put the mp3s on it

I'm not sure what you mean. It's a brand new out-of-the-box 80GB iPod and a brand new install of Feisty, with Rhythmbox. There is no iTunes. Could you elaborate please?

---

### Post by nexu56 on 2007-08-16
Rbprogrammer is spot-on. In order for the iPod to "see" your collection it expects to have a certain directory structure and db files. For Mac/Windows users this happens when you first connect it to iTunes. Amarok can do it too but apparently the version of Rhythmbox in Feisty can't. It just copies the files across as if it were a USB hard drive.

Oh well, I guess I have to switch from Rhythmbox to Amarok now that I have an iPod :-(

---

### Post by asktoby on 2007-08-22
To resolve:
The device was formatted with HFS (Mac's FS)

A brand new ipod is usually not formatted, and is first formatted when
it gets connected to a PC or a Mac, with either FAT32 or HFS+
filesystems.
Linux will have difficulty with a HFS+ ipod so it must be connected to a
windows PC first to format it as FAT32.

You can see how your ipod is formatted by going
$ cat /etc/mtab

Look for a line that says something like /dev/sda2 /media/ipod and see
what is listed to the right of that. If it says vfat, then you know your
device is FAT32 formatted. If not, well. . . you're just going to have
to change it.

I got my friend to connect his iPod to iTunes on an XP box and the
conversion was transparent. It now works in Ubuntu fine!

---

### Post by missed her show on 2008-01-03
> **asktoby said:**
> To resolve:
The device was formatted with HFS (Mac's FS)

A brand new ipod is usually not formatted, and is first formatted when
it gets connected to a PC or a Mac, with either FAT32 or HFS+
filesystems.
Linux will have difficulty with a HFS+ ipod so it must be connected to a
windows PC first to format it as FAT32.

You can see how your ipod is formatted by going
$ cat /etc/mtab

Look for a line that says something like /dev/sda2 /media/ipod and see
what is listed to the right of that. If it says vfat, then you know your
device is FAT32 formatted. If not, well. . . you're just going to have
to change it.

I got my friend to connect his iPod to iTunes on an XP box and the
conversion was transparent. It now works in Ubuntu fine!



Still having some problems, mainly i can't see any of the music i've "transfered" to the ipod.

---

### Post by mystery_man33 on 2008-01-06
> **missed her show said:**
> Still having some problems, mainly i can't see any of the music i've "transfered" to the ipod.

I'm having a similar problem with Gutsy and the Pro Duo card in my SE W850i. The GUI shows the files being copied onto the phone card. I then unmount the card and am told that data needs to be written before the unmount can be completed. Depending on how much data has been copied another message pops up after several minutes saying it is now safe to remove the device.
I check the phone and none of the MP3s are available. If I connect my phone to my MAC and map a samba connection to my Ubuntu box to copy the MP3 files this works. At the moment this is the only way to get MP3s onto my phone.

Unfortunately there is a separate MAC problem that seems to crop up when transferring large amounts of data........but that's for a different forum. 	](*,)

---

