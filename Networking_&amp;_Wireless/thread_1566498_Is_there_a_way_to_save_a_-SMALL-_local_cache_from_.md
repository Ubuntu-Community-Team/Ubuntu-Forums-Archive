---
title: "Is there a way to save a -SMALL- local cache from a -LARGE- SMB share?"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by Veovis Muad'dib on 2010-09-02
Here's my use case:

I have an Arch server with videos on it, shared with samba.  My mother's computer is running Ubuntu 10.04, and I use smbfs to mount ARCHSERVER\\share/Videos to ~/Videos for her in the fstab.  This works great, but sometimes she leaves the house, and sometimes the server is down, and I'd like for her to be able to see some of the videos even in those cases.  Her hard drive is not large enough to hold all of the videos though.

What I was thinking is this.  Whenever she watches a video from the server, save it to ~/.Videos and timestamp it.  When she tries to watch a video, if she has a local copy that is the same size, use that instead.  If she is away from the house, and the samba share is not mounted, ~/Videos should be a hard or symbolic  link to ~/.Videos.  There should be a size limit specified, and if she gets too close to the limit, say 50 GB, then it deletes the last accessed local file in ~/Videos, or enough to make room if one wouldn't be enough.  That way, if she watches a video twice, it is only streamed the first time.

She watches videos from that share in XBMC and through MPlayer.

I doubt anything like this exists, but I'm posting in case it does and someone can point me towards a solution.  If you have an alternate solution, I'd love to hear that as well.

---

