---
title: "mplayer fails in while loop"
date: 2011-02-15
forum: Multimedia Software
---

### Post by tankmil on 2011-02-15
Hi,  When I run the following commands: 

```
lynx --source "http://ccmixter.org/view/media/remix" | grep "mp3" | cut -d\' -f4 
```which gives me a links of URL's of mp3 files

and then  

```
mplayer "http://ccmixter.org/content/[name of file].mp3" 
```the music plays fine.

However, when I run the following code:
```

lynx --source "http://ccmixter.org/view/media/remix" | grep "mp3" | cut -d\' -f4 | while read mp3; do mplayer "$mp3"; sleep 15; done
```It doesn't work - instead I get the following:

```
Resolving ccmixter.org for AF_INET6...
Couldn't resolve name for AF_INET6: ccmixter.org
Resolving ccmixter.org for AF_INET...
Connecting to server ccmixter.org[72.51.41.176]: 80...
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   No bind found for key ':'.                         
Cache fill:  0.00% (0 bytes)   

Exiting... (End of file)
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
```Does anyone have an idea why?

---

### Post by sisco311 on 2011-02-15
http:// is part of mplayer's syntax. So try something like:

```
lynx --source "http://ccmixter.org/view/media/remix" | \
grep "mp3" | cut -d\' -f4 | **sed 's_^http://__'** | \
while read mp3; do 
  mplayer "**http://**$mp3"
  sleep 15
done
```

or

```
while read mp3; do 
  **eval** mplayer "$mp3"
  sleep 15
done < <(lynx --source "http://ccmixter.org/view/media/remix" | grep "mp3" | cut -d\' -f4)
```

---

### Post by frenchn00b on 2011-06-22
```
FILES=`wget -k http://www.troutman.org/ftp/pub/motorcycle/videos/`
echo "$FILES"  | while read i ; do eval  mplayer "$i" ; done
```

NOT WORKING? 

It seems that it does not identify the lines anymore ...

---

### Post by andrew.46 on 2011-06-22
**@ tankmil**:

Perhaps the following slightly different approach might work better:

```

lynx --source "http://ccmixter.org/view/media/remix" \
     | grep "mp3" | cut -d\' -f4 | \
     mplayer -cache 1024 -cache-min 80 -playlist -

```

**@frenchn00b**:

Yours is a little trickier as there are relative links instead of absolute but this works on my system:

```

lynx --source http://www.troutman.org/ftp/pub/motorcycle/videos/ | \
     grep -E '(mpg|avi|wmv|mpeg)' | cut -d '"' -f8 |
     sed s#^#http://www.troutman.org/ftp/pub/motorcycle/videos/# | \
     mplayer -cache 1024 -cache-min 80 -playlist -

```

There probably would be a cleaner way to do this but I was always a slightly clumsy regexp user :(.

---

