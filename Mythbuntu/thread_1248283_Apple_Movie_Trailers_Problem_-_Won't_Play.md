---
title: "Apple Movie Trailers Problem - Won't Play"
date: 2009-08-24
forum: Mythbuntu
---

### Post by zobcat on 2009-08-24
I'm not sure what's wrong here. This is my third install of Mythbuntu 9.04, but the first install was the only one that would allow use of Apple Movie Trailers. I used the same machine all three times. I have w32codecs, libdvdcss2, and ffmpeg enabled through Mythbuntu Control Centre and I have xubuntu-restricted-extras installed. It's very frustrating, because I was able to view these trailers through MythTV on the first install right out of the box (it seemed).

Here is the output:

```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) X2 250 Processor (Family: 16, Model: 6, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing http://movies.apple.com/movies/magnolia_pictures/theburningplain/theburningplain_480p.mov.
Resolving movies.apple.com for AF_INET6...
Couldn't resolve name for AF_INET6: movies.apple.com
Resolving movies.apple.com for AF_INET...
Connecting to server movies.apple.com[65.117.152.66]: 80...
Cache size set to 16384 KBytes
Cache fill:  0.00% (85 bytes)   
MOV: Reference Media file!!!
MOV: Reference Media file!!!


Playing http://movies.apple.com/movies/magnolia_pictures/theburningplain/theburningplain_h480p.mov.
Resolving movies.apple.com for AF_INET6...
Couldn't resolve name for AF_INET6: movies.apple.com
Resolving movies.apple.com for AF_INET...
Connecting to server movies.apple.com[65.117.152.51]: 80...
Resolving www.apple.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.apple.com
Resolving www.apple.com for AF_INET...
Connecting to server www.apple.com[17.251.200.32]: 80...
Cache size set to 16384 KBytes
Cache fill:  0.10% (16384 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)
```


I found that this avisynth.dll does not need to exist on my machine, it is apparently a default error message. I also found a fix for Mplayer (nothing to do with mythtv). You have to add -playlist to Mplayer like so:

mplayer -playlist [http://movies.apple.com/movies/magnolia_pictures/theburningplain/theburningplain_480p.mov](http://movies.apple.com/movies/magnolia_pictures/theburningplain/theburningplain_480p.mov)

However, that doesn't even work for me either. Mplayer just tries to connect to dozens of different apple movie trailer IP addresses and eventually fails.

I just filed the bug with mythtv.org: [http://cvs.mythtv.org/trac/ticket/6901](http://cvs.mythtv.org/trac/ticket/6901)

If anyone has run into a solution for this, please share the wealth.

---

### Post by movieman on 2009-08-24
Apple changed their web site, and the script is broken for the moment. Hopefully it will be fixed soon; apparently it needs to use a QuickTime user agent to access the files because Apple have blocked any other access.

---

### Post by jyavenard on 2009-08-24
it has been fixed already ...

---

### Post by zobcat on 2009-08-24
It's been fixed? How do you mean? I still can't access the trailers.

---

### Post by Niels Langendorff on 2009-08-24
Not working here either. Tried on my Mac, and the HD gives invalid URL, a normal video gives a question mark in a quicktime window

<edit> See [http://discussions.apple.com/thread.jspa?messageID=10033381](http://discussions.apple.com/thread.jspa?messageID=10033381) and [http://www.hd-trailers.net/blog/2009/08/20/direct-download-links-from-apple-are-not-working/](http://www.hd-trailers.net/blog/2009/08/20/direct-download-links-from-apple-are-not-working/) </edit>

---

### Post by hackmeister on 2009-08-25
Blame Apple. Bunch of freedom haters. :)

---

### Post by jyavenard on 2009-08-25
> **zobcat said:**
> It's been fixed? How do you mean? I still can't access the trailers.

Get the latest version of mythapple-trailers
[http://www.mythtv.ukpc.net/mythappletrailer-0.4.2.3.tar.gz](http://www.mythtv.ukpc.net/mythappletrailer-0.4.2.3.tar.gz)

---

### Post by movieman on 2009-08-29
BTW, if you prefer watching the Apple trailers in Mythstream, here's how to fix it:

cd /usr/share/mythtv/mythstream
sudo vi player.xml
search for '-identify'
add a section before or after that one:

```

      <item>
        <name>-user-agent</name>
        <value>QuickTime/7.6.2</value>
      </item>

```

Save the file and restart mythfrontend (may not be required, but might as well be safe).

Job done.

---

### Post by bbruenfl on 2010-01-17
I have mine setup to download 1080p versions to /var/lib/mythtv/trailers (as opposed to streaming)

To get around the Quicktime useragent check, I replaced the wget command in myth_trailer_grabber on line 163

```
system("/usr/bin/wget $movieLink");

```with...

```
system("/usr/bin/wget -U QuickTime/7.6.2 $movieLink");
```This causes wget to impersonate QuickTime.  As time passes the user agent may need to be updated.

A word of warning about downloading.  Generally you get about 20 trailers.  At 185MB a piece for 1080p that can add up to a big chunk of space on your hard drive and more importantly a big hit to your bandwidth.

Cheers.

---

