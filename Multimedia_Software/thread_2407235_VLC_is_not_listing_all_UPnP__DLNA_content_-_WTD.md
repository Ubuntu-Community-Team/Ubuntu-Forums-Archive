---
title: "VLC is not listing all UPnP / DLNA content - WTD?"
date: 2018-12-01
forum: Multimedia Software
---

### Post by dinkidonk on 2018-12-01
I have a HD-recorder which also functions as a DLNA media server. On my old system (Mint KDE 17.3) I can access all the content/recordings on it with VLC using "Playlist->LAN->Universal Plug'n'Play", but on Kubuntu 18.04.01 I only get a very sparse list of the content. When I expand the "Device->HDD->Video->All" branch I get a list of some of the content and if I open "Device->HDD->Video->Not viewed" I get a list of some other content which seems weird, because "All" should mean "All" and not "Some". Are there any known bugs in VLC causing this issue? Are there other players which would allow me to access all the content?

Thanks! :)

---

### Post by TheFu on 2018-12-01
I've seen the same issue with VLC for years.  Sometimes DLNA servers show up, sometimes they do not.  Because of the way that DLNA announces on the subnet, waiting up to 3 minutes to see all the sources might be necessary. Even then, it doesn't always seem to work.  I've seen that on all VLC clients with both wifi and wired LAN connections.

The only DLNA player on Ubuntu that seem to always work for me is **kodi**, but I leave the kodi systems on 24/7/365.  Plus, kodi is pre-configured to point at the DLNA server.  I use kodi on a few raspberry pi systems.

---

### Post by dinkidonk on 2018-12-01
It is not a problem with DLNA servers not showing up, it is a problem with content on the servers not being listed and therefore it is not available to the player.

---

### Post by ajgreeny on 2018-12-01
Using vlc as a dlna client did not and still does not work in 16.04 but I am using vlc on my Xubuntu 18.04 and it finds the dlna server running on another 18.04 system on my LAN with no problem, and also finds all the music, video and photo files that I expect it to.

It would be interesting to see more details of your HDD recorder configuration; how do you set that up or does it try to stream anything and everything on the HDD?

What filetypes does the HDD contain?  I record several things to a hard disk from my TV which are **file.ts** but not streamable by minidlna or PlexMediaServer which I also use as a media streamer. I convert them all with command ```
ffmpeg -i file.ts -acodec copy -vcodec copy file.mpg
``` and those mpg files stream without a problem.

EDIT:
In view of what vidtek says below, I should add that all devices that attach to the router in my LAN use reserved, ie static, IP addresses so there is no possible problem of DHCP changing those and causing problems of device discovery.

---

### Post by vidtek on 2018-12-01
> **TheFu said:**
> I've seen the same issue with VLC for years.  Sometimes DLNA servers show up, sometimes they do not.  Because of the way that DLNA announces on the subnet, waiting up to 3 minutes to see all the sources might be necessary. Even then, it doesn't always seem to work.  I've seen that on all VLC clients with both wifi and wired LAN connections.

The only DLNA player on Ubuntu that seem to always work for me is **kodi**, but I leave the kodi systems on 24/7/365.  Plus, kodi is pre-configured to point at the DLNA server.  I use kodi on a few raspberry pi systems.

DLNA discovery has always been patchy for me.   Most network systems have a set TTL (time to live) of 20 minutes (designated in hops).  In order to make discovery work correctly you either have to wait up to 20 mins after until the network device has been removed from the network, or switch everything connected off, and I mean EVERYTHING, including the network hub/internet gateway/router/switch/computer/smartphone/tablet:o.

One other thing to bear in mind, if you are using DHCP, the router handing out ip addresses will have a time limit that is usually user-settable.  I have mine set for 24 hrs, but it can be set for up to a week.  So if you disconnect your DNLA server and restart, the old settings may still be floating around in the ether somewhere.  This and the TTL can cause all sorts of weird and wonderful things to happen.  This is a common cause of many strange network behaviours that non-technical users find puzzling:confused:  

Cheers, Tony.

---

### Post by TheFu on 2018-12-01
Small correction.  TTL isn't in minutes.  It is in router hops.  As a packet crosses each router, the TTL is decremented by one.  This is a feature for IP packets and prevents packets that cannot find a destination from bouncing around forever.  When the TTL is 0 (zero), the router that sees that drops it.  20 is a fairly low value for ttl these days.  I think the default is 64 for IPv4 and probably double that for IPv6, but don't quote me.
 
