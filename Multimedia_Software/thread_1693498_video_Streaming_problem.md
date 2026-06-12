---
title: "video Streaming problem"
date: 2011-02-22
forum: Multimedia Software
---

### Post by greenwom on 2011-02-22
Here's the problem.  HD video locally plays with no problem.

Streaming the same ripped files over the network I'm getting choppy playback.  

Network problem right.  How do I troubleshoot that.  

It's a gigabit network.  

When I run the test on the windows side I have the same problem.
The files play locally without a hitch.

---

### Post by SeijiSensei on 2011-02-23
If you're sharing the files with Samba, my experience has been the SMB/CIFS isn't a very good solution for streaming.  If you have Linux clients as well as a Linux server, use NFS.  I can stream HD content over my G wireless connection with NFS.

You might want to look into using the streaming server in [VLC]("http://www.videolan.org/vlc/streaming.html").  Perhaps it has better performance than regular file-sharing schemes.

---

### Post by greenwom on 2011-02-23
Well I hate to say it in this forum but ultimately the system is going to be set up with Windows.  but being an Ubuntu guy I always test in Linux.  Having the problems with both OS.  

I'll try the VLC on the clients.

The "Server" is one of these HP media enclosures with 4 drives.
(we've got 4 1.5TB's in each bay).

The clients are dual core EEEpc.  They play the bluray just fine locally (in windows).  HD content in Linux 

I was wondering on the clients if there was any network tweaks or tweaks in media player / codecs..

---

### Post by SeijiSensei on 2011-02-23
> **greenwom said:**
> I'll try the VLC on the clients.

Actually I was talking about using VLC as the server.  Are you trying to stream directly from the HP device, or is it connected to a computer that is serving up the files?  If the latter, you could try VLC there.

---

### Post by greenwom on 2011-02-23
> **SeijiSensei said:**
> Actually I was talking about using VLC as the server.  Are you trying to stream directly from the HP device, or is it connected to a computer that is serving up the files?  If the latter, you could try VLC there.

No, it's a stand alone device that runs Windows Home Server.
I've never installed VLC as a server.  Didn't even know that was possible. 

Guess I'll have to read up on it.

---

### Post by Linearcraig on 2011-03-08
I've been having the same issue, however when I stream using the default Unbutu media players it crashes completely producing about 4 errors.
 
Played using VLC and just got seriously chopping play back. It seems to only be on HD files aswell. HD Tv series (which is obviously smaller) seem to play ok.
 
I'm streaming from a windows network onto, Ubuntu (Mavrick) on a REVO 3700. Wired and Wireless.
 
Would be great to get a solution to this issue.

---

