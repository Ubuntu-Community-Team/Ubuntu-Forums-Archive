---
title: "Can't get DVD's to play in VLC or any other player"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by gubemton on 2007-10-20
Hi,

I just installed Gutsy. It's my first time with linux so I am a noob. so far with all the Tutorials available here and other places online I have been able to blundeer through mostly everythign I needed to set things up the way I like. BUT no matter what I do I cannot get DVD's to play.

I know this is a question asked 100 times a day and I know there are millions of tutorials out there already, but i just spend the last 6 hours following them over and over and over, and nothing happens. I must have installed and uninstalled xine, gstreamer, libdvdread3, and libdvdcss2 a hundred times already.

From what I've read the totem movie player has trouble with dvd's, so thats why I got vlc. VLC plays not retail dvd's fine with no problems at all. but if I put a retail dvd in, it doesn't do anything.

in totem it says I don't have the right plugins. If i put xine and run totem it says it can't be played and asks if i am trying to run the dvd with out libdvdcss2 installed.

libdvdcss2 IS installed, so is libdvdread3, and the ubuntu restricted plugins, and extra codecs for gstreamer. someone PLEASE help me. I am going CRAZY, and if i can't watch dvd's then I am going to have to switch back to windows...

---

### Post by gubemton on 2007-10-20
bump

---

### Post by bakster on 2007-10-20
Are you using medibuntu repos?Try kaffeine and libxine-ffmpeg:on first start it will check if DVD playback is properly installed.

---

### Post by gubemton on 2007-10-20
yup, i'm using the medibuntu repos. I will try kaffeine now. thank you for responding.

---

### Post by gubemton on 2007-10-20
thank you for your response bakster..i think i am finally getting somewhere. this is the message i get from kaffeine: Can't check DMA mode. Permission denied or no such device: "/dev/dvd".

know what I should do?

---

### Post by bakster on 2007-10-20
It seems that your dvd-rom is not detected and/or not working in dma mode.Try using this command in terminal: 
 ```
sudo hdparm /dev/hdd
```
Output should look something like this

 ```
/dev/hdd:
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)

```
 You may need to replace /dev/hdd with /dev/hdc.Check in your /dev/ folder.Search forums for cd-rom/dma troubleshooting.

---

### Post by El Zoido on 2007-10-21
Stupid question: Did you try another DVD?

I had similar problems (and still have in Totem), even VLC wouldn't work at first.
Took me some time to find libdvdcss2 in the medibuntu repository.
Furthermore I installed libdvdplay0 (not in the repositorys unfortunately, but a search in the forums should provide a link). Presumably it shouldn't be necessary anymore though.

After that it still didn't work, but I then changed the DVD and suddenly Totem started playing the movie (not the menus though). VLC is working fine now, menus included.
Probably due to unmounting/mounting the drive again?

---

### Post by gubemton on 2007-10-21
ok I tried the hdparm command and it kept saying "no such file or directory", so I googled around a bit and found out that my devices are named scd0 and scd1.

after I found that our I would get this:

/dev/scd0:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

after some more reading and trying stuff out, I can't get this thing into dma mode. I've tried other commands, and I tried adding the dma: on text string to the bottom of the list, and nothing works. I still get the same thing.

is anyone else having problems like this? This only effects Retail dvd's, my "backups" work perfectly.


El Zoido: I've tried different dvd's, all with the same result. what is the libdvdplay0 you were talking about?

---

### Post by gubemton on 2007-10-21
Guys, I have no idea what I did, but somehow the dvd's are working now.

totem still gives an error and wont play anything but vlc works fine.  THANK YOU BOTH SO MUCH FOR YOUR HELP.

you can't know how much I appreciate it. I know that there are thousands of other new converts from windows all with the same questions as me, so I appreciate you taking the time to pick me out of the bunch and help.

---

