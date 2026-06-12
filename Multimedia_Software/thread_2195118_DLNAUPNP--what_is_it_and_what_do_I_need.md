---
title: "DLNA/UPNP--what is it and what do I need?"
date: 2013-12-22
forum: Multimedia Software
---

### Post by MrGibbage on 2013-12-22
I have tinkered around with some media sharing, but it has always been a hodge-podge clunky mess. I have seen some stuff about DLNA and UPNP, media sharing, renderers, etc. I don't know what I need. The fact that I don't know the terminology isn't helping either.

What I want to do is watch videos that are stored on my Ubuntu box on things like my Sony DVD player and my Android tablets. Ideally I would be able to watch them at home and away. I am very comfortable with port forwarding, so that should not be a problem. I just need the port numbers.

So, what software do I need for the Ubuntu box? The android tablets? Any other considerations?

---

### Post by TheFu on 2013-12-22
> **MrGibbage said:**
> I have tinkered around with some media sharing, but it has always been a hodge-podge clunky mess. I have seen some stuff about DLNA and UPNP, media sharing, renderers, etc. I don't know what I need. The fact that I don't know the terminology isn't helping either.

What I want to do is watch videos that are stored on my Ubuntu box on things like my Sony DVD player and my Android tablets. Ideally I would be able to watch them at home and away. I am very comfortable with port forwarding, so that should not be a problem. I just need the port numbers.

So, what software do I need for the Ubuntu box? The android tablets? Any other considerations?

Much of this is my personal opinion and experience. Others will have different opinions and experiences.[I][CENTER]
Just because something works, that doesn't make it secure.[/CENTER][/I]

UPnP is a huge security risk. If you care about security at all, don't use it.  There is a reason security people call it "Plug-n-Pray." That applies to game consoles too. Manually open any ports you want open and point them to static IPs inside your LAN. If this is too hard, then perhaps having any open ports is not a good idea?

DLNA is for local streaming only.  I've attempted to use it, but there are many different clients and servers, at the time of my use, they didn't really work well together. Even the MS-Windows7 Media Center DLNA Server was almost always months out of date for the videos available on it. It was very frustrating to see a TV show that had been deleted a month earlier still show up in the DLNA list as available.  On Linux, there are a few DLNA servers that mostly work .. MiniDLNA (needs a manual update cronjob), Tonky, PS3Media Center, and a few others.  I found them less-than-trivial to setup, they ate CPU, and keeping them updated was a directory scan job that had to run hourly to pick up any new recordings. Even with all that, their video list was mostly out of date.  With a few TB of videos, the scanning is cumbersome.

In the end, I found that using normal file sharing like Samba and NFS was the best answer for my needs. XBMC uses these easily and there are samba clients for android to access when on the same LAN.  Using wifi for streaming of HiDef content will never work very well, but for SD content, it should be ok.  Neither of these should be used over the internet. They are even worse for security than UPnP.  Bad enough that most ISPs have been blocking Samba sharing since the 1990s, thankfully.

Putting anything on the internet means using encryption and a key-based authentication. Passwords are NOT good enough these days as all the security breaches on professionally managed websites show.

Streaming over the internet is really easy if you don't care at all about security, but that opens the system up to all sorts of attackers and nefarious types. Being hacked and not knowing it for 6 months can easily happen. Please don't be "that guy."  I don't know anyone who does this streaming from their own network. They usually push stuff to 3rd parties like youtube or uStream if they want to stream videos.  A few people have purchased cheapo NAS devices for $20-$100 that use external providers to make the content available externally.  Of course, if you use that, then you completely trust the 3rd party service with all your data.  Dropbox, Tonido and pogoplug are some names for your research.

Snapstream is another option. Don't think there are any Linux servers or clients, but I'm probably wrong. I thought it was mostly a Windows thing.

If you do care about security, then using a strong VPN or at least an SSL-encrypted web stream are the only ways to do this short of buying a specialized device. Encryption adds overhead, especially on slower internet connections like DSL.  For the HTTPS method, something like **OwnCloud** is probably what you need - just don't forget to add the SSL cert before putting it on the internet. There are owncloud clients for most systems, including Android.  Lots of folks seem happy with it.  I have not been impressed, but I think that was my setup.  A few friends have it going and like it - these are security people and only access it using a VPN connection first. They got a VPS and push their media up to it, let OwnCloud on the VPS see it and stream using the VPS bandwidth, which is like .... 20x more than a home broadband connection usually has for upstream bandwidth.

As far as VPNs go, openvpn is really the best choice. Then you can share, access, anything on your LAN from anywhere in the world, securely. Using samba through an openVPN tunnel is completely secure. Clients exist for almost every platform ... but most work places will block this access as will a few hotels.  During an overseas trip a few weeks ago, my static subnet for servers was blocked by 3 different ISPs in the country I was in. The cellular ISP did NOT block access, oddly. In 2 other countries on that same trip, complete access worked just fine, so I'm confident it was the state/country blocking my access, not some technical issue on my network or servers.

