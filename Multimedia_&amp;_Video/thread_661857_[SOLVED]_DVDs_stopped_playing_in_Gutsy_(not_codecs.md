---
title: "[SOLVED] DVDs stopped playing in Gutsy (not codecs problem)"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Devi 710 on 2008-01-08
Hello everyone.

After a fresh install over a month ago, I had no problem playing DVDs in Gutsy. I installed all the required codecs: libdvdcss2, libdvdplay, libdvdnav, and libdvdread and never had any problems.

I didn't play a DVD for a week or 2, and then I tried to play the 2nd season of Arrested Development I just bought and it, and any other DVD, won't play in Totem, VLC, or Mplayer.

When I put the DVD in it mounts fine, shows on my desktop and I can browse through the folders on the disks. The default program for playing DVDs will start (which ever one I set it to) but then it stops. Nothing happens.

I tell the various applications to play the DVD, (ie: "Open Disk" "Play DVD" tell VLC the mount point - /media/cdrom0 ect.) the drive will read the disk and act like it is going to start, then nothing. The disk just keeps being read and I end up having to force quit the application. Then everything runs slowly.

No error messages or anything. The light just keeps blinking away in my DVD player and the video player freezes (all 3 of them, same issue)

The only thing I changed recently was in the Removable Drives and Media preference I change the default player to VLC from Totem because I didn't get menus with Totem and Mplayer, just the movie.

I really can't think of anything I have done to my system lately that would cause this problem. Anyone have any suggestions?? Please and Thank you.

Devi 710

---

### Post by Devi 710 on 2008-01-19
OK I fixed it.

I discovered my DVDs stopped playing in Gutsy after I tried to install [SIZE="5"]**pcsx2**[/SIZE] following this guide:

[http://forums.ngemu.com/pcsx2-official-forum/97350-linux-guide.html#post1240477](http://forums.ngemu.com/pcsx2-official-forum/97350-linux-guide.html#post1240477)
[PCSX2 Guide]("http://forums.ngemu.com/pcsx2-official-forum/97350-linux-guide.html#post1240477")

It never worked for me. I had to go back and remove everything that I had added with sudo apt-get remove

ie: sudo apt-get remove nvidia-cg-toolkit
     sudo apt-get remove subversion libjpeg62-dev
     and so on...

Then I reinstalled the DVD codecs to be safe:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh

And everything is fine again. I hope this helps somebody.

Devi
:guitar:

---

