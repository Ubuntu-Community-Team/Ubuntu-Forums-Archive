---
title: "Help choosing a portable mp3/mp4 player with video with Ubuntu."
date: 2009-07-10
forum: Multimedia Software
---

### Post by tmcarson1 on 2009-07-10
I would like to purchase a portable mp3/mp4/video player, like an ipod or zune that will allow the conversion and transfer of videos to the player.

I briefly tried this with a friends Ipod using gtkpod and I couldn't figure out how to get videos onto it, only music.

Anyone currently using a portable media player with ubuntu and able to sync videos/video podcasts over to it?

I am familiar with how to get music and audio podcasts onto a device in ubuntu, just now I need to buy one that supports some type of video playback.

Any thoughts are greatly appreciated.

---

### Post by NoBugs! on 2009-07-22
iPod and Zune players are said to not work very well with Linux.
If you get a player that works as a standard usb storage device instead of using libmtp, or a player that uses an sd card, it's almost guaranteed to work, since all systems should be able to use standard usb-drives and sd card readers.

---

### Post by spamjim on 2009-11-19
I stumbled on to this thread while looking for suggestions of a player to give someone as a gift. The previous comment about the ipod not working well with Linux seems to be a bit off. I've been using my ipod with Ubuntu for quite a while without problems. I just make a playlist in gtkpod and drag video files on to the gtkpod window.

You may have problems if your video files are not encoded to work on ipod (or whatever player you choose). I like to use 'handbrake' to convert to the right video format.

---

### Post by DouglasCaixeta on 2009-11-30
Linux users don't use MP4 Players?? This topic should be on fire.

I also want to buy one, but I don't know if will work in Ubuntu.

Someone has the Phillips GoGear working on linux?

---

### Post by andrea000 on 2009-12-01
zen players are said to work well with libmtp
and linux in general.You can look at [libmtp]("http://libmtp.sourceforge.net/index.php")
project and check for compatibility of the player
to work with libmtp but just because it doesn't
say it will doesn't mean it will not it may just
mount as a hard drive.

---

### Post by Drezliok on 2009-12-01
> **DouglasCaixeta said:**
> Linux users don't use MP4 Players?? This topic should be on fire.

I also want to buy one, but I don't know if will work in Ubuntu.

Someone has the Phillips GoGear working on linux?

I have a GoGear SA6145, currently it fails to stay connected. MTP [Music Transfer Protocol] is a Microsoft protocol and libmtp is trying to fill the gap. Unfortunatly libmtp is in version 1.0.1 now and Ubuntu's package is using 0.3.7.

I just posted about getting my newly compiled version 1.0.1 to work with my sync software [Rhythmbox] but I haven't heard anything yet.3


Ipod Classic is the way to go, my wife has one and it works great and doesn't use MTP

---