For watching videos and recorded TV when I'm away from home, I just take the media files on my netbook. When on a plane over Alaska on the way to someplace in Asia, streaming doesn't work too well anyway. Handbrake has settings for Android hidef transcodes to get a 20G file to be 3G with very little loss in perceptible quality.  

The slingbox is very interesting, however. If I spent time traveling in the USA, it might make sense, but alas, I travel mostly overseas.

For streaming audio - there are lots of options.  I like a reverse proxy doing the SSL and **gnump3** for the music part. It is a little old-school, but works. The reverse-proxy can be skipped if openvpn is working.  Icecast (never used it myself) is another option and there are apache MP3 modules for the mp3 server side. I think almost any mp3-player can be a client.

The easiest answer for internet seems to be
* get openvpn working
* setup samba/nfs/web/gnump3 for access to your media files
* Be happy AND secure.

Anyway, those are my thoughts and experiences. **Perhaps someone else has easier AND secure methods?**

Update - 
* [http://www.mythpvr.com/mythtv/mythstreamtv/open-source-slingbox.html](http://www.mythpvr.com/mythtv/mythstreamtv/open-source-slingbox.html) claims to be a slingbox clone for MythTV
* Slingbox appears to have a way to run on Linux - don't know anything more about it
* Vulkano Flow is a Slingbox competitor.
Found an old "what resolution does Slingbox stream" website - looks like everything was put to 480p or less, at least back then. They must to deal with crappy upload bandwidth.  480p doesn't look that bad, unless you've become use to higher resolutions AND have 40+inch screens. On a tablet, it would be fine.
A few yrs ago, I used a Nokia N800 for my trips. It has an 800x480 screen and a slow-by-today's-standards ARM CPU.  Usually, I'd re-encode the videos before a trip to be 240p resolution, at a slightly lower frame rate, and enjoyed them on planes. This was before tablets really existed. Then I got a 10inch tablet and discovered GPU acceleration issues. For those, it was best to re-encode for 480p and be done. I tried about 50 different 720p re-encode settings and wasn't able to get playback without noticeable artifacts or stuttering.
Why am I sharing all of this?  Well, slower CPUs directly matches the sort of upload bandwidth issues we all have with uploads.  These directly correlate.

---

### Post by MrGibbage on 2013-12-22
Wow, I can tell that you are passionate about this. But honestly, I don't have anything else on the Ubuntu box. And my Sony DVD/Blu Ray players aren't able to find the media using simple file sharing (which I do have set up already). Same goes for my Android clients such as MediaHouse and Avia. They are looking for UPNP servers.

So I really appreciate the effort that you put into this, I am still holding out hope for a nice stable solution.

---

### Post by TheFu on 2013-12-22
> **MrGibbage said:**
> Wow, I can tell that you are passionate about this. But honestly, I don't have anything else on the Ubuntu box. And my Sony DVD/Blu Ray players aren't able to find the media using simple file sharing (which I do have set up already). Same goes for my Android clients such as MediaHouse and Avia. They are looking for UPNP servers.

So I really appreciate the effort that you put into this, I am still holding out hope for a nice stable solution.

Yes, I am.  If you limit your needs to just DLNA on the LAN - then miniDLNA is the easiest to get working.
File Expert, in the play market, supports SMB and many other file sharing connection modes for Android.  There is also an XBMC for Android that works with file sharing fairly well.  Of course, these are all on the LAN or through an openVPN tunnel. Over the internet makes security an important consideration.

I am always looking for a better solution myself - every 6 months to a year, I look again.

---

### Post by rocky2003 on 2013-12-23
What you want MirGibbage are

TVMobili - extremely easy to install on Ubuntu, then go to TVMobili website watch section and click configure your client then bookmark the web page, TVMobili allows you to stream the media to loca networks and over the Internet as well. Free version with data cap or pay to remove cap.

Serviio - harder to install on Ubuntu, pro version needed for streaming media over the Internet.

BubbleUPnP add-on server - BubbleUPnP server is not a UPnP/DLNA media server but an add-on to any other server, it basically gives that server the ability to stream over the Internet, if you use BubbleUPnP client on the other end.

Plex media server - Plex includes a DLNA server and the ability to stream over Internet but I think that feature requires their plexpass subscription. Plex is the more slick approach if you use their plex clients.

TvMobili is the easiest of the bunch to get going on Ubuntu, for remote access you can either manually access the URL of the TVMobili interface through the browser or go through the TVMobili website.

---

### Post by MrGibbage on 2013-12-24
@rocky2003, with these servers, would I be able to watch movies using my Sony DVD player as the client? And Android?

---

### Post by irvingdave1 on 2013-12-28
For just inside my LAN, I have Serviio installed. So far, so very very good.
My Samsung TV picks it up just fine, and I can also get my tunes on my android mobile using (the free) Skifta app.

---

