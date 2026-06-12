---
title: "&quot;Use Windows Media Player&quot; Error"
date: 2009-10-19
forum: Multimedia Software
---

### Post by Mariane on 2009-10-19
I have 2 avi files which are played neither by vlc (my favorite) nor by noatun. Noatun opens and closes in a loop a video window displaying the message "Use Windows Media Player" when I tell it to open one of these files. 

I tried to follow the explanations there: 

[http://ubuntuforums.org/showthread.php?t=1206679&highlight=windows+media+player](http://ubuntuforums.org/showthread.php?t=1206679&highlight=windows+media+player)

I have the mediubuntu repository in my list. There is no such package as "w32" but there is one called "w32codecs" so I installed this one. It installed correctly but made no difference. 

There are also:
mingw32
mingw32-binutils
mingw32-runtime
non-free-codecs

Should I install one of these? 

"vlc media player" mentioned in the link above is not a valid command. Vlc simply answers:
Unable to open 'media'
Unable to open 'player'

When I try to open one of the avi files vlc say rows and rows of:
[00000312] access_file access error: read failed (Bad address)

When I stop vlc it says:
(.:9333): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gsignal.c:1741: instance `0x838e888' has no handler with id `812'

(.:9333): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gsignal.c:1741: instance `0x838a3d0' has no handler with id `746'
[00000312] access_file access error: read failed (Bad address)

(.:9333): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gsignal.c:1741: instance `0x856cdc0' has no handler with id `8473'

(.:9333): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.6/gobject/gsignal.c:1741: instance `0x8579318' has no handler with id `8578'

But this is normal on my computer, I always get a few of those even after the file has been succesfully played. 

Mariane

---

### Post by MelDJ on 2009-10-19
where did you get the files from? i suspect this is a scam

---

### Post by Mariane on 2009-10-19
I got them from a torrent. mplayer also displays "Use Windows Media Player", albeit only once, and then closes saying it has reached the end of the file. 

Do you mean I should just give up on these files and delete them? 

Mariane

---

### Post by MelDJ on 2009-10-19
in mplayer, does a window pop up telling you to use windows media player? or is it on the video?
if its on the video, i am quite sure its a scam.

---

### Post by Mariane on 2009-10-19
Mplayer does not show the video at all, just just message in white on a dark background. Only stays open for a few seconds and then closes. 

And I just came across this link:
[http://forum.videolan.org/viewtopic.php?f=14&t=64879](http://forum.videolan.org/viewtopic.php?f=14&t=64879)

Which is making me rather worried - and really glad I'm using Ubuntu, also. 

Mariane

---

### Post by MelDJ on 2009-10-19
i downloaded a similar file which told me to play on wmp. i tried finding codecs and finally realized it was a fake. it was quite frustrating as i spent a long time getting it. if its not that important, i advise you to just delete it and get the file from a more trustworthy source. :)

---

### Post by kerry_s on 2009-10-19
> a video window displaying the message "Use Windows Media Player" when I tell it to open one of these files.

i mark it as fake, to me it's just like that other vix player thing.

---

### Post by Mariane on 2009-10-19
I've had connections problems twice after trying to open one of these files. I wonder if it could be related? 

I use wifi-radar
```

sudo apt-get install wifi-radar
sudo wifi-radar

```

Wifi-radar told me I was still connected but nothing seemed to go through anymore. I clicked on "Disconnect" in wifi-radar, then I selected my network and clicked on "Connect" and it worked again. I thought it was just one of these things, but as it happened twice and each time after I tried to play on of these videos I wonder. 

Should I try to open one of these videos once more to check if there really is a correlation or would that be unsafe? 

BTW I am using ktorrent and running neither ktorrent nor vlc as root, of course. 

Mariane

---

### Post by MelDJ on 2009-10-19
try making a new thread about that in the network or security section:)

---

### Post by Mariane on 2009-10-19
I tried 3 times, once each with vlc, noatun and mplayer. My connection kept running, so it looks like the trojan or whatever malicious script which may be included in the file is not affecting Ubuntu. Great. 

Thank you very much MelDJ. 

@kerry_s: what other vix player thing? Just curious. 

Sometimes I really pity all the poor people using windows. Of course there are problems with Ubuntu but they are just normal computer problems, there is not a whole buch of baddies out there deliberately doing their very best to ruin your computer. 

Dowloading an infected file under Ubuntu only results in a waste of download time, frustrating of course, but at least no damage is done to our system. 

I'm going to get a proper version of these files and I'm going to seed them for a long long time. 

Mariane

---

### Post by MelDJ on 2009-10-19
no problem:). learn more on linux malware here: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by kerry_s on 2009-10-19
> @kerry_s: what other vix player thing? Just curious. 

playvix is a media player you have to buy to play certain videos.

after you've downloaded the torrent for a little bit, just look in nautilus, it will make a thumbnail, so you don't waist your time downloading the whole thing. use a torrent site with a rating system & comments.
example of rating system & comments:
[http://www.kickasstorrents.com/avatar-2009-dvdrip-axxo-t3109238.html](http://www.kickasstorrents.com/avatar-2009-dvdrip-axxo-t3109238.html)

---

