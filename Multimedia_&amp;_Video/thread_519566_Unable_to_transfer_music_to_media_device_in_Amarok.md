---
title: "Unable to transfer music to media device in Amarok"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by robinl on 2007-08-07
I can't transfer music from Amarok to my SD card using its devices tab. It simply throws a transfer failed window but I can copy and paste things into and from the card without any problem. Is there any way I can fix this?

---

### Post by koshari on 2007-08-07
as far as i know the oly benifit of using amarok to transfer to a device as that amarok will update the devices database. this is advantageous for items such as ipods ect but has no real benifit to coying to an SD card.

---

### Post by koshari on 2007-08-07
oh and for the record, how are you going about it, 

try going intoi amarok properties and seeing if it will detect your sd card as a generic mp3 player, then connect the device, then drag a song from the playlist window onto the device tab, and then click transfer.

---

### Post by robinl on 2007-08-07
The reason I'm using Amarok to transfer is because of its random tracks playlist: it just take too much time to copy each song individually. Yes the SD card is recognised as a generic MP3 player, I've right click on the "50 random tracks" playlist, transfer to media device (which is connected already), and press transfer. It just throws a bunch of errors for every single file and does nothing.

---

### Post by robinl on 2007-08-10
In the end I just save it as a play list and use this script to copy it to my MP3 player, hope someone else might find it useful.
```

sed "s/#.*//g" < playlist.m3u | sed "/^$/d"[FONT=verdana, arial, geneva, sans-serif][SIZE=-1]* |*[/SIZE][/FONT] while read line; do cp "${line}" /path/to/drive/; done

```

---

### Post by iggee85 on 2007-10-13
My SD card isn't even detected as an audio player so I can't transfer to it from amarok.
But that script works fine. Thanks.

---

### Post by TrinitronX on 2007-12-09
Same problem here with a sony ericsson w810i phone with Pro stick duo card recognized as a Generic device.  How does simply transferring to a generic usb mass storage device fail?  You'd think that something as simple as that (without a database) would be easy.

It'd be nice to get amarok to manage file transfers like this simply because, finding specific songs in your music folder can be tedious to copy by hand.

---

### Post by rmroczk on 2007-12-16
I was able to get around this problem by creating a symlink in my home directory to the mount point where the device is mounted.
in my case there was a space in the original mount point directory causing the transfers to fail.

For example: ln -s /media/my\ mp3\ device /home/me/mymp3device

---

