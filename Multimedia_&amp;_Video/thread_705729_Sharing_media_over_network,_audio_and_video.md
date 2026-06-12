---
title: "Sharing media over network, audio and video"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by rezfiles on 2008-02-23
Hello, I haven't been on the Ubuntu forums since 2005 so please bare with my noobness

I just installed ubuntu 7.10 server on an IBM xseries.

I am going away to college soon and wanted to build something that can share media with all of my friends in my dorm and be useful for something. 

I want people to be able to stream audio and video from this server to their computer... I have GNUMP3 installed for all of the music, now i need something for all my movies, does anyone have any suggestions?

Also, I have 14 20gb scsi hard drives, Is there any way i can put two directories in GNUMP3 for it to access? 

Thanks!!!

---

### Post by GreaterCore on 2008-02-24
Hi there,

What exactly do you mean sharing media?

If you mean allowing them to grab files from you, consider running Apache (a http server, thus accessible from a browser) or Samba (smb server, reversed engineered from Windows network drives, thus you can mount them from Windows machines). The good thing about this is that they could also share files with you. However, the legality of this exists, and make sure you won't get into any trouble with authorities if you decide to do this. Many, if not all universities do not condone file sharing. So if you were to do it, don't get caught.

A safer way would be to put them in an account, and ask your friends to SSH in and have access to your files. All transfers are encrypted thus it is harder (but still not impossible) for snoops to sniff at what is being transferred.

As for live streaming, I personally have not used it. One possible way is to look at VLC (Video LAN Client) [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/). I used it only for watching DVDs and VCDs but never did have the time to setup my own server.

Good luck!

---

### Post by rezfiles on 2008-02-24
Thanks for the help,
I wanted to like put them on a website essentially off my server, 
it has apache, just i wanted to figure out a way for them to click on a movie and have it stream over the site to them, 

but your suggestion of SSH is very good!! I think i might just go that way,

Thanks alot!

---

