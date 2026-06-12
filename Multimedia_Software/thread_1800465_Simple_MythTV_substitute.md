---
title: "Simple MythTV substitute"
date: 2011-07-09
forum: Multimedia Software
---

### Post by Cantido on 2011-07-09
I've been trying to find a way to watch videos from my main desktop computer on another computer I've plugged into an HDTV. I'm such a Linux newbie that I decided to give Mythbuntu a try. It was way to complicated for what I needed, and I'm sure that some more experienced people reading my first two sentences laughed to themselves at my naivety.

What I am trying to find is simple: browsing one computer's home folder from another computer, and playing the videos therein. If there's anything like Mythvideo that requires less than half of the skill requirements, I will telepathically send love to the person that informs me of it. Cheers!

---

### Post by Cantido on 2011-07-09
I found exactly what I wanted: sshfs to mount that computer's videos folder :p. It isn't exactly a MythTV substitute, but it lets me do everything that I wanted to do without anything fancy. Now I can play around with any home theater software with nothing to lose.

---

### Post by BicyclerBoy on 2011-07-09
If you are just looking for a fully integrated media centre then try XBMC.

XBMC has very good support for video decode acceleration via VDPAU or VA-API.

nfs is possibly the best file sharing tool for linux.
Gnome does have GUI tool to help file sharing between linux boxes & linux-windows..

---

### Post by N00b-un-2 on 2011-12-05
I would have to second BicycleBoy.  XBMC is highly configurable and easier to use IMHO than mythtv.  If all you're trying to do is have a simple GUI frontend to watch video files available on an NAS drive or other method of file sharing then XBMC is likely your best bet.  Samba can be a complete pain in the *** to set up, but has the advantage of being able to share files among computers using DHCP, whereas NFS requires static IP addresses.  Given the choice between the two, I'd prefer to use NFS (which I use to do exactly what you are trying to accomplish) on my home network.  The old laptop that I have plugged into my TV acts as a MythTV backend/frontend and I have it configured to access NFS shares that contain my movies, music and pictures over the network.

As for configuring either SMB or NFS, it requires a little bit of networking knowlege.

---

### Post by BicyclerBoy on 2011-12-05
A couple more options include using DLNA..
DLNA simplifies the network setup..

Client:
Rhythmbox with coherence DLNA client plugin works well in 11.04.
(Does not seem to work/exist in 11.10.)
VLC
XBMC
modern TVs (samsung work best)

Server:
mediatomb
mediaserver
coherence
mythtv backend
windows media player
etc

---

### Post by N00b-un-2 on 2011-12-05
xbmc runs fine in 11.10.  There just hasn't been much update to it since 9.10.  Seems as though XBMC spinoffs like Boxxee are still under rapid development though.  but why install boxxee if you can just buy a boxxee box?  I'm still a die hard XBMC user because like they say, if it aint broke, don't fix it.

At one point in time I loved VLC because it could handle ANYTHING you threw at it.  But as of late, the native media backends have caught up and even surpassed VLC, and the fact that they use your desktop native interface without being forced to use VLC's proprietary fugly QT widget set is always nice.  On my HTPC, I can play virtually any file natively using Parole on XFCE just fine, but the same files when played on VLC tear and artifact. 

I've never understood why in all the years that VLC has been around why no one ever bothered to properly port it to GTK or even the standard QT so it would use native icons and have a cohesive look with the rest of the apps on your computer.  One argument I guess is that since VLC is cross platform, they wanted to maintain a brand idendity (?!) but if that's the case then why stick with the straight up ugly Windows 95 era icons and widgets?  Not to mention the fact that VLC does not respect the notification area standard, nor the computer's icon theme.

---

### Post by N00b-un-2 on 2011-12-05
As for DLNA, I may not speak for everyone but I would steer clear of it.  Sure it makes connecting media devices easier for the average user, but the problem with it is that it is an industry standard endorsed by companies that stand to make money from it's existence (although the organization responsible directly for the administration of the standard itself is a non-profit).  The issue therein lies in the fact that it's only a matter of time before DLNA simply becomes a vehicle to further enforce DRM restrictions on media, and who is to say that it be capable of "spying" on your media, the way that an iTunes library does?  Also, from the way I understand it, DLNA disregards many standard security measures which creates further privacy and security concerns.  The bottom line is that if it can connect to a network, it can be hacked into.  I'd hate to see my television become a potential point of intrusion.

---

### Post by BicyclerBoy on 2011-12-05
Concerns:
Modern TVs are internet appliances..
BD players will not play latest releases without continuous firmware updates.

Not so concerned:
DLNA server & clients can be open source only..
mythtv backend is a DLNA server..
Nothing to hide (any media).

iTunes:
good points are, NO mp3, great range, NO mp3.

Security:
Don't really understand this topic..(headache inducing).
UPnP is the big weakness in a home network.

AFAIK The security problem is not so much connecting to an exposed DLNA server/client interface but being able to elevate permissions or being able to execute damaging code.
I do not have any externally visible servers.

To get the best video playback performance VLC needs to use VAAPI.
XBMC supported VDPAU from years back (a little after MythTV).

---

### Post by N00b-un-2 on 2011-12-05
I don't mean to start an argument but MythTV uses a straightforward SMB configuration.  It happens to reserve a handful of ports for specific things, but it's network capabilities are based on samba.  Don't believe me?  Delete your smb.conf and let me know if your frontends still access the backend for PVR, videos, music, etc.  I have DLNA capable devices in my house and they do not detect my MythTV backend.  As for it being open source or not, it doesn't matter.  iTunes is open source (partly) and it has been the blueprint for DRM, so I fail to see what distinction the licensing scheme the code is released under makes.
It's not like DLNA is an industry standard like IPv4 or WPA2.  It is a service which is backed and endorsed by many companies that stand to profit a great deal from it's existence, and it's purpose is centered around streaming media, the big technology pie that everyone is trying to get a slice of right now.  But I digress...

---

### Post by BicyclerBoy on 2011-12-06
MythTV-samba:
So what ?
Why would that surprise me or concern me ?
mythtv be-fe connect so easy & across any/all OS so it probably has to be samba.
There is nothing I can do about it except disconnect from internet (need it for EPG).

Like I said I have no externally visible servers (hopefully) & the network closed down as much as possible (for me).

And if your shiny new BD player is not connected to the internet then it will eventually be revoked.

MythTV DLNA server:
DLNA clients in Rhythmbox (coherence) works (11.04)
Forums show samsung TVs work okay.

I fail to see any risk with open source implementation of DLNA.
Most proprietary DLNA implements are non-standard/tweaked to trap the consumer into one brand (Apple & Sony are good at this).
I don't think DLNA is a potential revenue stream.

I can not believe iTunes is open source especially in the GPL sense..
It is, at the minimum, protected by copyright & NDA & more cash than Europe.

This thread is heading off topic, so we should head somewhere else.

---

### Post by N00b-un-2 on 2011-12-06
agreed.  What you said about proprietary DLNA is exactly what I was getting at.  Also, I do not own a bluray player for that very reason.  I have a BD ROM drive which I've flashed region free firmware onto and use MakeMKV to backup my movies, free of DRM.  But like you said, we're far off topic at this point.

---

### Post by BicyclerBoy on 2011-12-06
DLNA does not trap me because I only use GPL open source client servers.

BD region settings/zoning is only enforced by the s/w player in the host..
What you likely have is optical drive that offers up VUK even if the drive certificate is revoked.
I would not have bought any BDs without this drive feature.

MythTV can play BDs directly from optical drive..

---

