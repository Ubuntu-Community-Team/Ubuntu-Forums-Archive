---
title: "Problems with using SMBv2 and higher - client won't connect!"
date: 2021-05-03
forum: MINT
---

### Post by username2758 on 2021-05-03
Hey,

I am definitely not an expert when it comes to networking.

I have been trying to set up a Samba server to share files between my devices at home and one of these devices is the WDTV Live Streaming which only supports SMBv1. So I tried to add the "server min protocol = NT1" string to no avail. If I try to connect with the NT1 string, the WDTV Live Streaming will give me an error message saying it can't connect to the selected source. But if I try to connect without the NT1 string, the WDTV Live Streaming will give me an error saying the password is wrong.

Does anybody know of a possible workaround? Since the WDTV Live Streaming only supports SMBv1. Is there a way to downgrade the SMB protocol version? Or maybe using a virtual machine on top of the main operating system?

I am currently using Linux Mint 20.1 Ulyssa.

---

### Post by TheFu on 2021-05-03
Do : 
[https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480](https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480) 
or
[https://ubuntuforums.org/showthread.php?t=2447575&p=13974310#post13974310](https://ubuntuforums.org/showthread.php?t=2447575&p=13974310#post13974310)
help?
There are many interactions between different settings that are beyond my skill. I think the 2nd link has more details.

---

### Post by slickymaster on 2021-05-04
*Thread moved to **MINT**.*

---

### Post by username2758 on 2021-05-04
> **TheFu said:**
> Do : 
[https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480](https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480) 
or
[https://ubuntuforums.org/showthread.php?t=2447575&p=13974310#post13974310](https://ubuntuforums.org/showthread.php?t=2447575&p=13974310#post13974310)
help?
There are many interactions between different settings that are beyond my skill. I think the 2nd link has more details.
Jesus! It worked! Thank you man, you are my savior! :D

The following strings did it, and now my good old WDTV Live Streaming box connects to Samba no problem!
```
client lanman auth = yes
ntlm auth = yes
```
But can anybody explain what those lines mean?

---

### Post by TheFu on 2021-05-04
> **username2758 said:**
>  
But can anybody explain what those lines mean?

They say to use the worst security possible. samba.org will have more details, if you care.

If you don't want any security and just want to stream media, use a DLNA server, not samba. I think a WD Live HD TV does DLNA.
There are F/LOSS firmwares available [http://forum.wdlxtv.com/](http://forum.wdlxtv.com/) for the WD TV Live devices, BTW. That firmware can make it a little Linux server, if you like. These days, most people would be better off using a Raspberry-Pi v3 or newer with OSMC loaded [https://osmc.tv/](https://osmc.tv/) instead of the WDTV.  The supported things that a r-pi can accomplish for video really are amazing.  A v4 r-pi can handle 4K video, for example.

---

### Post by username2758 on 2021-05-04
> **TheFu said:**
> They say to use the worst security possible. samba.org will have more details, if you care.

If you don't want any security and just want to stream media, use a DLNA server, not samba. I think a WD Live HD TV does DLNA.
There are F/LOSS firmwares available [http://forum.wdlxtv.com/](http://forum.wdlxtv.com/) for the WD TV Live devices, BTW. That firmware can make it a little Linux server, if you like. These days, most people would be better off using a Raspberry-Pi v3 or newer with OSMC loaded [https://osmc.tv/](https://osmc.tv/) instead of the WDTV.  The supported things that a r-pi can accomplish for video really are amazing.  A v4 r-pi can handle 4K video, for example.
Thank you! I didn't know about F/LOSS alternative firmware. I will have a look!

I don't think the original firmware for WDTV Live Streaming supports DLNA, but it says it supports NFS. I never tried NFS before, what is it? Is it secure? Should I give it a try?

The thing about this particular media player is that I have recently had a bad experience using a tv box (Android TV) where I tried many different video players available on Google Store (Kodi, VLC, etc) but none of them gave me a satisfactory experience like WDTV Live Streaming does. More specifically, when I use Android TV software via a tv box with my conventional smart TV I get terrible inverse ghosting, jittering and issues regarding framerate/audio sync etc. It appears it lacks proper playback configuration or something which a dedicated media player doesn't. I don't know.

---

### Post by TheFu on 2021-05-04
Android sucks.  Android TV players have all the issues that Android phones have. They never get patched. We are stuck with the shipped OS because those are never upgraded by the vendor, and we'd stuck with some bad app-store.

Raspberry Pis run Linux AND feel like Linux.  No phoning home to Google. No bloated Java crap software required.  Most use APT, so **sudo apt install** and **sudo apt upgrade** are how you maintain the system, just like you do with Ubuntu.  Raspbian, the normal Raspberry-Pi distro, is based on debian.  It "feel" right.

Debian supports repos, PPAs, installing from source, and all the other normal OS and packaging methods.  My r-pi v2 is still great as a 1080p driver for our projection system and THX receiver.  I have a r-pi v3 as well, but the extra performance doesn't make any difference for audio/video playback, so it isn't hooked up to the projection room.  A r-pi v4 is a huge leap in capability.  BTW, all of these can run home document, storage, calendar, servers fine.  I don't do that, but people do.  Some people run Nextcloud on their raspberry PI systems and have it do
[LIST]
[*]documents
[*]calendars
[*]email
[*]music
[/LIST]
I do run mpd on my r-pi systems next to OSMC for nice music playback controlled by any mpd client.  ncmpc is the Linux client I use. On android (phones/tablets), MAPS - I think that's the name - connects to any of my 3 mpd servers depending on which room I'd like to listen inside.

NFS can be very secure with server-to-server Kerberos authentication and AES encrypted connections, but most people in home environments want simple and fast, that isn't open to the world.  NFS is the native file sharing used by Unix systems for 30+ yrs.  It is server-to-server, unlike Samba which is user-to-server.  NFS supports native POXIS users, groups, and permissions.  chmod works, provided the underlying file system supports is, so be certain to avoid Windows-file systems like NTFS.  Use EXT4, if you don't have a specific reason to use something else.  NFS is two installs (one on the client and 1 on the server), then a config file on the server, which says which clients can connect and how, then on each client system, the fstab says where to mount the storage.  For streaming videos, DLNA seems the best, then NFS, then CIFS as the worst.
There are 2 bad things about NFS.  
1) Clients and servers are usually determined purely by IP address, so both should have static IPs. If you don't manage your network so every server and client has static IPs, this will suck for you.
2) userids and groupids - the numbers - have to match between the clients and servers.  Use the 'id' command.  It is only those numbers that matter, not the names.  People with OSX run into a problem immediately because OSX starts uids at 500 and Linux starts them at 1000.  So, one of those systems needs to change the uid for the users.  There is an ID-mapping tool, but I've never seen it work or got it working myself.  In a corporate environment, users and groups are centrally managed via LDAP, so this isn't an issue.  Only the users and groups that actually make use of the NFS storage need to be carefully mapped, so it isn't like we need to map the 20-50 daemon/service accounts between all the systems. Usually, it is just the human users and perhaps the DLNA server account.  It isn't the end of the world if the userids don't map 1-for-1, but security will likely be less if not.

---

### Post by username2758 on 2021-05-05
> **TheFu said:**
> Android sucks.  Android TV players have all the issues that Android phones have. They never get patched. We are stuck with the shipped OS because those are never upgraded by the vendor, and we'd stuck with some bad app-store.

Raspberry Pis run Linux AND feel like Linux.  No phoning home to Google. No bloated Java crap software required.  Most use APT, so **sudo apt install** and **sudo apt upgrade** are how you maintain the system, just like you do with Ubuntu.  Raspbian, the normal Raspberry-Pi distro, is based on debian.  It "feel" right.

Debian supports repos, PPAs, installing from source, and all the other normal OS and packaging methods.  My r-pi v2 is still great as a 1080p driver for our projection system and THX receiver.  I have a r-pi v3 as well, but the extra performance doesn't make any difference for audio/video playback, so it isn't hooked up to the projection room.  A r-pi v4 is a huge leap in capability.  BTW, all of these can run home document, storage, calendar, servers fine.  I don't do that, but people do.  Some people run Nextcloud on their raspberry PI systems and have it do
[LIST]
[*]documents 
[*]calendars 
[*]email 
[*]music 
[/LIST]
I do run mpd on my r-pi systems next to OSMC for nice music playback controlled by any mpd client.  ncmpc is the Linux client I use. On android (phones/tablets), MAPS - I think that's the name - connects to any of my 3 mpd servers depending on which room I'd like to listen inside.

NFS can be very secure with server-to-server Kerberos authentication and AES encrypted connections, but most people in home environments want simple and fast, that isn't open to the world.  NFS is the native file sharing used by Unix systems for 30+ yrs.  It is server-to-server, unlike Samba which is user-to-server.  NFS supports native POXIS users, groups, and permissions.  chmod works, provided the underlying file system supports is, so be certain to avoid Windows-file systems like NTFS.  Use EXT4, if you don't have a specific reason to use something else.  NFS is two installs (one on the client and 1 on the server), then a config file on the server, which says which clients can connect and how, then on each client system, the fstab says where to mount the storage.  For streaming videos, DLNA seems the best, then NFS, then CIFS as the worst.
There are 2 bad things about NFS.  
1) Clients and servers are usually determined purely by IP address, so both should have static IPs. If you don't manage your network so every server and client has static IPs, this will suck for you.
2) userids and groupids - the numbers - have to match between the clients and servers.  Use the 'id' command.  It is only those numbers that matter, not the names.  People with OSX run into a problem immediately because OSX starts uids at 500 and Linux starts them at 1000.  So, one of those systems needs to change the uid for the users.  There is an ID-mapping tool, but I've never seen it work or got it working myself.  In a corporate environment, users and groups are centrally managed via LDAP, so this isn't an issue.  Only the users and groups that actually make use of the NFS storage need to be carefully mapped, so it isn't like we need to map the 20-50 daemon/service accounts between all the systems. Usually, it is just the human users and perhaps the DLNA server account.  It isn't the end of the world if the userids don't map 1-for-1, but security will likely be less if not.
Thanks for the suggestions! 

