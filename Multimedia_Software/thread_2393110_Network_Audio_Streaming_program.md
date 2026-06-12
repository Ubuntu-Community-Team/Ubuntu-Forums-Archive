---
title: "Network Audio Streaming program?"
date: 2018-05-29
forum: Multimedia Software
---

### Post by RallyDarkstrike on 2018-05-29
Hi all!

This is going to be an odd question, but I am looking for a network-capable audio streaming program for a somewhat specific situation...

I'll explain! Essentially, I want a program I can run when I wish that  will start streaming the desktop audio (primarily playing music through  Clementine) from my laptop over the network so I can pick it up with VLC  on my phone for listening to music around the house. I have the  Clementine Remote app installed on my phone, so I can control Clementine  remotely from my phone and then just hear the wonderful music from the  phone as well (as Clementine has no built-in stream function, but is my  favorite music player).

I've tried using VLC to stream just audio to my phone, but can't seem to  get it to work. Is there a simple audio network streaming tool I can  install and then run or quit on command when I want to stream the music  to VLC on my phone? [IMG]https://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

Long story short, I would like a program for my laptop that I can open a GUI for, have it start streaming a stream of my desktop audio so that I can access said stream over my private network using VLC on my phone without needing any external servers or some such, and then simply close the program when I want to stop streaming.

Thanks for any suggestions! :D

---

### Post by TheFu on 2018-05-30
I don't know how to use vlc with clementine.  But here's what I use, which might provide some other options.

If you want to play music from a central system through your phone, there are 50 options. Web-based, DLNA-based, C/S based, and all the *subsonic* methods.

I use **cmus** to play music on different devices around the house - just depends on which speaker system each is connected.
For playback via DLNA or web, I use a central **plex server** with different clients.
On laptops when I'm away from home, I'll stream the web GUI through either a VPN to the house or ssh-proxy.
On Android, I'll use UPnP to access the Plex server for playback on the LAN or start up the VPN and use the plex web interface when outside the home network.
Tried Clementine, liked it, but it was heavy compared to cmus.  I never got the client/server parts working, but that was because the version in the Ubuntu repos was old and didn't support it.  It wasn't worth added hassles of using a PPA or manually installed versions to me.

VLC is heavy compared to other players, though I use it from time to time for live TV (DLNA sources) and videos, though most of the time I'll use **mpv** instead. 

For a long time, before Plex, I used **gnump3**. That is a web interface with weenie security that provides a web music file streaming capability.

My plex server only uses the internet to get metadata, I don't have any plex account and don't use any plex-specific client software.  To me, Plex is just a DLNA server.

Update - found a tool called djmount.  This tool creates a virtual file system (fuse) that can be accessed by any tools you like from DLNA servers on the network.   Been testing it out all morning.  **$ djmount /mnt/av** .... the av directory was just created and empty.  No config file.  No specifying DLNA servers.  No security. Doesn't run as root.  Sorta like sshfs. After the DLNA discovery finishes, the entire DLNA tree is shown under /mnt/av ... {device}/{type of content}/{content offers}/ .  The first run seemed to miss some DLNA announcements.  Ran it again an hour later and all the DLNA devices showed in a few seconds.  When all done, use **$ fusermount -u /mnt/av** to umount the FUSE area. 
Should be able to have minidlna or plex on a central server, use djmount on your different desktop devices, and run clementine accessing those directories with music through the FUSE mount. Android support?  Maybe not. IDK.

Lots of options.   Don't think any meet your explicit needs, but perhaps some ideas will happen?

---

### Post by SeijiSensei on 2018-05-30
As TheFu says, there are many ways to stream audio to your phone.  Playing a track in Clementine and streaming the output is probably not the easiest approach.  I use minidlna to provide DLNA services on my network.  On my Android phone i can browse the audio and video lists from minidlna with the BubbleUPnP app and play them with the default Music app or, for video, MXPlayer.

[https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA)

The same files are also available on my Roku device, my PS3, and via my TV's built-in DLNA player.

---

