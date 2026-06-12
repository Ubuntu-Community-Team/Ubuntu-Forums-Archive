---
title: "Streaming through Mediatomb to UPNPlay - cannot get playlists working"
date: 2012-09-30
forum: Multimedia Software
---

### Post by mogdad on 2012-09-30
Hi,

I have Mediatomb on a machine with 12.04 LTS. It seems to be working happily enough, streaming to a Google Nexus 7 tablet that is running UPNPlay. But I am struggling with playlists. I have a pile of playlists made with Rhythmbox (most are .m3u but I have also tried .pls and .xspf) in a subdirectory of my main music directory. I can see the playlist directory and files with UPNPlay but it tries to play them as if playlist were a music file (rather than parsing them as playlists). I can also transfer the playlists to the Nexus and open them in UPNPlay - it parses the tag info but doesn't find the music files.

Through a not very scientific process of elimination (e.g. trying other UPNP clients) I think this down to the setup of Mediatomb and how it is handling or not handling playlists.

I crave the indulgence of the members of this forum for posting a query that probably isn't really strictly a Ubuntu issue but I'm really having a hard time working this out and from hunting around about the best Mediatomb expertise I have found is here (whereas the Mediatomb home site is really heavy going).

But hopefully _someone_ out there has had a similar problem and found how to fix it?

Thanks

---

### Post by mogdad on 2012-10-02
Update to previous post...

I think the problem I have been having with playlists relates to the fact that mediatomb is not compiled with JS support. There are apparently ways around this but I have just switched to miniDLNA instead, which seems to be able to handle my playlists right out of the box.

---

