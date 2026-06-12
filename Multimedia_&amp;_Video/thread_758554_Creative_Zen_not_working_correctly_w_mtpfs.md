---
title: "Creative Zen not working correctly w/ mtpfs"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by vemon on 2008-04-18
Hi!

I've got an almost working setup of libmtp + mtpfs which I use to transfer music to my Creative Zen player. With "almost working" I mean there is one annoying bit that doesn't work. The player isn't able to get duration of (some of) the mp3 songs which means seeking doesn't work for those tracks.

I tried to put the same mp3's to the player using Windows and the the seeking works. I even copied a "broken" mp3 file from the player to Windows and then back to the player and after that the seeking worked and the player was able to tell the duration of the song. It looks like the problem isn't in the mp3 files but in the way libmtp/mtpfs transfers the files.

System info:

I'm using libmtp + mtpfs from [http://ubuntu.jbbr.net/](http://ubuntu.jbbr.net/) on Ubuntu Gutsy. The firmware of my Zen is 1.21.01. The mp3's which wouldn't seek when transferred using mtpfs were 256kbps CBR.

- Jaakko

---

### Post by mif86 on 2008-05-31
I'm having the same problem, almost...

Until I stopped using gphoto2 and started using libmtp for transferring, I was also not able to seek the mp3 files i had transferred, but it works now.
Although I am still unable to seek video files that i transfer using libmtp...

I've also tried copying the files back from the device to my computer using libmtp, and they play fine on the computer, and they are the same size as the originals, so it seems they are bit-for-bit-identical (although haven't tried diff.)

And not only am I unable to seek through them, most videos finish playing too early (about 10% too early, it seems.)

Got the same firmware as you, and videos are encoded XVID AVIs with mp3 sound through mencoder.

---

### Post by vemon on 2008-06-01
How exactly are you using libmtp (or mtpfs?) to transfer your music? I've only managed to get zen to understand the track length either by:

1) Using mp3 files with ID3v2 tags containing the "TLEN" (track length) attribute or adding it myself using eyeD3 before transferring the tracks using libmtp. Apparently libmtp is able to read the "TLEN" and uses it to inform zen about the track length instead of the "Xing header" (which is a pretty standard way).

2) Transferring the tracks using Gnomad2 (works great and hasn't crashed a single time!) This method doesn't need any tampering with the TLEN attribute since Gnomad2 is able to inform the track length to zen by using the mp3 files "Xing header".

- Jaakko

---

