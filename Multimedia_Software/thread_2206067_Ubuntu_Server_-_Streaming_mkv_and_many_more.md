---
title: "Ubuntu Server - Streaming mkv and many more"
date: 2014-02-17
forum: Multimedia Software
---

### Post by smokers2 on 2014-02-17
Hey guys,

this is my szenario im curently working on.

I have a vpn network with my ubuntu server and im running a samba services on it. All in all playing video files out of the samba-shares, is pretty poor, because of multiple laggs and non existint buffering. 
So i thought about a easy solution which should give all users of the network the possibility to stream any file out of the MEDIA-samba-share (on demand). But till now, i haven't working with streaming services so my first question is, which software is most applicable to this szenario?

And how do i deal with maybe different mp4,mkv,... -files? Any user cann upload his videos to the share and im not able to control their encoding behaviour or their camera output. so the streaming-software may should 
be capable of this situation.


if all this is possible, is it also possible to provide streams (on demand) with a live encode to a lower bitrate/resolution? in example the original file is present on the hdd in 1080p the user can device streaming in 720 or lower?


mhh thanks for any input so far.

smokers

---

### Post by TheFu on 2014-02-17
Not F/LOSS, but "plex media server" does the streaming ... without using a VPN. Any DLNA client can be used or there are paid Plex clients for a nicer/XBMC-like interface. I think they have an SSL mode now too. I refuse to stream outside my own network, so ... don't know about that.

Samba/CIFS is less efficient than other methods of file transfer. Last week I learned that Windows7 includes NFS. Haven't tried this myself. Also, if any of the clients are wifi or using cell-data-networks, CIFS is probably the least of all the evils, provided a VPN is used.

---

### Post by SeijiSensei on 2014-02-17
I believe NFS [only comes with Windows Ultimate and Enterprise versions]("http://superuser.com/questions/525473/how-do-i-mount-an-nfs-share-in-windows-8"); even Win Professional no longer includes the NFS client.  However, I would recommend NFS over Samba for media shares if you have clients that support it.  I can stream 1080p Matroska files over wifi from my server without a hitch.  (I do have my caching buffers in SMPlayer set rather high to 2 MB.)

---

### Post by smokers2 on 2014-02-17
maybe i didn't described it more correct.
i use samba with windows clients, e.g. NFS.

but my server is a dedicated root - server (100mbit bidirectional) . everything is tunneled thru a openVPN service. behind de VPS wall there is the samba/nfs server. users have mounted their own movies and the complete media share over an net share.
but as i said, if they open a mkv file from the explorer, it is sometimes a little struggeling because of bitrate up and downs.

so i thought on a streaming service, so they can let a video buffer maybe 3 minutes, (or more) and so they are aware of waiting times.

maybe i will try the plex server ;-)

---

### Post by TheFu on 2014-02-17
Thanks SeijisSensei!
I'd looked on a Home-Premium and didn't see it, but the Microsoft Forums implied that it was available as a download for all versions except "basic".  I haven't check my Win7 Ultimate install (got this free from MS by attending a launch party) for NFS ...  yep - it is in there. 2 steps to get it working. Enable "unix services", then NFS will show up in the same list - enable that too.

DLNA clients can have huge caches,  seeing 500MB in BubbleDLNA on android now.

---

