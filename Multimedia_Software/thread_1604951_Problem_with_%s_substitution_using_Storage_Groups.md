---
title: "Problem with %s substitution using Storage Groups"
date: 2010-10-24
forum: Multimedia Software
---

### Post by johnlatz on 2010-10-24
I own a set of cartoons that I'd like to play at random for the kids.  Googling turned up this four year old post that would seem to accomplish exactly what I want:  <[http://www.codedread.com/blog/archives/2006/12/17/setting-up-mythvideo-for-playlists/](http://www.codedread.com/blog/archives/2006/12/17/setting-up-mythvideo-for-playlists/)> 

Short story:  when I use the %s token, I would expect to get the filename - "playlist.spl"  or "/myth/videos/Cartoons/playlist.spl"   Instead, I've determined the value for %s to be "myth://Videos@192.168.15.101:6543/Cartoons/playlist.spl".  (I substituted the command echo "%s" > output.txt temporarily in the settings).

So my question is - what are my options?  I'd prefer not to change the Storage Groups approach, since that appears to be the direction Myth is moving.  I can't find any list of string substitutions (i.e. "%s" "%d" etc) via googling or searching the mythtv.org/wiki

Am I left to write an external script that does what I want, or is there a more elegant solution that I just can't find (figuring out which string substitution %xxx would be best)?

---

