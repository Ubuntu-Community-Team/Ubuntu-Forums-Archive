---
title: "I hate itunes! need solution for m4v"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by toddr on 2006-11-11
I hate itunes! I started with Ubuntu in March of this year and I love it! I still have a windows partition just for itunes/ipod. I am tired of itunes locking my collection of music and videos (I PAID for!) into their proprietary format. I am ready to make the move. I want to delete windows and itunes along with it! The only problem is the mp4 and especially the m4v (encrypted video format from itunes store) videos I own. I want to decrypt or unencrypt or whatever these videos. Does anyone know of a linux solution for this? I really would hate to lose my music and videos. I can burn the music to a cd, but you lose quality that way. Any thoughts?

---

### Post by dorme1 on 2006-11-11
I would say use hymn, but that doesn't work if you're running anything newer than itunes 6. I think your best bet would be rip to cd. I recently converted to linux myself, it's a bit more work, but you do learn a lot along the way and I find myself more relaxed while using the computer for some reason.

---

### Post by toddr on 2006-11-13
I agree. Linux is so much more peaceful than windows. Unfortunately I have itunes 6.2. I checked out Hymn, but it doesn't convert videos purchased from the itunes store. I found a program that does do the conversion, but it costs 30 bucks. These videos aren't worth paying an extra $30. Thanks for responding.

---

### Post by EtniesBMX on 2007-02-25
I am facing the same problem. I noticed this thread is from Nov '06. Is there any new news on unlocking these files?

---

### Post by offchance on 2007-05-02
Does anyone have anything new on this? There seems to be lots of programs that will rip dvds to ipod format, but I have yet to find a program for linux that will convert avi [etc] files into m4v. If anyone has any news on this please post!

---

### Post by fakie_flip on 2007-05-02
> **offchance said:**
> Does anyone have anything new on this? There seems to be lots of programs that will rip dvds to ipod format, but I have yet to find a program for linux that will convert avi [etc] files into m4v. If anyone has any news on this please post!

Yes, there is a program that can convert video formats and re-encode video. Probably the best one for that is Avidemux. I think the package name in Synaptic/Apt-get is called avidemux2. Last time I used it, it was. If you want to go commando style, then you can use MPlayer's Mencoder.

---

### Post by fakie_flip on 2007-05-02
> **toddr said:**
> I hate itunes! I started with Ubuntu in March of this year and I love it! I still have a windows partition just for itunes/ipod. I am tired of itunes locking my collection of music and videos (I PAID for!) into their proprietary format. I am ready to make the move. I want to delete windows and itunes along with it! The only problem is the mp4 and especially the m4v (encrypted video format from itunes store) videos I own. I want to decrypt or unencrypt or whatever these videos. Does anyone know of a linux solution for this? I really would hate to lose my music and videos. I can burn the music to a cd, but you lose quality that way. Any thoughts?

You should install grip and vorbis-tools to rip and encode your music. There is also cdparanoia for those who like the command line. Vorbis-tools includes oggenc which can be used from the cli or from the gui of G-Rip. Don't buy  proprietary music and video made by people who want to control everything. Those kinds of things are against open source and should be boycotted. Instead you should encode your music to something that is a free open source high quality format such as ogg vorbis (music) and theora (video) and works out of the box with most Linux distros including Ubuntu. Unfortunately you probably bought something with firmware that does not support those unless you install Linux on your ipod. One way to get your music to another format is to burn the music to cds, and then rip or rip+encode them from the cds back into Linux. If you must have mp3, use lame in Linux with Grip unless you don't want to use a gui, then get lame only. But why waste all those blank cds if you don't have to? I was thinking that there must be a way to burn the music to a cd image iso and then mount that image so the computer sees the mouted iso as an audio cd in a cd drive, and then rip+encode from that. Daemon tools lets you mount isos into virtual drives on Windows and in Linux, it is easy to do with the mount command for example "mount -o loop my_music_album.iso /media/cdrom0". There is also a gui program made in gtk that can mount isos if you can't figure out how to do it with the command.

---

### Post by krpnm on 2007-08-20
Try this -- rename the '.m4v' file to a '.mp4'.

It has worked for me.

---

### Post by wesswei on 2008-01-30
in case anyone is still looking...

PYmusique and sharpmusique are itunes store alternatives, but may lack variety of media.

Right now* there is no way (that I know) of playing apple's drmed music or video without "converting." 

For converting you need a program like tunebite or soundtaxi, which are windows executables. Really this just plays back the video and audio and captures the output to a new file.

As for ripping I use handbrake on linux, mac, and windows. you can choose mp4 as output and specify settings for ipod or psp, etc. I use this for dvds. 

I wish someone would find a way to emulate the apple drm unlocking, I read somewhere that the drm is connected to pc name/bios/windows/mac id... if there was a way to emulate that information somehow while being played thru vlc or mplayer, we'd be golden on the playing end.

---

