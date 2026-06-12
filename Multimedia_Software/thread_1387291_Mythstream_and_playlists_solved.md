---
title: "Mythstream and playlists solved"
date: 2010-01-21
forum: Multimedia Software
---

### Post by sr_guy on 2010-01-21
Hi All, 

Thought I'd share this with everyone since it's been such a pain for me. Many of the youtube feed generator sites have died. So I was abe to finally find this solution to pull youtube rss feeds in mythstream. Hopefully a longterm solution.

1. Download the youtube parser patch. copy/paste. Save as youtube.patch in /home/foo/.mythtv/mythstream/parsers/youtube directory. Run patch < youtube.patch

```
[http://minimyth.googlecode.com/svn-history/r5830/trunk/gar-minimyth/script/myth-trunk/mythstream/files/mythstream-mythtv-r21640-youtube_parser_fix_2.patch](http://minimyth.googlecode.com/svn-history/r5830/trunk/gar-minimyth/script/myth-trunk/mythstream/files/mythstream-mythtv-r21640-youtube_parser_fix_2.patch)
```


I found this rss feed "mashup" for youtube playlists on yahoo pipes.

```
http://pipes.yahoo.com/pipes/
```

Here is the pipe:
```
http://pipes.yahoo.com/pipes/pipe.info?_id=BDPg9Wft3BGspImQl7okhQ
```

Basically, plugin a gdata youtube rss link to spit back a rss feed that will work in mythstream.
```

Example:
gdata like: [http://gdata.youtube.com/feeds/playlists/E45E22E8976E8F57?max-results=50](http://gdata.youtube.com/feeds/playlists/E45E22E8976E8F57?max-results=50)

```

```

Finished link:

[http://pipes.yahoo.com/pipes/pipe.run?_id=9bf36a7dfbf2c9cb9101d4e7e1a4b3aa&_render=rss&urlinput1=http%3A%2F%2Fgdata.youtube.com%2Ffeeds%2Fplaylists%2F](http://pipes.yahoo.com/pipes/pipe.run?_id=9bf36a7dfbf2c9cb9101d4e7e1a4b3aa&_render=rss&urlinput1=http%3A%2F%2Fgdata.youtube.com%2Ffeeds%2Fplaylists%2F)**[playlisthere]**%3Fmax-results%3D50

```

Taking this link and plugin a playlist ID here [playlisthere] will return a rss feed list in Mythstream. Just change the playlist id in the right section of the RSS link will make a somewhat easy way to create youtube rss feeds for mythstream.

```

Enter that link into mythstream setup, or in your streams.res file formatted like:

[item]
Youtube Rss Feed
Youtube Feed Title
[http://pipes.yahoo.com/pipes/pipe.run?_id=9bf36a7dfbf2c9cb9101d4e7e1a4b3aa&_render=rss&urlinput1=http%3A%2F%2Fgdata.youtube.com%2Ffeeds%2Fplaylists%2F](http://pipes.yahoo.com/pipes/pipe.run?_id=9bf36a7dfbf2c9cb9101d4e7e1a4b3aa&_render=rss&urlinput1=http%3A%2F%2Fgdata.youtube.com%2Ffeeds%2Fplaylists%2F)[playlisthere]%3Fmax-results%3D50
[emptystring]
youtube/feed

```

---

### Post by sr_guy on 2010-01-23
This pipe will work too. Easier to use as the plalist id is right at the end of the address.

```

http://pipes.yahoo.com/pipes/pipe.run?_id=337f74aec94658353dc4de2d51a814ae&_render=rss&textinput1=68A083F6EAFEFE01

```

---

