---
title: "Myth backend + xbmc frontend... works in windows, not ubuntu..."
date: 2010-09-16
forum: Mythbuntu
---

### Post by Cowzor on 2010-09-16
So yesterday I got my hands on a TV tuner card for free, and since I still had a server lying around not being used from an old project, I thought I'd put it in there so I could watch TV on my ubuntu-XBMC media center.

It didn't work though, as whenever I would select a channel from the live channels it would simply do nothing. I googled it for hours but came up with nothing.

This morning when I got up, I decided to install XBMC on my windows machine and connect it to the backend just to see what would happen - I got a green picture and funny audio. I changed the codec, and everything works the way it's supposed to on my windows machine. Not on my ubuntu machine though, which is where it's really supposed to work.

Since it's working on one machine and not the other, my guess is it's one silly little configuration error somewhere, but I cannot find it for the life of me.

Here's a log from XBMC:

```
23:44:27 T:3033757584 M:2373750784  NOTICE: DVDPlayer: Opening: myth://myth:XXXXXXXXX@192.168.0.103/channels/40.ts
23:44:27 T:2852154256 M:2373750784   DEBUG: thread start, auto delete: 1
23:44:27 T:3033757584 M:2373750784 WARNING: CDVDMessageQueue(player)::Put MSGQ_NOT_INITIALIZED
23:44:27 T:2863315856 M:2373750784   DEBUG: thread start, auto delete: 0
23:44:27 T:2863315856 M:2373750784  NOTICE: Creating InputStream
23:44:27 T:2863315856 M:2373750784   DEBUG: SECTION:LoadDLL(xbmc.so)
23:44:27 T:2863315856 M:2373750784   DEBUG: Loading Internal Library
23:44:27 T:3032021904 M:2373750784   DEBUG: thread start, auto delete: 0
23:44:27 T:2863315856 M:2373750784   DEBUG: SetupLiveTV - recorder isn't running, let's start it
23:44:29 T:3032021904 M:2373718016   DEBUG: Process - MythTV event UNKNOWN (error?)
23:44:29 T:3032021904 M:2373718016   DEBUG: Process - MythTV event RECORDING_LIST_CHANGE
23:44:29 T:3032021904 M:2373718016   DEBUG: Process - MythTV event LIVETV_CHAIN_UPDATE: LIVETV_CHAIN UPDATE live-media-2010-09-16T23:44:27
23:44:29 T:2863315856 M:2373718016   ERROR: SetupLiveTV - unable to spawn live tv: Failed to setup livetv.
23:44:29 T:2863315856 M:2373718016   ERROR: CDVDPlayer::OpenInputStream - error opening [myth://myth:XXXXXXXXX@192.168.0.103/channels/40.ts]
23:44:29 T:2863315856 M:2373718016  NOTICE: CDVDPlayer::OnExit()
23:44:29 T:2863315856 M:2373718016  NOTICE: CDVDPlayer::OnExit() deleting input stream
23:44:29 T:3033757584 M:2373718016   DEBUG: OnPlayBackStopped - Playback was stopped
23:44:29 T:3033757584 M:2373718016   ERROR: Playlist Player: skipping unplayable item: 0, path [myth://myth:XXXXXXXXX@192.168.0.103/channels/40.ts]
23:44:29 T:3033757584 M:2373718016   DEBUG: Playlist Player: one or more items failed to play... aborting playback
```

And the log from the mythtv backend:

```
2010-09-17 00:03:59.672 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 40!
2010-09-17 00:03:59.683 MainServer::HandleAnnounce Playback
2010-09-17 00:03:59.700 adding: media as a client (events: 0)
2010-09-17 00:03:59.710 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 40!
2010-09-17 00:03:59.718 MainServer::HandleAnnounce Playback
2010-09-17 00:03:59.725 adding: media as a client (events: 1)
2010-09-17 00:03:59.735 MainServer::HandleVersion - Client speaks protocol version 8 but we speak 40!
2010-09-17 00:03:59.738 MainServer::HandleAnnounce Playback
2010-09-17 00:03:59.738 adding: media as a client (events: 0)
2010-09-17 00:03:59.743 TVRec(1): Changing from None to WatchingLiveTV
2010-09-17 00:03:59.753 TVRec(1): HW Tuner: 1->1
2010-09-17 00:04:00.028 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
[mpeg4 @ 0xb73a1b88]2010-09-17 00:04:01.131 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
removing common factors from framerate
strange error flushing buffer ...
```

Anyone know what to do?

---

### Post by nickrout on 2010-09-17
what is your video capture device?

---

