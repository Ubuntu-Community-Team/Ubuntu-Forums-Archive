---
title: "Play DVDs from ISO image"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by tbg58 on 2007-05-28
Here's a tip for you to be able to watch your legally-obtained DVDs on your Ubuntu system.  Check out the Medibuntu site for more information on how to get Totem to play DVDs - I won't post that information here other than to say before you obtain any additional codecs, you will want to switch your Totem installation from GStreamer to Xine, as the former seems to have some issues with DVDs currently.
sudo apt-get install totem-xine
sudo apt-get xine-ui 
will get you up and running on xine.  If you wish to view encrypted DVDs again check the Medibuntu site for more information.

Once you have your DVD, stick it in the DVD drive on your Ubuntu box.  Ubuntu will auto-mount it and start playing it if you have the right codecs.  
Stop the play on Totem and close.  
Ubuntu will make the ISO for you:
Right-click the mounted DVD and click Copy disc, and in the pop-up dialog box, click write.
The process will continue for a while.  A Dual-layer DVD will take about 10-20 minutes, depending on the speed of your drive.
Ubuntu is writing out a temporary file.  When the percentage bar is all the way across, the temp file is written out and you are prompted to insert writable media, simply click cancel.
Go to a terminal, look in your /tmp drive and you will see a file with the name like image.iso.1A2BCD  - this is the temp file written out.  Rename it to diskname.iso and you have yourself a disk image.  

Mount and play the ISO:
Make a directory called something like  /media/dvd
This is the mount point for your ISO image.
To get full menu capability in Totem you will need to start from the command line (or make a script to do the same)

sudo mount -o loop ./diskname.iso /media/dvd
totem /media/dvd

Totem will play the ISO image just as if the DVD were mounted.  Now you can take your DVDs on the road without having to carry media.

Good luck!

---

### Post by Ek0nomik on 2007-05-28
Good stuff.

You can make an official tutorial if one doesn't exist already.  :)

---

### Post by Mandrake12 on 2007-05-28
even simpler method; from terminal type:
dd if=/dev/cdrom of=/home/mydir/Desktop/filename.iso 

this will create an iso from the media in your CD/DVD rom, to play the resulting file, simply open it in vlc. (sudo apt-get install vlc)

---

### Post by taurus on 2007-05-28
You don't even have to mount it before you play it.

```
gmplayer **filename.iso**
```

---

### Post by brennydoogles on 2007-06-09
You can also create a script in your ```
.gnome2/nautilus-scripts/
``` folder called "play as dvd.sh", and inside that script put: ```
#!/bin/bash 
# script for playing iso images as dvd's
for I in "$*" 
do 
vlc "$I"
done
exit0
```

which will add a right click option to the GUI to play your DVD's without mounting them. You can also change the vlc to whatever media player you prefer.

---