I had never thought about the possibility of buying a Raspberry Pi as a replacement or next media player, might give it a try too. But right now I can't spend a dime because already spent too much. Maybe the day I finally buy a 4k television I might replace the good old WDTV Live Streaming for good.

A few questions on the Raspberry Pi though, since it's based on Debian and not having x86-64 hardware what kind of software I will be actually running on it? For example if I install VLC, will it be VLC based on Android or Debian? If I recall correctly, there is a mobile version of Ubuntu for smartphones. Is that it? I am worried about playback issues regarding framerate and such.

I am still looking at WDLXTV.

---

### Post by TheFu on 2021-05-05
> Raspberry Pis run Linux AND feel like Linux.

It is debian.  
It is NOT android.
The programs are debian versions. If you load OSMC, then it has a 10ft interface designed to work as friendly WDTV box, but without the limitations and more addons.  99% of kodi addons are cross platform, so they work. It has skins just like Kodi does on other platforms. If you like, install kodi on you Ubuntu system and run it.  That's what it will look like with the "heavy" theme on OSMC.  OSMC's default theme is light and designed for use on a R-pi v2.  

There are thousands of youtube videos, if you want to see it before hand.  I don't have any media on my OSMC system, just the OS. Inside OSMC, I point it at either NFS storage with media or DLNA media servers.

