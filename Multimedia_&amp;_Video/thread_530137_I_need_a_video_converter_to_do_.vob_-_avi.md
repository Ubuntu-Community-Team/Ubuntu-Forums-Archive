---
title: "I need a video converter to do .vob - avi"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by eXidos on 2007-08-20
I am using dvd::rip to backup my dvd's but It is having trouble with my LVM partition it will let me rip the dvd but when I I try to transcode it it says "0mb will be used and 0mb free" (I have 1.5TB free) then errors out. so now I have all these movies in multiple .vob files and I want to encode them to divx or xvid in a singal file. I have been using xine to make playlists for each movie but they are coming out at 6-11GB per DVD, I wouldn't mind 3 or 4GB files to save quality but I have allot of dvd's and hard drives are expensive, plus my case can only take so many drives.

What I need is a good converter (preferably with a gui) but I'm not against finding a new backup program to re-rip my dvd's if needed; any suggestions?

The converter needs to:

rip dvd's at full resolution 480p
rip audio with 5.1 audio
transcode to Xvid or DivX (maybe even H264 I'd like to give it a shot)
work with ubuntu 7.04
as far as working with LVM partitions I can test that myself.

---

### Post by julian67 on 2007-08-20
1st maybe make sure all the directories dvdrip uses are writeable. There's a chance you're trying to write the project/temp files to directories that only root can write. I had this problem the first time I used some ripping apps whose default config wasn't ideal for Ubuntu's default permissions.

A good alternative for ripping DVD to avi is [acidrip]("http://untrepid.com/acidrip/")

> AcidRip is a Gtk2::Perl  application for ripping and encoding DVD's. It neatly wraps MPlayer and MEncoder, which I think is pretty handy, seeing as MPlayer is by far the best bit of video playing kit around for Linux. As well as creating a simple Graphical Interface for those scared of getting down and dirty with MEncoders command line interface, It also automates the process in a number of ways:

    * Parses DVD into contents tree
    * Finds longest title
    * Calculate video bitrate for given filesize
    * Finds black bands and crops them
    * Gives suggestions for improved performance
    * Other stuff!



Again you need to configure it making sure all the directories you choose are writeable. It's in the multiverse repo.

---

### Post by endersshadow on 2007-08-20
They're AcidRip (apt-get acidrip), gmencoder (apt-get gmencoder), and [Vive](https://sourceforge.net/project/showfiles.php?group_id=158461).  Take your pick.

---

