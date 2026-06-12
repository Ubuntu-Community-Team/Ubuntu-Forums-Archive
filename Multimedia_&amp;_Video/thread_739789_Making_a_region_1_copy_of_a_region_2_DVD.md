---
title: "Making a region 1 copy of a region 2 DVD"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Replicon on 2008-03-30
Hi all,

I have this one region-2 DVD that I'd like to rip, and burn as region 1 so I can play it on my home theater system.

Do i need to set my laptop DVD drive's region with regionset for it to work, or does dvd::rip bypass that entirely? I am able to just playback the DVD on my old windows xp laptop (from dell) without having to do anything, so presumably, this should be an easy thing to do. Is it as simple as just flipping some config switch while ripping the image to make it rip it into something that will burn into a region-1 image, or does it get more complicated?

I heard you can only set the region of your drive X number of times, and I really don't want to do anything so permanent to my drive...

---

### Post by xc3RnbFO8P on 2008-03-30
If you got all the codec installed, DVD::RIP should do it:
>  sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

> sudo apt-get install w32codecs

> sudo apt-get install libdvdcss2

> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

[http://en.wikipedia.org/wiki/DVD_region_code]("http://en.wikipedia.org/wiki/DVD_region_code")

And if you got Dvd player with region code: [http://www.videohelp.com/dvdhacks]("http://www.videohelp.com/dvdhacks")

---

### Post by mc4man on 2008-03-30
As soon as you rip the title it becomes 'all region' -  as in 
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8
Your only issue will be format - if it's a pal title (most region 2's are) ripping, normal processing, and burning won't change that - it will still be pal format.
If your standalone player doesn't do pal<>nstc conversions it won't play the backup (without doing a pal>ntsc conversion while reencoding)
Pc's are able to display both formats

---

### Post by Replicon on 2008-03-30
Ok cool. I assume my drive is region-free, since it's a new serval performance, but how do I check just to be sure?

Then the question becomes whether I can do the conversion with dvd::rip :)

It looks like in order to burn it, I'll need something like tovid (unless DVD::Rip can actually just rip directly to iso of the right format, in which case the default burning options should just work).

---

### Post by mc4man on 2008-03-30
I've purchased a fair # of region 2's and for a while did the convesion for watching on the tv. To do a good job is somewhat involved and in any event I was using windows. There are probably some apps that have a '1 click' option to do so, there is even an .ifo hack (simply editing video_ts .ifo to mark as ntsc).In all these cases some people swear by, others don't, sort of a quality is in the eye of the beholder thing.
Myself I just went out and bought a good upconverting standalone that also did pal<>ntsc conversions.
Sometimes _cheap_ standalones will also work even though not advertised as such.
Note that this usually isn't an issue in europe as most players and or tv's can handle all of the common formats.
here is an imformative post concerning ntsc>pal in linux - somewhat dated but the basis is valid
[http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/6883-legitimate-dvd-copying-pal-ntsc-conversions.html](http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/6883-legitimate-dvd-copying-pal-ntsc-conversions.html)   #4

---

### Post by Replicon on 2008-03-30
Thanks, that link looks extremely useful and I'll check it out in greater detail soon.

Come to think of it, since this is an old cartoon from the 80s or so, qulity isn't exactly something I'm too worried about (so long as it doesn't too too much worse), meaning I could probably rip it to just a regular VCD format and I'll be happy with it.

cheers

---

