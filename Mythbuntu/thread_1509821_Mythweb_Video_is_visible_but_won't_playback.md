---
title: "Mythweb Video is visible but won't playback"
date: 2010-06-14
forum: Mythbuntu
---

### Post by tmcgary on 2010-06-14
I am having difficulty playing video on my  windows-based laptop using mythweb from my combination FE/BE running Mythbuntu 10.04  (using the 2.6.32-22 kernel).  I am able to view the path/directory tree over mythweb as seen in this screenshot:


[http://s941.photobucket.com/albums/ad253/tmcgarybass/](http://s941.photobucket.com/albums/ad253/tmcgarybass/) 
  However, when I click on any of the movie titles  nothing plays or happens (i.e. error messages). I am able to play back music via mythweb on this windows laptop. All playback is normal on the FE/BE  itself. 
   
  I am not using storage groups as the videos are all  iso’s. Each video iso file is contained in a folder with the same name as the file  itself.
   
  Any ideas?

---

### Post by tmcgary on 2010-06-15
I just had an idea I wanted to try as a work around, but needed to see if someone could confirm this:

Is the default mythbuntu directory for videos /var/lib/mythtv ??

I changed my settings and don't recall the default. Thanks!

---

### Post by tgm4883 on 2010-06-15
> **tmcgary said:**
> I just had an idea I wanted to try as a work around, but needed to see if someone could confirm this:

Is the default mythbuntu directory for videos /var/lib/mythtv ??

I changed my settings and don't recall the default. Thanks!

Yes

---

### Post by tmcgary on 2010-06-15
Thanks for your reply!

Just in case anyone stumbles on this in the future, here is what I did to enable streaming of my video content to my 2 windows laptops via mythweb and still have everything function on the FE. I used a partial storage groups/non-SG solution.

I set my BE video directory (in BE setup) to /var/lib/mythtv/videos. In this location I placed a symlink for each of the .iso files that appear in my main video directories (.../Video/DVDs and .../TV Shows). Then I set my FE video settings (util/setup>setup>media settings>video settings>general settings) to these two directories.

This setup allows mythweb to see the iso files via the symlinks, playback locally within myth FE and still having everything play nice in XBMC. I can download each movie from mythweb. Alternatively, I can stream the movie with VLC by right-clicking the link, copying link location, and pasting that location into the network stream prompt in VLC (Media>open network stream). 

This solution isn't pretty but seems to work. The only snag is sometimes in VLC I have to hunt for an audio track that works but have yet to have a stream that didn't have audio. If anyone has a more elegant/simpler/pretty solution please let me know. Also if anyone knows if this cut-n-paste method would work in an android based device or phone please chime in. I hope this may help someone out there at some point.

Tom

---

