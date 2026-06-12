---
title: "Synch Music playlists to Android phone via Wireless"
date: 2011-06-20
forum: Multimedia Software
---

### Post by mindwalkr on 2011-06-20
Hi guys,

Been happily using Ubuntu for the past 2 months now! Also recently I got an Android phone. I wonder what are my options to synchronize Music via wireless.

When I plug in the phone via USB cable, it auto-mounts and most media players (such as Banshee and Clementine) will automatically recognize the phone as a media device and offer to manage it themselves.

Now, I am able to install an FTP server on my android device. Using CurlFTPFs I am able to mount this server as a regular mount point in the filesystem. I haven't actually tried it but I'm pretty sure Banshee or Clementine will not recognize my Android phone running FTP via Wifi as a media device.

I found on the web that you can create a file on the root of the FTP server called .is_audio_player
This file will be recognized by Banshee and Rythmbox. I guess using this method Banshee will then recognize my FTP server on the Android phone as a media device and work just like via USB.

... however this will not work with Clementine.. which isn't a real biggie but this brings me to a bigger question: what exactly happens when you mount a USB device (such as an iPod, or a phone) that tells the system that it is a media device ? Can you somehow mock this behavior when setting up the mountpoint with CurlFTPFs to get the same treatement out-of-the-box, just as if you'd have plugged it with a USB cable ?

Thanks for any hints / pointers guys :)

---

