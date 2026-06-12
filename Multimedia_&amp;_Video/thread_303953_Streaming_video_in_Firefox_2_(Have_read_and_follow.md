---
title: "Streaming video in Firefox 2 (Have read and followed numerous how-to's)"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by Robert Leithe on 2006-11-21
I have found several threads like the one I'm starting here. Have read all I have found, and followd links to other forums and sites. But I still seem to be missing something...

I'm running Ubuntu 6.10, and am trying my best (note that I am fairly new to Linux) to be able to stream video in Firefox. Currently I'm simply getting the text "(no video)" when I visit a streaming site (that be it [www.vg.no](www.vg.no), [www.consiusmedianetwork.no](www.consiusmedianetwork.no), [www.cnn.com](www.cnn.com) or any other). YouTube plays well.
As it would appear it's QuickTime and Windows Media that fails.

I've read several places that I can't expect Windows Media to run - I'll live with that, if that's the case. But it would be *really* nice to have QuickTime.

Anyone wanting to take some time out of their schedule on this one?
If so, what kind of output would you need for starters?

Sincerely

---

### Post by tommcd on 2006-11-21
I assume you have all the mulitimedia codecs:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
If you can play video that you download, but just can't stream directly in firefox, get the firefox extension 'media player connectivity'. I had the same problem. This extension lets you easily choose the media player you want to run the video in. It then opens it in a new window. I can now watch CNN (Or any other video I have tried) without problems.
EDIT: this does not really fix the inherent problem. It will let you watch the videos though.

---

### Post by juantovarm on 2006-11-21
Get the extension media player connectivity, and, personally, i suggest you install xine and its extra codecs, so when the extension asks you which player to use for wmv, you choose xine

---

### Post by tommcd on 2006-11-22
Yes, I should have mentioned that. I also use Xine as my media player of choice with Media Player Connectivity. It has not failed me yet.

---

### Post by drphilngood on 2006-11-22
I had similar video problems but got them sorted by deleting all of the plugin links in usr/lib/firefox/plugins and installing Mplayer and haven´t found a vid format that I can´t stream, since.
BTW, since you have to be root to do this, I suggest using gksudo to run a program like Gnome Commander and just relocate all of the plugin links to a backup folder.  Also, make sure you have all of the necessary codecs.

Kind of an easy way out but it works.

---

