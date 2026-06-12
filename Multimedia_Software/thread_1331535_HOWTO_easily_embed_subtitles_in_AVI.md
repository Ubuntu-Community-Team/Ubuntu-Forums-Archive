---
title: "HOWTO easily embed subtitles in AVI"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Donalb on 2009-11-19
Hey,

I'm posting this just as much for myself for future reference as for anyone else.

I use a Multimedia HDD connected to my TV. The embedded OS on the HDD won't load separate subtitle files so occasionally (maybe once a year)I want to watch a film that doesn't have embedded subtitle files and I have to manually add them.

I've tried running AviAddXSub in Wine but that doesn't work for me.

Likewise tried adding in Avidemux with no success.
 Searching around I found the following on a post on Last.fm. I'm no CLI guru so I just copied, pasted & edited.


```
transcode -i videofile.avi -x mplayer="-sub subfile.xxx" -o outputfile.avi -y xvid
```

where videofile.avi and subfile.xxx are the input AVI & Subtitle files.
```
transcode -h |more
``` for simple options. The command above outputs to xvid. 

This is a slow enough method but at least it worked (for me).

Thanks to original author.
Original post here:
[http://www.last.fm/user/HawkeVIPER/journal/2008/01/13/eys_embedding_subtitles_into_avi_files_on_the_linux_command_line]("http://www.last.fm/user/HawkeVIPER/journal/2008/01/13/eys_embedding_subtitles_into_avi_files_on_the_linux_command_line")

---