The default r-pi costs $35.  You need a 
[LIST]
[*]case; lots of $5-$8 exist.
[*]heat sinks for the pi chips/ may want a fan for a v4 to prevent heat throttling of the CPU; sometimes included with the pi.
[*]power supply - get theirs, $8; most other USB 5V power isn't good for the Pi and will undervolt or not provide sufficient power for the v4
[*]microSD card - cheap ones should last a few years if you don't put media on it. 8G is fine.  If you do put media on it and use the library organization, get a "high endurance" microSD.  Think those are $10 for 32G-64G.
[*]appropriate HDMI cable - v2/v3 use full sized, but v4 uses a micro-HDMI.
[*]audio out cable - 3.5mm jack or just use the audio in the HDMI signal. I split audio from the hdmi because my old receiver doesn't support hdmi
[*]USB keyboard, if you need to hook up a keyboard. I don't, but I'm pretty good at linux networking and ssh. I can set those up before putting the microSD into the Pi and booting. Or get the MAC and use DHCP reservations.
[*]Computer to do a bit-for-bit copy of the OSMC img to the microSD, then mount it and tweak the network settings, so ssh works (or not)
[*]Wired ethernet cable; wifi always sucks. Avoid wifi. Always.
[/LIST]

And obviously, you'll want to download an image with the OS you will run.  There is no "install". It is copying an image onto the microSD. Bit-for-bit. That's it.  Raspbian (the raspberry-pi debian release) is a no-gui image install designed to work on raspberry-pis and understands the network card, storage, video drivers, etc.

There's no need to buy the commercial $2 video decoder licenses 99% of the time. The h.264 one isn't needed, as it is free now. The mpeg2 license isn't needed on v4 pi hardware, since the CPU can easily decode 1080p mpeg2. v2/v3 pis don't have hardware support for h.265, so the HEVC codec stuff won't play well, except on v4 pis.  

