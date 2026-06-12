---
title: "minidlna file display"
date: 2010-10-05
forum: Multimedia Software
---

### Post by Geffers on 2010-10-05
My Sony Bravia TV finds my minidlna server OK but if I browse for video files I get the message 'There are no items to display'

I am trying an mp4 video which plays fine on the TV via the USB key

I assume I am reading the default directory correct as /opt which I have not changed in the minidlna.conf file as I do not want to complicate matters until I understand the directories but of course /opt may be wrong.

Any advice appreciated.

Geffers

---

### Post by j0nny on 2010-10-08
Hi

I've also have a sony bravia tv and I have miniDLNA working with it, there are just a couple of things you will need to know

1) miniDLNA only serves up MPG videos to your TV. Any other format will be skipped and not displayed. If you want to watch other video formats you need to transcode them to MPG first using ffmpeg (a simple example would be "ffmpeg -i test.avi -target ntsc-dvd test.mpg" to convert the avi to mpg). Something like mediaTomb can transcode on the fly but unfortunately it doesn't work with sony bravia TVs
2) miniDLNA needs to be told where you videos are stored. when you install minidlna you'll probably have copied the minidlna.conf to /etc. In this file set the media_dir directory to where ever your files are (remember only mpg will be served up)
3) the miniDLNA server will create a local database of available files that you will see on your tv. This database will be in the directory you specify in db_dir minidlna.conf -> I set mine to "db_dir=/opt/minidlna". If you add new files to your collection you'll need miniDLNA to refresh the database it maintains. To do this you start miniDLNA with "-R" and it will delete the directory and add all the files again.

a typical startup line would be
sudo mindlna -R -f/etc/minidlna.conf

to see what minidlna is doing have a look at the log files, which will be in the same directory as specified by db_dir
tail -f /opt/minidlna/minidlna.log

---

### Post by Geffers on 2010-10-08
> **j0nny said:**
> Hi

1) miniDLNA only serves up MPG videos to your TV. Any other format will be skipped and not displayed. If you want to watch other video formats you need to transcode them to MPG first using ffmpeg (a simple example would be "ffmpeg -i test.avi -target ntsc-dvd test.mpg" to convert the avi to mpg). 

to see what minidlna is doing have a look at the log files, which will be in the same directory as specified by db_dir
tail -f /opt/minidlna/minidlna.log

Thanks for good explanation.

My video files were all mp4, I thought as I am able to play these on the Bravia using the USB key that the dlna server would play them.  The mpg worked fine.

So is it minidlna that cannot serve other video formats or is it the Bravia's client that cannot receive them.

My conversions using ffmpeg seem to be taking longer than real time, not sure if converting to pal-dvd is slower than ntsc

Geffers

---

### Post by j0nny on 2010-10-09
Geffers> 

So is it minidlna that cannot serve other video formats or is it the Bravia's client that cannot receive them.



My understanding is its a Sony Bravia limitation (and other common DLNA clients), and that minidlna was built with the limitation in mind - no point in serving up content that can't be displayed!

transcoding does take a while, especially if you have a backlog. There are plenty of scripts out there than can help batch it up. Another issue you'll face is the size of the files generated .....

---

### Post by Geffers on 2010-10-09
> **j0nny said:**
> Geffers

My understanding is its a Sony Bravia limitation (and other common DLNA clients), and that minidlna was built with the limitation in mind - no point in serving up content that can't be displayed!


Fully understandable but the Bravia plays mp4 videos fine via the USB key.

The annoying thing is some BBC iplayer programs I download end up as mp4 files, which as mentioned play fine through the USB key but not via the  dlna server.

Geffers

---

### Post by handheld-penguin on 2010-12-30
I've had my bravia play avi file fine over windows shares...I guess doing live transcoding.

Out of this massive list ([http://www.rbgrn.net/content/21-how-to-choose-dlna-media-server-windows-mac-os-x-or-linux](http://www.rbgrn.net/content/21-how-to-choose-dlna-media-server-windows-mac-os-x-or-linux)) is minidlna the only one that works with Bravia? Why doesn't mediatomb work?

Fuppes apparently does live transcoding, does anyone know if that works? I'm going to give it a go now.

It really isn't usable having to transcode all my videos to mpg!

EDIT: Fuppes didn't work after much agony. A very useful thread here concerning Bravias. ([http://www.avforums.com/forums/lcd-led-lcd-tvs/1026920-bravia-w5500-dlna-compatibility.html](http://www.avforums.com/forums/lcd-led-lcd-tvs/1026920-bravia-w5500-dlna-compatibility.html)) I guess I will have to stick to Windows for streaming

---

### Post by Hecxa on 2011-01-01
Getting a bit annoyed here, set up the server but unable to show even JPG pictures. All I get is message "There is no items to show". I am able to browse folders though. Did everything by the "book" and installation went fine.

and... How do I change the logo/icon for minidnla? Kind of annoyed with that sitting penguin...

uShare was working fine with PS3, but I would like to use minidnla at least to show 
pictures directly from Bravia.

- Sony Bravia + PS3 + Ubuntu

---

### Post by handheld-penguin on 2011-01-01
I just found this which might be of some use... [http://sourceforge.net/projects/minidlnawebmin/](http://sourceforge.net/projects/minidlnawebmin/)

---

### Post by Hecxa on 2011-01-01
> **Hecxa said:**
> Getting a bit annoyed here, set up the server but unable to show even JPG pictures. All I get is message "There is no items to show". I am able to browse folders though. Did everything by the "book" and installation went fine.

and... How do I change the logo/icon for minidnla? Kind of annoyed with that sitting penguin...

uShare was working fine with PS3, but I would like to use minidnla at least to show 
pictures directly from Bravia.

- Sony Bravia + PS3 + Ubuntu

I'll answer to my own message. Dunno why, but manually removing cache directory and restarting minidlna resolved my problem not seeing any pictures... minidlna was for reason unkown just not caching the files.

---

