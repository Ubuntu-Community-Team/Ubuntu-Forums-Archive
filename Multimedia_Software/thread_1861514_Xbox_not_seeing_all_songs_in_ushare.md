---
title: "Xbox not seeing all songs in ushare"
date: 2011-10-15
forum: Multimedia Software
---

### Post by Chewy2 on 2011-10-15
So I just configured ushare and got my computer displaying on my xbox, but it only displays a limited amount of songs. At first it was only displaying 50(some of them not actually songs but album art etc), but I reset my computer and ran it again and now it's displaying 500.

Also the metadata is messed up, it displays song name under artist, genre, and everything. This part isn't really as big of a deal.

This is what I get when I run it with ushare -x:

```
ryan@ryan-laptop:~$ sudo ushare -x 
Interface eth1 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.69:49201
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/Users/Ryan/Music
Looking for files in content directory: /home/Users/Ryan/Downloads
Found 9405 files and subdirectories.

```

So it says that it found 9045 files, but it is only displaying 500 of them. Anyone know what is causing this?

These songs are also the ones that are in the first few folders of the first directory (/home/Users/Ryan/Music)

---

### Post by Chewy2 on 2011-10-17
So I merged both of my music files into one directory because I read that ushare sometimes has trouble with multiple directories. 

No luck though, still exactly 500 songs showing up, just a different selection of them.

---

### Post by kerry_s on 2011-10-17
You have to reload ushare every time you change something(add/remove), i use the web ui. 
[http://the.machine.address:49200/web/ushare.html](http://the.machine.address:49200/web/ushare.html)

You can also just do "sudo service ushare restart".

---

### Post by Chewy2 on 2011-10-17
Yes I have reset it many times with no luck. Always only 500 songs displaying, sometimes only 50.

I find it really weird that it's such an even number, like there has to be something limiting it somewhere.

---

### Post by Chewy2 on 2011-10-17
Bump. 

It's back down to 50 again...

---

### Post by Chewy2 on 2011-10-22
One more bump...

---

### Post by dopple on 2012-02-26
I could also do with an answer to this one. Only shows the first 50 songs. Also doesn't display metadata for the mp3 files like artist, album & genre. Not sure if that's related.

---

### Post by ajaygautam1981 on 2012-03-02
Hi,
I am able to see the list of available media file at [http://mymachineip:49153/web/ushare.html](http://mymachineip:49153/web/ushare.html),
But now i am unable to open these media files via [http://mymachineip:49153/web/xyz.mp4](http://mymachineip:49153/web/xyz.mp4).
I have set USHARE_DIR in My config file is 
USHARE_DIR=/share
So please help me to get the absolute URL of these files, where i have to change in ushare code to get this.


Thank
Ajay Gautam

---