So, it comes down to the resolution and video codecs for any media you want to play which raspberry-pi is needed.
[LIST]
[*]4k or HEVC or h.265 - v4 needed. Anything with less resolution should play fine using software decoding if hardware decoding isn't there.
[*]1080p mpeg or h.264 - v3 needed.  Anything with less resolution should play fine using software decoding if hardware decoding isn't there.
[*]1080p w/h.264 v2 needed.  mpeg2 playback works well for 720p and less.  Any video resolution of 720 or less using almost any video codec should play fine.
[/LIST]

What should play fine on all?  Any video of 720p or less resolution with flash/flv, mpeg2, divx, xvid, and 50 other odd video codecs that never took off.

Just to clarify:
AVI is just a container, not a video codec.
MPEG4 is just a container, not a video codec.
mkv is just a container, not a video codec.
webm is just a container, not a video codec.
MOV is just a container, not a video codec.

Each of those containers has a typical video/audio codec pair, but lots of different codecs can be used.

Did I mention - avoid wifi?

---

### Post by username2758 on 2021-05-07
> **TheFu said:**
> It is debian.  
It is NOT android.
The programs are debian versions. If you load OSMC, then it has a 10ft interface designed to work as friendly WDTV box, but without the limitations and more addons.  99% of kodi addons are cross platform, so they work. It has skins just like Kodi does on other platforms. If you like, install kodi on you Ubuntu system and run it.  That's what it will look like with the "heavy" theme on OSMC.  OSMC's default theme is light and designed for use on a R-pi v2.  

There are thousands of youtube videos, if you want to see it before hand.  I don't have any media on my OSMC system, just the OS. Inside OSMC, I point it at either NFS storage with media or DLNA media servers.

The default r-pi costs $35.  You need a 
[LIST]
[*]case; lots of $5-$8 exist. 
[*]heat sinks for the pi chips/ may want a fan for a v4 to prevent heat throttling of the CPU; sometimes included with the pi. 
[*]power supply - get theirs, $8; most other USB 5V power isn't good for the Pi and will undervolt or not provide sufficient power for the v4 
[*]microSD card - cheap ones should last a few years if you don't put media on it. 8G is fine.  If you do put media on it and use the library organization, get a "high endurance" microSD.  Think those are $10 for 32G-64G. 
[*]appropriate HDMI cable - v2/v3 use full sized, but v4 uses a micro-HDMI. 
[*]audio out cable - 3.5mm jack or just use the audio in the HDMI signal. I split audio from the hdmi because my old receiver doesn't support hdmi 
[*]USB keyboard, if you need to hook up a keyboard. I don't, but I'm pretty good at linux networking and ssh. I can set those up before putting the microSD into the Pi and booting. Or get the MAC and use DHCP reservations. 
[*]Computer to do a bit-for-bit copy of the OSMC img to the microSD, then mount it and tweak the network settings, so ssh works (or not) 
[*]Wired ethernet cable; wifi always sucks. Avoid wifi. Always. 
[/LIST]

And obviously, you'll want to download an image with the OS you will run.  There is no "install". It is copying an image onto the microSD. Bit-for-bit. That's it.  Raspbian (the raspberry-pi debian release) is a no-gui image install designed to work on raspberry-pis and understands the network card, storage, video drivers, etc.

There's no need to buy the commercial $2 video decoder licenses 99% of the time. The h.264 one isn't needed, as it is free now. The mpeg2 license isn't needed on v4 pi hardware, since the CPU can easily decode 1080p mpeg2. v2/v3 pis don't have hardware support for h.265, so the HEVC codec stuff won't play well, except on v4 pis.  

So, it comes down to the resolution and video codecs for any media you want to play which raspberry-pi is needed.
[LIST]
[*]4k or HEVC or h.265 - v4 needed. Anything with less resolution should play fine using software decoding if hardware decoding isn't there. 
[*]1080p mpeg or h.264 - v3 needed.  Anything with less resolution should play fine using software decoding if hardware decoding isn't there. 
[*]1080p w/h.264 v2 needed.  mpeg2 playback works well for 720p and less.  Any video resolution of 720 or less using almost any video codec should play fine. 
[/LIST]

What should play fine on all?  Any video of 720p or less resolution with flash/flv, mpeg2, divx, xvid, and 50 other odd video codecs that never took off.

Just to clarify:
AVI is just a container, not a video codec.
MPEG4 is just a container, not a video codec.
mkv is just a container, not a video codec.
webm is just a container, not a video codec.
MOV is just a container, not a video codec.

Each of those containers has a typical video/audio codec pair, but lots of different codecs can be used.

Did I mention - avoid wifi?
Thank you TheFu!

Good to know that only Raspberry Pi v4 has HEVC support. I might give it a try someday, but not now.

---

