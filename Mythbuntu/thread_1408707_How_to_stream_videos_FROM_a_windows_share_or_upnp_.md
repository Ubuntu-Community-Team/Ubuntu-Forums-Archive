---
title: "How to stream videos *FROM* a windows share or upnp server *TO* mythtv box"
date: 2010-02-16
forum: Mythbuntu
---

### Post by JasonBr on 2010-02-16
I can't seem to find the answer to this.  Everywhere I search is filled with howto's on viewing mythtv content on a windows box but not the other way around. 

I have a windows machine running a UPNP server as well as windows shares of videos and music.  I want to add these to my mythtv library so that I can watch them on the mythtv box.  Is this possible?

---

### Post by epi 1:10,000 on 2010-02-16
Good Question!!    I would like to know the answer to this too.  I know XBMC can do this but XBMC doesn't have the advanced VDPAU options that MythTV has.

---

### Post by ian dobson on 2010-02-17
Hi,

Maybe you could miss use vlc to stream the media from your upnp system and get MythTV to use the output from vlc as an extra tuner card.

Have a look here:- [http://www.mythtv.org/wiki/Dreambox-NetworkRecorder#The_channel_change_script](http://www.mythtv.org/wiki/Dreambox-NetworkRecorder#The_channel_change_script) 

The page is for streaming from a dbox into mythtv, but as vlc does the streaming it doesn't matter where the media is cmming from.

It's not for the faint hearted, I setup my dbox last weekend to stream to mythtv and it took me about 8 hours to get it working. Mainly due to the fact that my dbox has a different sw version and when I setup vlc I used the hostname of the myth backend rather than hard wired IP addresses.

Regards
Ian Dobson

---

### Post by nickrout on 2010-02-17
The answer is very simple. Run dmount on the linux box. This will mount all upnp drives on your network.

Then add the mount point to the directories that mythvideo looks for videos in.

---

### Post by joho500 on 2010-02-17
You can also mount your Windiows shares and add the folders where you mounted them to the locations in mythbackend.

Cheers,
Joost

---

### Post by JasonBr on 2010-02-17
> **nickrout said:**
> The answer is very simple. Run dmount on the linux box. This will mount all upnp drives on your network.

Then add the mount point to the directories that mythvideo looks for videos in.

dmount is a command?  I don't see any further information on this command in a google search.

---

### Post by nickrout on 2010-02-17
Thats cos I mistyped it. It's djmount. [http://djmount.sourceforge.net/](http://djmount.sourceforge.net/)

Sorry bout dat.

---

