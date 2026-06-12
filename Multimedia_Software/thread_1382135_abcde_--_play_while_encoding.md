---
title: "abcde -- play while encoding?"
date: 2010-01-15
forum: Multimedia Software
---

### Post by PGScooter on 2010-01-15
Hi,

(1) I'm wondering if there is a way to have abcde play the songs while it is encoding? I understand that this would be a lot slower.

(2) Is it possible to have abcde start playing right after it finishes ripping the first track and then have it add on the other tracks to the playlist as it rips them.

Is there anyway to do one or both of these from the command line or with abcde's built-in options?

Thank you

---

### Post by slakkie on 2010-01-15
I just start start mplayer and listen to the music as it is doing it thing..

I listen to the ogg, not the CD btw :)

---

### Post by andrew.46 on 2010-01-16
Hi PGScooter,

I suspect you are after the post__read function of abcde:

> 
post_read
   post_read  ()  is  a  shell function which is executed after the
   CDROM is read (and, if applies, before the CDROM is ejected). It
   can  be used to read a TOC from the CDROM, or to try to read the
   DATA areas from the CD (if any exist).  The default function  is
   empty


but I have to say that this is an area of abcde that I have never investigated...

Andrew

---

### Post by PGScooter on 2010-01-17
Hi guys, thanks for the replies

slakkie, that's the kind of thing I want to do. But it is kind of inefficient because you have to keep adding the newly ripped ogg's to the queue.

andrew.46
that's very close to what I want. I want a command that can be executed after each track is ripped. The command would be a command to my music player that says "add this song to the queue". Is there a post_read_track or something like that? thanks

---

### Post by mc4man on 2010-01-17
The post read command, while it certainly can work, (with a player that can be addressed as such - amarok 1.4, audacious can), is, as it stands,  run after the disc read is complete, not track read.

So not much to be gained there other than auto playing your encodes or I guess the temp. .wav's if you've set abcde to not delete or just starting the player on the cd itself.

Plus the command would need to include the path to the dir. holding the files  - known for the encodes prior R&E, not so for the .wav's
( unless you find some other means to tell the player where the files are

---

