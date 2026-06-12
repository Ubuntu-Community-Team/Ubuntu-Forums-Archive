---
title: "firefox mplayer cache problem"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by dmizer on 2006-12-19
this problem has plagued me since the very first time i tried to use mplayer back in breezy.

embedded windows media plays fine with mplayer.  it even plays okay if i force mplayer to play the video in a popup window.  this is fine for my personal use, but i need to be able to have this work correctly because i need to loan these computers out.

notes:
1) this is NOT a codec problem ... videos DO play.
2) this is NOT a problem with totem plugins ... i have removed them from the plugins folder.

the problem is that when the page first loads, mplayer IMMEDIATELY attempts to play the video, but fails.  then mplayer caches the entire video and halts at 99%.  after this, you can hit play several times and the video will eventually play correctly.

i have played with the mplayer config settings. and no amount of adjusting with the cache levels appears to make a difference.  the videos ALWAYS attempt to play without caching, then cache to 99% and stops.

also note, i can sometimes press play while the video is caching from the site, and it will play correctly (but not always)

these are identical symptoms to what i experienced in both breezy and dapper when attempting to use mplayer, and i can find no answers on this site for the problem.  everyone is satisfied with using the firefox streaming media plugin or including the "noembed=1" option.

what i need:
mplayer to cache the correct amount of the video and begin playing it correctly.  and it MUST be embedded to be satisfactory for deployment to customers.

i have also tried to make totem work, but it does not.

totem works in dapper, but i can't make it work in edgy.  totem does not attempt to play embedded video at all unless you use the firefox embedded media plugin.  otherwise totem just sits there with a gray box and does nothing (read: there is zero network activity which indicates that totem is not even communicating with the media on the site)

---

### Post by dmizer on 2006-12-21
*bump*

---

### Post by dmizer on 2006-12-21
okay ... more methodical perhaps?

here is my mplayerplug-in.conf file:
```
vo=x11
ao=alsa
cachesize=512
cache-percent=25
dload-dir=/home/dmizer
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-midi=0
enable-pls=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=0
rtsp-use-tcp=0
rtsp-use-http=0
noembed=1
```
it resides exactly as above in the following locations:
/home/dmizer/.mplayer/mplayerplug-in.conf
/home/dmizer/.mozilla/mplayerplug-in.conf
/etc/mplayerplug-in.conf

now i KNOW its reading the file at least in part because as you can see above, i have enabled the "noembed=1" option, and streaming videos always pop up in a new window.

according to the mplayerplug-in page,
> Note: value is in Kilobytes. Default value is 512
If used with the download option. This is the buffer size before the video plays.
and as you can see, i DO indeed have the download option enabled.

video still attempts to play (and of course fails) imediately.  zero cache takes place, and the mplayer window pops up and attempts to play the file.

for the love of all that is holy ... what is wrong?

---

### Post by dmizer on 2006-12-23
and ..... *bump*

---

### Post by dmizer on 2007-02-10
i finally ... FINALLY figured out how to resolve this.  video plays consistently well, and plays embedded.

install mplayer and mozilla-mplayer via the repositories (enable universe and multiverse repos)

or via automatix.

uninstall totem-xine or totem-gstreamer and/or make sure that all the libtotem references are removed from your plugins directory (firefox should be closed while you do this).

then go here: [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php) and install the mplayerplug-in-0.4.xpi firefox extention (now called add-on)

make sure that ~/.mplayer/mplayerplug-in.conf looks like this:
```
vo=x11
ao=alsa
cachesize=512
cache-percent=25
dload-dir=/home/YOURUSERNAME
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=0
rtsp-use-tcp=0
rtsp-use-http=0
```

and ~/.mplayer/config looks exactly like this:
```
vo=x11
ao=alsa
```

reopen firefox, and browse to news.yahoo.com and listen in embedded bliss.

---

### Post by dmizer on 2007-03-10
latest updates broke streaming media on every single last one of my edgy installs.  this includes:
mplayer installed from source
mplayer installed from automatix
mplayer installed from the repos.

media currently plays but is unwatchable.  VERY jumpy even if cached completely.

---

### Post by Snookered on 2007-03-11
Hi dmizer! 
Glad to see I'm not alone.
Having issues here, too. Trying to set up an old compaq w/Celeron 667 MHz, 384 ram,
and onboard video/audio. If I play the featured video (news.yahoo.com) directly, it is very choppy or no other videos show up the playlist.
If I go to "all videos" and pick CNN they play just fine.
If I pick ABC videos it gets choppy video and sound.
Mplayer is launched when a video is selected but after the video starts and right click on the screen the "About Flashplyer" pops up. Is there a conflict between Flash9 and Mplayer? Any ideas?




BTW, an opportunity to fix up some older PC's is coming up. Would like to install Linux on them. But they need to have multimedia support.

---

### Post by Snookered on 2007-03-11
Well, after a little research it seems this comp (compaq 5BW130, celeron 667,
 384 ram) isn't worth much. Back to Xubuntu and see what happens.

---

### Post by dmizer on 2007-03-11
yeah, gnome's probably a bit heavy for that machine.  xubuntu should be much better.

me on the other hand ... only one of my edgy machines with this problem has less than a 1ghz processor (and it's running xubuntu.  the rest are all over 1.8ghz cpu's with plenty of memory.

i thought maybe it was a network issue, but this happenes at multiple locations.

update:
two problems with this were:
1) my home connection was particularly slow
2) my test machine's wireless card is slow.

so even though i was trying this at various locations, i was getting the same results because of a weak card, not because of a bad player.

---

