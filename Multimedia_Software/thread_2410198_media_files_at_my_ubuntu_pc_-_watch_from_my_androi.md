---
title: "media files at my ubuntu pc - watch from my android phone"
date: 2019-01-12
forum: Multimedia Software
---

### Post by marchello_lippi2 on 2019-01-12
Hi all, 
I got video and music files at my ubuntu pc. 
Is there any ubuntu software that might allow me watching mentioned files from my android phone?
Please adivse.

---

### Post by TheFu on 2019-01-12
Lots.

minidlna, plex, cifs server on the Ubuntu side.  If you share the storage on the LAN with either CIFS or NFS, then any android that can read from those methods will work.

Then any DLNA renderer/client on android or a web browser if you use plex's web interface.  VLC can be a DLNA renderer, client, or access files on a streaming site.  I use bubbleUPnP.  There's also Kodi.  This is probably the most full-featured, easiest to use media center software, but Kodi would be  a little heavy for a phone.

There's also the nextcloud/owncloud serve options with video players for webclients as an option.

There are probably 50 others.  Just depends on the level of effort you are willing to do on the front end for a smooth experience later.  If you spend more time now, it is much easier later.

Also, if you want to stream audio/video from anywhere in the world, there are solutions for that. Some are "pay to make it work", but you can run you own VPN and access the media like it was local, assuming you have a broadband internet connection from home already.

---

### Post by marchello_lippi2 on 2019-01-12
Thx **TheFu**

---

### Post by SeijiSensei on 2019-01-12
I use minidlna on the server, BubbleUPnP to connect to the files from my Android phone, and MXPlayer to play them.  Only problem with MXPlayer is that it doesn't support Chromecast.

---

### Post by marchello_lippi2 on 2019-01-12
I'm trying plex right now. 
Works great on my ubuntu pc, ubuntu notebook, raspberry pi under kodi/osmc and android. 
The only thing is that official android app allows to watch only the first minute in free version. 
So I just use chrome or firefox browser on my android phone, which is not so convenient, but it's for free.
Thanks!

---

### Post by SeijiSensei on 2019-01-12
Try using BubbleUPnP as the DLNA client on your phone.  It has no such restrictions.

---

### Post by TheFu on 2019-01-12
> **marchello_lippi2 said:**
> I'm trying plex right now. 
Works great on my ubuntu pc, ubuntu notebook, raspberry pi under kodi/osmc and android. 
The only thing is that official android app allows to watch only the first minute in free version. 
So I just use chrome or firefox browser on my android phone, which is not so convenient, but it's for free.
Thanks!

As SeijiSensei says, try BubbleUPnP on the phone.  I don't use my phone that way - generally want to playback only local media, so I use nextcloud to get the media local, then Odyssey music player to play the local media. Odyssey is in the f-droid store, so you don't have to use the google-play store.  F-droid tends to have GPL software, not proprietary and most apps don't have ads.  Many people don't care about this aspect.

Also, you can use the plex web interface http://{IP}:32400/web from any browser, including your phone's, to watch or listen to any media inside the Plex DB.  If you setup either an ssh-tunnel or VPN from your phone to your home, then you can access all that media from anywhere in the world.  I've posted my ssh-tunnel SOCKS proxy script here a few times.  Whatever you do, don't make 32400/tcp available to the internet. Plex really isn't designed to be secure. DLNA just didn't consider security at all in the protocol.

I've never used any Plex client. It just isn't needed.  On my r-pi systems, I use Kodi with the PlexBMC addon to access Plex Server media and the transcoding it provides for players that can't deal with older file types ... or just file types that Kodi doesn't handle well, like xvid or divx from 2004-ish.

Lastly, I consider NOT having chromecast support to be a huge, huge, feature. ;)  But I don't really watch youtube videos.

---

### Post by marchello_lippi2 on 2019-01-12
Thx to all!

---

### Post by marchello_lippi2 on 2019-01-12
Just a followup. I got some high quality video about nature which I was not able to watch on my weaker notebook. But with plex it is possible to choose quality, like in youtube. So it is cool.

What is not so cool is that when plex scans my folders with video, it also looks for appropriate name and poster for the movie. Don't know how it works, but in many cases its finding is not appropriate at all. For example, I got cartoons series for kids and each file starts from number of episode. So plex looks for some movies with that number in its name. The result is funny. Any idea how do I turn off this option? I would rather prefer it to show filename as is...

