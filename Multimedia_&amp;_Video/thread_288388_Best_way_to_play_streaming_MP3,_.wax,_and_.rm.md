---
title: "Best way to play streaming MP3, .wax, and .rm?"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by purifyyourmind on 2006-10-29
I have a couple problems trying to play streaming audio that worked in Windows:

1. The Hourly Newscast link at npr.org won't play anything (whether .wax or .smil) if I specify Totem or RhythmBox at the player. They're hiding behind a JavaScript link, so I'm not sure how to better open the stream.

2. One MP3 stream from a local public radio station has artifacts (blips, stutters) and will stop playing after less than a minute, at which point it buffers endlessly. This is in the RhythmBox player. If I start and stop the stream again, it will play for another minute or less, etc.

Thanks!

---

### Post by nealmcb on 2006-11-11
I have the same problem.  E.g. I go to load the story on this page, via the "listen" button: 

[http://www.npr.org/templates/story/story.php?storyId=6471912](http://www.npr.org/templates/story/story.php?storyId=6471912)

It gets a file of mime type "audio/x-ms-wax" named npr6983.wax

I select "open with Movie Player", and totem gives me this error:

An error occurred Only a subtitle stream was detected.  Either you are loading a subtitle file or some other type of text file, or the media file was not recognized.


The file looks like this:

 <asx version = "3.0">
<ENTRYREF href="http://www.npr.org/templates/dmg/dmg.php?prgCode=WESAT&showDate=11-Nov-2006&segNum=15&mediaPref=WM&sauid=U039769671151902999916&getUnderwriting=1&mswmext=.asx" />
</asx>

It works fine to just run totem with the URL in the href there.  But something needs to parse that text file and hand it off to totem.

I'm running dapper, with packages like totem-gstreamer-firefox-plugin, installed by easyubuntu, if I recall correctly.

Any idea what if anything can do that?

-Neal

---

### Post by notoriousdbp on 2007-01-22
totem-xine works way better than totem-gstreamer

---

