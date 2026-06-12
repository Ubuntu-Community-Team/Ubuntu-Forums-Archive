---
title: "Setting up my home network"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by duncan_bayne on 2010-12-14
Hi All,

I'm hoping someone can make some suggestions for using Ubuntu & FOSS to meet a few requirements I'm have for my home network.  

Currently I have a network containing:

[LIST]
[*]a laptop running Windows XP

[*]a desktop, several laptops and a netbook all running Ubuntu 10.10 Desktop

[*]a 'server' (an old Dell Vostro running Ubuntu 10.10 Desktop) with an SMB share containing photos, music and videos

[*]an HP Color LaserJet CP1215, attached to the server and shared via SMB

[*]an iPhone (iOS 3.x)

[*]an HTC Desire (Android 2.2)

[*]a stereo connected to the line-out on the server
[/LIST]

There's no LAN cabling; all devices including the server are on WiFi, which is why I'm running Desktop on the server as I found it easier to set up wireless networking that way.

What I'd like to be able to do is:

[LIST]
[*]Synchronize the music across all systems except the phones, thereby propagating any change on one system to all other systems.  This will allow me to take music with me away from home, load music on the phones and other MP3 players, and manage my library from any machine.

[*]Leave the videos on the server, and stream videos from the server to any OS (iOS, Android, Ubuntu, Windows) on the network.

[*]The videos should be available via an SMB share, so that I can manually copy individual videos to any system should I need to (say if I want to watch a movie on the train)

[*]Hook my stereo up to the server and play music on it, controlling the playback from any other machine on the network.

[*]Easily back up the contents of the server to an external (USB 2.0, sigh) HDD

[*]Print from any machine on the network
[/LIST]

Can anyone recommend a good approach to take here, and some software to achieve it?

One approach I was thinking was to set up cron jobs on all the machines (including the XP box courtesy Cygwin) so as to maintain synchronisation between music libraries on all machines using rsync.  The back up could happen the same way.  I'm imagining I might have conflict issues with that approach though.

Printing could be easily handled by samba, as could file shares for the video.  That's what I'm doing now in fact :-)

I'm not at all sure what to use for streaming media from the server, ditto for remote control of music playback on the server.  If it were just me I'd use ssh and rhythmbox-client for the latter, but I'd like something a lot friendlier for family & guests :-)

TIA for any suggestions ... I'm hoping there is an easy solution to all of this that I just haven't heard about :-)

Yours,
Duncan Bayne

---

