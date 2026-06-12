---
title: "Sansa fuze, libmtp and banshee"
date: 2009-05-07
forum: Multimedia Software
---

### Post by rossmoore on 2009-05-07
Hi,

I have been trying to get my Sansa Fuze to work with Banshee in MTP mode without success. I'm on Jaunty. I believe it is possible, but I think I might be missing a step - here's what I've done so far:

Plugging in the Fuze in MTP mode with Banshee running does nothing. This is because Jaunty ships with libmtp version 0.3.0, and the Fuze isn't supported until 0.3.6. If I run
```
sudo mtp-detect
```
then it begins to detect the Fuze (but not without the sudo), but the command hangs and crashes.

Then I uninstalled libmtp and Banshee. I then downloaded libmtp v0.3.6. I did a ./configure, make, and then:
```
sudo checkinstall
```
This installed the v0.3.6 versin of libmtp. If I run
```
sudo mtp-detect
```
then an error reporting that libmtp8 cannot be found is reported. This error goes away and the command completes successfully if I create a symlink in /usr/lib to the installed location (/usr/local/lib).

Then I installed Banshee using Aptitude - and it installed fine, recognising that libmtp was already installed.

Now everything seems to be in place, but Banshee (and Amarok 1.4, and Rhythmbox) doesn't notice when I plug in the Fuze.

So what am I missing? I seem to have the right version of libmtp, and Banshee seems to know it's there. mtp-detect detects the Fuze (but, as I say, only as root - is that normal?).

Hope there's a guru out there who can help,
Thanks,
Ross

---

### Post by motang on 2009-05-09
Hey bro, I ran into the same problem and really ticked me off but I couldn't really dive into the problem as my school and work was getting in the way and also my recent trip back home (India) held back from fixing it until today.

Here we go this is how I got it working on both my desktop and notebook. Ok here is how I got it working with Rhythmbox (Banshee is going to have to wait till I am done with my midterms):

[LIST=1]
[*]Launch Synaptic and search for MTP, and install MTP-tools and MTPfs 

[*]Now after those are installed on your system, launch Rhythmbox and go into Plugins under Edit and tick mark Portable Player MTP and untick mark (if it isn't already)iPod Player.
[/LIST]
Thats it, plug in your Sansa and you should be able to use it like you were back in 8.04 and 8.10.

---

### Post by motang on 2009-05-18
Alright got it working like a charm now. I think what the newest Linux kernel has done is built in full support for MP3 players that have MSC mode...or maybe it's Canonical doing it (what do I know :)). It works perfectly in MSC mode. These are the steps you need to do get it working in Jaunty:

[LIST=1]
[*]First make sure you have the latest [firmware]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=23276&view=by_date_ascending&page=1") (I think it's version 2.x.x).

[*]Now after that is done, go into the System Settings and then to USB Mode and choose MSC.

[*]After you done with that you will have full read and write to you Fuze.
[/LIST]

**Note**: Make sure you backup all your data to your hard drive as when you change over to MSC mode you can't see them when you plug in the Fuze to your computer running Ubuntu.

---

### Post by rossmoore on 2009-05-20
Hi, thanks for both your posts. I found that out of the box Banshee (and Rhytmbox) wouldn't work with my Fuze, even with libmtp and mtpfs installed. In the end I installed the latest version of libmtp (0.3.7 I think), and built a copy of banshee against that.

It looked like it worked, mostly. But if I transferred a reasonable (read dozens and above) number of tracks it would crash (the Fuze, I mean) when I went to eject it at the end of the transfer. The Fuze would then not recognise the tracks - it would see them, but slow to crawl and crash when I tried to play them.

In the end I just used the MSC connection options and gave up on MTP. I was hoping to manage the player as one big 16Gb player, not two 8Gb ones - but that seems impossible for now.

Oh well, it's working well enough for now. Would be nice to get proper synchronization of the entire player (incl. SD card) without having to manually copy etc. eventually.

---

### Post by mikezila on 2009-05-20
libmtp is usually pretty good about adding new (or in this case, new versions of old) devices.  If you can't get it to work, just give it a month or so, and it'll probably be fixed to work out of the box.

---

