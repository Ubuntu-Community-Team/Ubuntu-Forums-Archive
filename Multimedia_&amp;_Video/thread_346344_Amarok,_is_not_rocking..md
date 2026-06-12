---
title: "Amarok, is not rocking."
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by dothedorky on 2007-01-25
I decided today that i'd delve into the world of Amarok,I'll start from the beginning so maybe you all can (hopefully) follow my very frustrated train of though...

I uploaded my library via the drag-and-drop method discussed on the amarok wiki, and everything was playing inside the library (all songs on the dvd are mp3 format).

I exited the program completely, then right clicked-->eject to try and get the disk out.

I got this error:

```
Unable to eject media:
umount: /media/cdrom1: device is busy
umount: /media/cdrom1: device is busy
eject: unmount of `/media/cdrom1' failed

```

I go to check the system monitor to see if i can kill a process (or pretty much just see exactly what it was working on, since it really wasnt playing anything)... i saw nothing out of the ordinary, until i clicked on the 'devices' tab.

It showed that my /dev/hda3 was 41% used, and my /dev/hdd was 100% used. 

Is that completely irrelevant?

After a really long time, the dvd finally ejected.

I went to start amarok once again, All my files are there (music/folders etc), but when i go to click on a song to play it- it tells me:

```
Local file does not exist.
```

So i pretty much have a library full of songs and song names that dont play unless the actual disk is in my drive.

Also, in my library, some songs show up as having no time length and some of these play, while others do not. When i try to edit them it tells me i do not have permissions to write. (with the disk inserted) and when i edit them without the disk inserted it tells me the file does not even exist.

So to wrap all this up, i'll leave you with just the basic questions:

1)If the file doesnt exist them why are there folders, and song names? 

2)Why does amarok hold my dvd hostage until its done doing whatever? (even after i press quit)

3)How do i get amarok to save more than just the names of the tracks?

4)How  do i get amarok to play mp3s when the disk isnt inserted?

5)How do i edit track names/information?

6)Why do some tracks have no times, yet still play, and others do not?

Sorry for the long post, i've been trying to figure this out (on my own) since... well forever, 

Thanks in advance to anyone with any suggestions/help.

---

### Post by meltingrobot on 2007-01-25
I haven't played around much with playing dvds or cds full of mp3's with well... really anything.  Amarok has worked pretty good for me, but my setup is a little bit different.  I always offload the music to the local disk.  It sounds like this is what you are wanting to do.  If so, I would recommend putting in the disk and using the cp command to move all the files or drag them via the GUI into a folder in your home directory.  If you don't want the files copied locally, then my directions don't help.  :(

---

### Post by dothedorky on 2007-01-25
the files seem to be physically there already, they just wont function.

---

### Post by meltingrobot on 2007-01-25
I doubt that's the case.  Amarok probably just learned the files location, which was the dvd drive.  Amarok stores the ID3 tag info in its own database.  I bet if you clicked Tools and selected Rescan Collection with the disc out of the dvd drive, they would disappear.

---

### Post by dothedorky on 2007-01-25
[COLOR="Red"]New Problem[/COLOR]

I had this significantly bright idea to search and install some plugins that i've never seen before (possibly, i thought, what could be preventing me from playing music)

I followed the instructions given to me on this link:

[http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06](http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06)

of course i ignored the statement that it was for Kubuntu (i'm running plain ubuntu 6.06 LTS).

When i tried to restart amarok, i got a completely new interface (not entirely bad)... but then all of those unplayable music title i had in the previous amarok version have disappeared.

In replacement, i get a friendly message from Matthias Ettrich welcoming me to amarok....

and that's really all i get. :( 

More help :confused:

---

### Post by meltingrobot on 2007-01-25
That's because Amarok didn't copy the songs to the hard drive.  You need to do that, and then point Amarok to where you copied them to.

Put the disc with the mp3's back in.  Then open it with the file viewer or browser or whatever it's called.  Then go the the menu at the top of the screen and click Places and then Home Folder.  Copy the music into the home folder, maybe under it's own directory if you want to create one, and then tell Amarok to search your home directory for music.

---

### Post by dothedorky on 2007-01-25
when i try to copy the songs from the disk to its own folder (in the home directory) it tells me 

```
Error while copying to "/home/dork...ous/Music".
There is not enough space on the destination.
```

edit: i figured id split up the songs among folders, and save them to a folder i created called "Imported music"... only it tells me that copying a cd's songs into a folder will take 30 minutes..., something's gotta be wrong with that.

---

### Post by meltingrobot on 2007-01-25
Go to Applications -> Accessories -> Terminal and type df -h and hit Enter.  What does it say?

---

### Post by dothedorky on 2007-01-25
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             8.2G  5.4G  2.4G  70% /
varrun                189M   76K  189M   1% /var/run
varlock               189M  4.0K  189M   1% /var/lock
udev                  189M  124K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   19M  171M  10% /lib/modules/2.6.15-27-386/volatile
/dev/hdd              8.0G  8.0G     0 100% /media/cdrom1

```

thanks for your quick responses btw, i really appreciate it.:KS


edit: this was before finally saving all my music files to a folder in my home directory. I pretty much just drag-and-dropped each file into the folder simultaneously (killing my cpu, but it worked). It all took about an hour or two. However, on the same disk i also have a folder containing movies i downloaded from frostwire when i used windows, for this group of videos, it told me i had no more space. (Despite making a seperate folder)...

Here are the updated results of df -h:

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             8.2G  6.1G  1.7G  78% /
varrun                189M   76K  189M   1% /var/run
varlock               189M  4.0K  189M   1% /var/lock
udev                  189M  124K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   19M  171M  10% /lib/modules/2.6.15-27-386/volatile
/dev/hdd              8.0G  8.0G     0 100% /media/cdrom1
```

---

### Post by liljoe76 on 2007-01-25
i could be totally outta line here, but are you trying to copy 8gigs of dvd to 1.7gigs of free space on your harddrive???

---

### Post by dothedorky on 2007-01-25
> **liljoe76 said:**
> i could be totally outta line here, but are you trying to copy 8gigs of dvd to 1.7gigs of free space on your harddrive???

Is that bad? :-$ 

The music files are already on my hard drive, i just can't add anything else TO folders.

and the hard drive still 1.7 G's available.

I'm still banging my head against the keyboard... amarok's STILL not working properly.

---

### Post by dothedorky on 2007-01-25
[COLOR="Red"]Update:[/COLOR]

With this 'new' version of amarok, i was able to install my music files (now in a folder in my home directory) within the player. I ejected the disk, and then tried to play a song.

I got this error:

```
Error Loading Media
No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.

```

---

### Post by dothedorky on 2007-01-25
wow, what a big mess i made by tinkering...

i got the songs to play, and be in the library without the disk inserted. 

here is why i'm giving up on amarok (temporarily- unless someone else has better ideas)

-It spikes my cpu usage to 100% and NEVER comes down.
-It mixed up the 'album names' for EVERY song. It'd play a song from one artist, and display the album title for another.
 *note- when i right clicked and tried to see if i could change these names, everything in the following files was correct! (correct song name with correct band..even with the correct file path!).
-The album covers were mixed up and/or COMPLETELY off. For the Red Hot Chili Peppers. for example, it gave me an album cover for Bruce Springsteen... and i dont even HAVE springsteen *shudder* music in my library.

I'm completely at my wits end. Amarok is on hiatus...

Surely open source material can't be THIS complicated..

---

