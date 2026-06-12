---
title: "Creative Zen Ubuntu 7.10 AMD 64"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by brucehelp on 2008-02-01
First I am new to Ubuntu but not to operating systems. The 7.10 is wonderful.
Had it up and running in 20 minutes on a AMD64. Even got Utube to work with the change Adobe made in Dec.

Anyway....

Need to get Creative labs Zen MP3 player to work as well in Ubuntu as it can in Ubuntu.

I found the latest version of Gnomad 2.9 but Synaptic does not have it in the list.

Would rather not get into compiling and all. Just a nice simple one button solution. smiles

Ok Cut and past into terminal solution.

---

### Post by brucehelp on 2008-02-01
Found this at [http://perbu.livejournal.com/2012.html](http://perbu.livejournal.com/2012.html)
Totally greek to me anyone have an easier solution ????
Bruce


perbu (perbu) wrote,
@ 2008-01-30 20:51:00
Previous Entry  Add to memories!  Tell a Friend!  Next Entry
Entry tags:	ubuntu, zen

The Creative Zen and Ubuntu
Yesterday I've got a Creative Zen. Whoohoo. I did some investigation ahead of the purchase and found out it should work well with Gnomad2. As this is my first MP3-player which is not a generic USB mass storage unit things are not straight foreward.

Creative uses MTP - multimedia transfer protocol - to push content onto the Zen. You have to rely on special tools (Amarok, Gnomad2 or some not quite intuitive cli tools) to transfer your mp3 files to the zen.

Ubuntu ships a version of libmtp which does not recognize the zen. To fix this we can either patch in the USB id of the zen into libmtp or simply upgrade the library. I did the latter. Here is how I did it:

   1. Download the 0.2.5 version of libmtp
   2. Download the source the the Ubuntu 7.10 version of libmtp with "apt-get source libmtp"
   3. Copy the directory "debian" from the source into the 0.2.5 directory you've just created.
   4. Issue a "debchange -i" and fix the version number and add a usefull comment
   5. "dpkg-buildpackage -b -rfakeroot" inside the directory will build a new version of the package in "..".
   6. Install the libmtp and the libmtp-dev packages you've just buildt
   7. Now do a "apt-get source -b amarok" and "apt-get source -b gnomad2" to rebuild amarok and gnomad2 with the new version of libmtp.


Great. Things should work now. If you get funky "detected a broken PTP header, code field insane, expect problems" you firmware is broken (probably). You need to get a hold of a windows system and install the software on the CD-ROM onto it. Then run the "autoupdate software" from the windows thingy. It should fix your Zen.

If this was greek and you need this to work - please leave a comment. If you trust me (who doesn't?) I'll even put up the 0-day versions of libmtp, Amarok and Gnomad2 I've created. :-)

---

### Post by brucehelp on 2008-02-01
Found this from Gnomad2 site
[http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)
News


2008-01-28: Gnomad 2.9.1 adds support for device detection using D-Bus and HAL, you can plug in/out devices and gnomad2 will react. We will not erroneously delete "." or ".." dirs. We can cancel up/download on MTP devices. You can use taglib only if you want to. (No more libid3tag, but this is NOT RECOMMENDED). And finally we have folder support for the MTP device


Working Devices:
Creative NOMAD Jukebox 1 (aka D.A.P.)
Creative NOMAD Jukebox 2
Creative NOMAD Jukebox 3
Creative NOMAD Jukebox Zen
Creative NOMAD Jukebox Zen USB 2.0
Creative NOMAD Jukebox Zen NX
Creative NOMAD Jukebox Zen Xtra
Creative Zen Touch
Creative Zen Micro
Creative Zen Sleek
Creative Zen
Dell Digital Jukebox ("Dell DJ")
Second Generation Dell DJ
Dell Pocket DJ

MTP devices:
Creative Zen Portable Media Center
Creative Zen MicroPhoto
Creative Zen Vision
Creative Zen Vision:M
Creative Zen Sleek Photo
Creative Zen Xtra (MTP mode)
Creative Zen Micro (MTP mode)
Creative Zen Touch (MTP mode)
Creative Zen Sleek (MTP mode)
Creative Zen V
Creative Zen V Plus
Second Generation Dell DJ (MTP mode)
Dell Pocket DJ (MTP mode)

Perhaps:
Any other MTP device which can play audio. I haven't tested them much, but they reportedly work with libmtp so should be OK. This includes:
Samsung YH- and YP- MTP players
Intel PMC
JVC Alneo
Philips HDD/GoGear series
Sandisk MTP devices
iRiver MTP devices
Toshiba Gigabeat devices
Archos MTP devices
Dunlop MP3 player
Sirius Stiletto


You are invited to read the Gnomad README file and Change Log.

---

### Post by brucehelp on 2008-02-01
Great I have downloaded a new version of Gnomad that is as mentioned above should 
fix the MTP issue. But all I have now is a .tar file on my desktop.

HELP >>>>>>>>>>:confused:

I know in terminal one can install a .tar file. But can we get some instructions on how ?

:)


Downloading ...

Thank you for downloading Gnomad2 - a NOMAD / MTP Device Manager.

Your download should begin shortly. If you are experiencing problems with the download please use this direct link.

Downloading from the following mirror:

---

### Post by Valok on 2008-02-01
If you go into rhythmbox.

Edit-->Plug-ins.  Then make sure that the box next to MTP - Portable players is checked.

Once you do that (you may have to restart rhytmbox) the MP3 player you're using should show up on the left  hand column in the same place a CD would if you put that in.  As a note, I'm doing with with a Creative VIsion: M

Hope this helps!

---

