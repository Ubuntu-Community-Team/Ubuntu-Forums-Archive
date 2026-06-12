---
title: "Problem viewing h.264 avi's with XBMC over Samba Share"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by xpeeblix on 2007-09-21
Hi, for any SAMBA/video gurus out there, I've got a rather tough problem I'm trying to solve.

I have a softmodded Xbox with XBMC installed connecting to an Ubuntu Feisty server through a Samba share.

XBMC can see the share and the files just fine.  The problem is that XBMC cannot play the files off the share.  If I log in to the share through OS X on my MacBook, Mplayer can't play them either.

The odd thing is that if I ftp the file back over to my MacBook, Mplayer can open them fine.  Then, if I ftp the file back to the Linux box, XBMC can play the video just fine, as can Mplayer on the Mac over the share.

Why would it work all of a sudden just because I copied it to another machine and wrote back over the old copy?

The video is H.264 in an AVI that is being FTP'd to the Feisty server from a Windows XP server, if that makes a difference.

Does anyone have any idea what could be causing this?  I'd appreciate any help on this, I'm truly stumped.

---

### Post by xpeeblix on 2007-09-22
Well, figured it out.  Turns out to be a simple permissions problem.  The folder wasn't set to allow files to be executed so mplayer couldn't play them.

Once the files were copied onto another system, it received new permissions which carried over upon being copied back.

Problem solved.  Thanks, all.

---