---

### Post by marchello_lippi2 on 2019-01-13
> [COLOR=#000000]What is not so cool is that when plex scans my folders with video, it also looks for appropriate name and poster for the movie. Don't know how it works, but in many cases its finding is not appropriate at all. For example, I got cartoons series for kids and each file starts from number of episode. So plex looks for some movies with that number in its name. The result is funny. Any idea how do I turn off this option? I would rather prefer it to show filename as is...[/COLOR]
So... it's ok in browser, it has "show directory" option and it displays real file names. Still can't find this option in plex addon for kodi/osmc @ rpi though.

---

### Post by marchello_lippi2 on 2019-01-13
> **TheFu said:**
> As SeijiSensei says, try BubbleUPnP on the phone.

My phone is on 192.168.1.0 network and plex server is on uplink router 192.168.0.0 network. Probably this is why BubbleUPnP android app can't find my plex server. Can't see where to set plex server ip address manually. 
So... continue trying it from my chrome or firefox browser at android.

---

### Post by TheFu on 2019-01-13
> **marchello_lippi2 said:**
> Just a followup. I got some high quality video about nature which I was not able to watch on my weaker notebook. But with plex it is possible to choose quality, like in youtube. So it is cool.
Yep, it is.  That is usually automatic for the most popular player devices, but how well it works depends on the Plex Server hardware.  Lots of people are putting a Plex Server on a raspberry pi. This computer can't transcode 4K video to 720p for a weak tablet.  Trade-offs.

> **marchello_lippi2 said:**
> 
What is not so cool is that when plex scans my folders with video, it also looks for appropriate name and poster for the movie. Don't know how it works, but in many cases its finding is not appropriate at all. For example, I got cartoons series for kids and each file starts from number of episode. So plex looks for some movies with that number in its name. The result is funny. Any idea how do I turn off this option? I would rather prefer it to show filename as is...

Plex folders can be configured for the types of files stored.  You **must** put like content together and you MUST pull out content that doesn't fit that type into other directories not in the directory path for any other content types.

/Movies
/TV
/Music
/Photos
/Videos

Then you configure the appropriate scanner for each of those directories.  Don't put TV shows into the Movie directory.  Don't put home-movies in TV or Movies either.  Put those into /Videos and do not configure any scanner.  The web interface controls that.

Do not fight against the organization.  All media center programs work the same way.  Kodi uses the same structures.

Also, if one of those directories fills up a HDD, don't worry. You can add another HDD and add those directories into the list for the different types.  I have 5 different directories for recorded TV, for example. Those are on different storage.  No need to use any fancy directory merging tools.

---

### Post by TheFu on 2019-01-13
> **marchello_lippi2 said:**
> My phone is on 192.168.1.0 network and plex server is on uplink router 192.168.0.0 network. Probably this is why BubbleUPnP android app can't find my plex server. Can't see where to set plex server ip address manually. 
So... continue trying it from my chrome or firefox browser at android.

DLNA uses a broadcast method to announce it is on the network. That is specific to the subnet/netmask used.  By default, Plex allows "local access" with out their remote client to a /24 subnet. This can be changed in the web-admin interface. 

You can list other subnets to be allowed non-authenticated plex access too.  This is generally a bad idea, but I suspect you have a very good reason.  My wifi subnet is separate from my wired LAN and requires using a VPN to gain access.

Plex is good for many things, but not great in all ways or at everything it does.

---

### Post by MartyBuntu on 2019-01-14
You might be better off with a simpler UPnP server/client setup like **UPnPlay**.
I agree with TheFu, Plex might be overkill...even though it's quite good overall.

---

### Post by ajgreeny on 2019-01-17
I use both minidlna and Plexmediaserver in my home and for an Android client I find VLC simplest and great to use as it finds the minidlna server immediately.

Just open VLC, go to Local Network and the minidlna server will show in the list.  You can then drill down into the folders you have set up in the minidlna.conf file on the server, thus playing whatever video, music or image you want; brilliant!

---

### Post by marchello_lippi2 on 2019-05-04
Hi again, how do I disable plex from running on startup?

---

### Post by sisco311 on 2019-05-04
```
sudo systemctl disable plexmediaserver.service
```

---

