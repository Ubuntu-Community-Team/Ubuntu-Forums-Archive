---
title: "cdg to mp3+g  converter in ubuntu?"
date: 2011-05-31
forum: Multimedia Software
---

### Post by throatgorge on 2011-05-31
Hi, I had some software for creating CDG files for karaoke but at the bar the DJ's computer only runs mp3+g.  I only found one application that converts in windows, but it costs too much and now that I'm using linux, I figure if it exists it might be free.
Not much luck finding any linux karaoke software.
What about a CDG player that will function without installation; the bar owns my DJ's computer so I can't install anything-- plus it's a windows machine.

---

### Post by andrew.46 on 2011-06-01
> **throatgorge said:**
> Not much luck finding any linux karaoke software.

I do not know much about this format but I note that the latest MPlayer plays cdg files (with a few problems) while the latest vlc appears to play the same files quite well, screenshot attached. Not sure if this is any help to you though....

---

### Post by GeoMX on 2011-06-04
> **andrew.46 said:**
> the latest MPlayer plays cdg files (with a few problems)
My Mplayer version does not seem to play cdg files.
Where could I find information about this feature? (Haven't found the correct site)

---

### Post by andrew.46 on 2011-06-04
> **GeoMX said:**
> My Mplayer version does not seem to play cdg files.
Where could I find information about this feature? (Haven't found the correct site)

You can test your copy of MPLayer as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i 'cdg'[/COLOR]**
ffcdgraphics ffmpeg    working   FFmpeg CD-Graphics  [cdgraphics]

```

and if you come up empty you will need to upgrade. You can have a shot at building your own:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

or try this PPA:

MPlayer Daily Builds 
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

Getting vlc to work in this way is a slightly more complex proposition...

---

### Post by GeoMX on 2011-06-06
I've added the PPA and now I can play cdg files, thanks a lot for your help :).

---

### Post by andrew.46 on 2011-06-06
> **GeoMX said:**
> I've added the PPA and now I can play cdg files, thanks a lot for your help :).

No problem, good to see the issue resolved for you!

---

