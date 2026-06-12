---
title: "HowTo Convert (extract) VCD to DVD"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by NumPy on 2007-05-21
Hello all, 
I am sure this has been covered before in some form. However, I wanted to make a tutorial that would outline this specific area.

First off, this is a collection of information gathered from many different sources. 
Secondly you will need a few tools installed to achieve the end result. 

There may be some better UI's out there to achieve this, but I find doing things in the command line more appealing. 

Lets start by installing the right packages for the job:
```
#sudo aptitude install  ffmpeg mencoder mplayer lame ligogg
```

All this should go well, if not leave a reply 

All packages are now installed.

Lets get our movie. Insert your VCD cdrom/dvdrom into your drive, and open K3B, and select copy cd. This will make an ISO of the disk. Save this somewhere on your local drive.  Now mount the ISO.

First lets make a temporary directory to mount the iso in. 
```
# mkdir /your/home/dir/iso 
```

Change to your home directory
```
# cd /your/home/dir/
```

Mount the ISO to the directory we just created
```
# sudo mount -o loop -t iso9660 /path/where/you/saved/iso.iso /path/to/home/ISO
```

```
# cd iso 
```

Locate your MPEGAV folder and cd to it. Make sure there is a *.DAT file there, remember this path/location, we will need it shortly!

Now on to the meat of this solution/tut:

1. Convert VCD files to mpeg; you can convert as many sequences as you want. 
ffmpeg -i /path/to/your/AVSEQ01.DAT -target ntsc-dvd /path/to/your/movie.mpg;
(change the "/path/to" part to the location of your origination VCD file/image) 

2. Verify that the mpg file works: 
xine /tmp/2.mpg;

3. Create DVD structure as file dvd.xml. you can create menus, backgrounds, chapters etc. the simple structure is: 
<dvdauthor dest="/path/to/dvd/">
 <vmgm />
 <titleset>
 <titles>
 <pgc pause="inf">
 <vob file="1.mpg" />
 <vob file="2.mpg" />
 <vob file="3.mpg" />
 </pgc>
 </titles>
 </titleset>
</dvdauthor>

4. Author the DVD 
 dvdauthor -x dvd.xml

5. Burn the DVD 
growisofs -dvd-compat -Z /dev/scd0 -speed=256 -dvd-video /path/to/dvd

And thats about it.. there may be some things I will add later. This is my first tut on this forum, and my first venture in video editing, so suggestions are welcome. 

take care
~NumPy

---

### Post by theomodsim on 2008-02-26
Your instructions were very clear, worked great for me! Thanks!

---

