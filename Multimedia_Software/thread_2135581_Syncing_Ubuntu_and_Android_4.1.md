---
title: "Syncing Ubuntu and Android 4.1"
date: 2013-04-14
forum: Multimedia Software
---

### Post by CaptinGoogle on 2013-04-14
Hey all,

I have recently purchased a Samsung Galaxy Victory with Virgin Mobile. It's a pretty neat phone and my first time using an Android device. One particular thing I was looking forward to with this phone was syncing my music with greater ease than my old iPod Touch. Turns out I was wrong and it's actually become somewhat more difficult.

In trying to synchronize my music I set the phone to connect to the computer using the PTP connection so it would be recognized as a camera. If Banshee manages to recognize that there is in fact a device connected it will not show me any of the music that I previously synchronized with Banshee.

Edit: I'd also like to note that when I connect the phone to my computer Ubuntu recognizes two separate devices. One I assume is the phone's internal memory and the other being the Micro SD card. When I search the Micro SD card there is a directory labeled 'Music', which is empty. When I search the mounted Android file system there is also a directory labeled 'Music' with many sub-directories with the names of the artists I listen to but there is no music stored there, just the album art. This being so I assume the real problem is Ubuntu here and not just Banshee, or Banshee at all for that matter.

This seems to be the only issue with managing my music thus far.

I would be greatly appreciative if someone can help me with this.

-Vin

---

### Post by cwsnyder on 2013-04-14
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html) is one answer for 12.04.  mtpfs is another which may work.  These will work, if they do, with your phone connected via USB.  Also check out [http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html) .

You may also want to try the AirDroid app or KiesAir app from your phone, but these work _only_ over WiFi.

Another WiFi alternative is to install an FTP server app (I use RapFox) and Filezilla on your Ubuntu logged in over the FTP app to share files.  Warning: FTP does not check for codecs and allows you to copy files which you may not be able to play on your Android 4.+ device.

---

### Post by CaptinGoogle on 2013-04-14
Thanks for replying!

I tried your first suggestion but that got me nowhere. I upgraded Gvfs and now Ubuntu can read the card, but cannot play any of the music on the device. Also, opening Banshee causes the device to auto-unmount and makes Banshee crash.

It's times like these that I wish the Ubuntu Phone were out and full-featured.

Edit: If I allow the device to stay unmounted and then open Banshee, the phone will appear and so will the playlists. However, I cannot see the music in the main 'Music' directory. I can see all the music listed in the playlists but I am unable to play them.

---

### Post by CaptinGoogle on 2013-04-14
Hey all,

So after testing everything the best way to I have found to get your music onto your Android 4.+ phone is transfer music directly to your Micro SD card, if you have one. You can export all of your Playlists to '.m3u' and put it in /media/SD Card/Music/Playlists/

---