My Win7 media center doesn't show all the newer files I know exist on it or often shows outdated files from 6+ months ago.  Since I only access it for playback when watching live TV that is also being recorded, it has never been a priority to figure out that issue.  I consider it a Windows problem, not an Ubuntu problem.

Perhaps there is a patch for your DVR?  Which DLNA server is it running?

---

### Post by dinkidonk on 2018-12-01
**@ajgreeny**: Just for the fun of nit-picking, your ffmpeg command is not doing any conversion it is just remuxing streams into a different container :P

My HD-recorder is an oldish Panasonic DMR-BCT720 (it stores recordings as raw transport streams, TTS aka MTS, TS etc.), and I have never had any issues with accessing contents from it with VLC on Mint KDE 17.3 and/or Debian Jessie. VLC on Kubuntu 18.04.01 only allows me to access parts of the content, I have 5 episodes of a TV-series recorded from the same channel but only one episode is accessible. It almost seems like the number of files VLC fetches from the HDR is somehow limited to 12. Tomorrow I will try to delete one of the listed recordings from the HDR and see if another takes its place in VLC.

**EDIT**: I've just tried to delete some recordings from the HDR, other recordings are now listed in VLC but again the list is limited to 12 items - seems like a bug to me. Also, one of the recordings is being detected as a Gzip archive, remuxing it with ffmpeg makes it playable. Weird, none of this happens on Mint 17.3 or Debian Jessie. If I somehow can help fix this issue, please poke me! :)

---

### Post by ajgreeny on 2018-12-01
> **dinkidonk said:**
> **@ajgreeny**: Just for the fun of nit-picking, your ffmpeg command is not doing any conversion it is just remuxing streams into a different container :P
Yes, I'm aware of that but it is the simplest way of making those .ts files streamable by both minidlna and Plex.
I admit I've not tried simply changing the filetype suffix from .ts to .mpg; perhaps I should try that!

---

### Post by dinkidonk on 2018-12-01
> **ajgreeny said:**
> I admit I've not tried simply changing the filetype suffix from .ts to .mpg; perhaps I should try that!

That's probably not gonna work since the container and the information about the streams does not change. I've just had a *.TS from my HDR showing up as a Gzip file and changing the extension made no difference, remuxing it with ffmpeg repaired it, though! :)

---

### Post by TheFu on 2018-12-01
For 16.04 lurkers ... 
If you use the vlc v3 PPA, **sudo add-apt-repository ppa:jonathonf/vlc-3** then the DLNA support should be much better.  update/upgrade after that add-apt-repo command to get the newer vlc.

[http://ubuntuhandbook.org/index.php/2018/05/install-vlc-3-0-2-ubuntu-16-04-ppa/](http://ubuntuhandbook.org/index.php/2018/05/install-vlc-3-0-2-ubuntu-16-04-ppa/) has more detailed instructions, if you need them.  Also shows how to get a newer, stable, ffmpeg.

In theory, 18.04 should be getting newer versions already.

---

### Post by vidtek on 2018-12-02
I have edited my post to reflect the hops.  My point was to stress that it can take up to 20 mins for the packets to die.

---

### Post by TheFu on 2018-12-02
> **vidtek said:**
> I have edited my post to reflect the hops.  My point was to stress that it can take up to 20 mins for the packets to die.

Perhaps we were talking about different TTLs? To clarify there are 3 main TTLs.
* DNS
* IP packets
* HTTP headers

The TTL in DNS is based on time before a cached record needs to be refreshed.  The DNS server controls this value. [https://en.wikipedia.org/wiki/Time_to_live#DNS_records](https://en.wikipedia.org/wiki/Time_to_live#DNS_records)  If I need to make DNS changes, I'll reduce that value to 5 minutes, but leaving it set that low will incur higher charges from a paid DNS provider due to the additional requests. Normally, I'll leave public DNS caching set to at least 24 hours.

The TTL in IP is purely the number of router hops allowed.  [https://en.wikipedia.org/wiki/Time_to_live#IP_packets](https://en.wikipedia.org/wiki/Time_to_live#IP_packets)  In DNLA, the TTL is set to 1 - 3 hopes to prevent the packets from leaving the home subnet. This is why DNLA doesn't work over the internet.

The TTL in HTTP isn't involved here, at least I don't think it is.  I've seen it used to prevent web spiders from refreshing article content constantly or for AJAX/Javascript updates to happen every few seconds. I've usually seen the JS timer setup on the client-side to refresh, so they don't use the TTL.

---

