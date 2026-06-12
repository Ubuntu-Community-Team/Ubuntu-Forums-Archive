---
title: "Denmark's netradio seems to lock out Ubuntu"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by Lars Noodén on 2006-10-10
Denmark's [radio]("http://www.dr.dk/omdr/index.asp?sektion=eng") seems to be locking out Ubuntu and any system not beholden to the Windows Media Player Codec: [http://www.dr.dk/omdr/index.asp?sektion=eng](http://www.dr.dk/omdr/index.asp?sektion=eng)

1) what is a short term work around to get XMMS or other players to deal with the codec?

2) what strategy can be applied to get broadcasts from public service organizations to use codecs more platform independent ( and more oriented to a free market) ?

---

### Post by claus on 2006-10-10
Hi Lars,

I just tried it myself, and to me it seems that the 'mplayer plug-in' for Firefox *does* support this stream, albeit not directly. (I'm having problems with *some* media types right now, and I posted today on this [[http://www.ubuntuforums.org/showthread.php?t=274608](http://www.ubuntuforums.org/showthread.php?t=274608)], but imho *basically* it should work, even if it evidently doesn't in 'xmms'.) 

When you open the window which has the player embedded, a  file is being saved in your '/tmp' directory (like 'mplayOt4zeb'). From this file you can extract the URL of the respective channel, e.g. [http://wmsc.dr.dk/e06ch03m?wmcontentbitrate=40000](http://wmsc.dr.dk/e06ch03m?wmcontentbitrate=40000). I used this URL like an ordinary link in Firefox. The plug-in loaded and tried to open the file; then I got the message 'Stopped', but I think this message has to do with the problem I generally have with the plugin, and not so much with the radio stream.

I would recommend you to take a look at the thread (see  above) I opened on my problem; maybe you'll be able to find a solution for yours as well. If you haven't already done so, I would suggest that you install the 'mplayer plug-in' in Synaptic (I think it's listed under 'mozilla' somewhere). This plug-in is really cool and opens a number of commonly used multimedia formats (both audio & video) in Firefox/Mozilla (it even works under Epiphany).

---

### Post by Xappe on 2006-10-11
The Media Player Connectivity extension for firefox should get the stream url for you, and send it to a media player of your choice...

---

### Post by Lars Noodén on 2006-10-12
I'm not finding the Media Player Connectivity extension with Synaptic.  Where should I look for it ?

---

### Post by Xappe on 2006-10-13
look inside firefox (think it is under the tools menu) for a tool to let you search for and install extensions...

---

