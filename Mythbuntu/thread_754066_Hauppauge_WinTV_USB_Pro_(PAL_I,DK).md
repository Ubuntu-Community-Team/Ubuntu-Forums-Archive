---
title: "Hauppauge WinTV USB Pro (PAL I,D/K)"
date: 2008-04-13
forum: Mythbuntu
---

### Post by dead_bored on 2008-04-13
ex-windows, new to linux, trying to get mythtv working on ubuntu7.1. failing pretty miserably.

I have video into the s-video socket on the usb device. no tuner involved just screen capture. 

tried the following to see if drivers work (all installed with apt-get):
**tvtime** - flashes up and then dissappears. cant find the logfile to include in post.
**zapper** - has an option to set s-video - works - dont think it has correct standard - limited selection pal, secam etc. but at least i know everything is cool with drivers etc.
**xawtv** - makes screen go black - only way to get it back is to reboot - reminds me of windows. 
**VLC** - open capture card - video4linux and pvr make the usb box light up but no picture.
**MythTV - mythbuntu**- video card is picked up correctly in the back end - set up source, channel etc on s-video - when i start front-end and choose 'Watch TV' get a black screen for a while, then back to front-end menu. logs.
**dont know if relevant but in the beginning back-end could not connect to mysql so had to change mythtv password and then it could connect - throught console in system-admin.

syslog says: usbvision_probe: Hauppauge WinTV USB Pro (PAL I,D/K) found

mythtv front-end says:
2008-04-13 15:40:11.558 Connected to database 'mythconverg' at host: localhost
2008-04-13 15:40:11.573 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-13 15:40:11.575 Using protocol version 31
2008-04-13 15:40:11.583 TV: Attempting to change from None to WatchingLiveTV
2008-04-13 15:40:11.584 Using protocol version 31
2008-04-13 15:40:18.589 MythSocket(84d6778:14): readStringList: Error, timeout (quick).
2008-04-13 15:40:18.590 RemoteEncoder::SendReceiveStringList(): No response.
2008-04-13 15:40:18.590 GetEntryAt(-1) failed.
2008-04-13 15:40:18.591 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2008-04-13 15:40:18.591 TV Error: LiveTV not successfully started
2008-04-13 15:40:18.592 TV Error: LiveTV not successfully started
2008-04-13 15:40:18.595 TV: Deleting TV Chain in destructor
2008-04-13 15:40:18.599 DPMS Deactivated
2008-04-13 15:40:18.599 DPMS Reactivated.

mythtv-backend log says
2008-04-13 15:39:59.118 Seem to be woken up by USER
2008-04-13 15:40:11.575 MainServer::HandleAnnounce Monitor
2008-04-13 15:40:11.579 adding: homebuntu as a client (events: 0)
2008-04-13 15:40:11.580 MainServer::HandleAnnounce Monitor
2008-04-13 15:40:11.580 adding: homebuntu as a client (events: 1)
2008-04-13 15:40:11.584 MainServer::HandleAnnounce Playback
2008-04-13 15:40:11.585 adding: homebuntu as a client (events: 0)
2008-04-13 15:40:11.587 TVRec(1): Changing from None to WatchingLiveTV
2008-04-13 15:40:11.591 TVRec(1): HW Tuner: 1->1
2008-04-13 15:40:20.756 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-04-13 15:40:20.759 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-04-13 15:40:20.759 TVRec(1) Error: Failed to set channel to 69.
2008-04-13 15:40:20.778 TVRec(1) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Sun Apr 13 15:40:20 2008) endts(Sun Apr 13 15:40:20 2008)
             recstartts(Sun Apr 13 15:40:20 2008) recendts(Sun Apr 13 15:40:20 2008)
             title()
2008-04-13 15:40:20.823 Unknown video codec
2008-04-13 15:40:20.838 Please go into the TV Settings, Recording Profiles and
2008-04-13 15:40:20.838 setup the four 'Software Encoders' profiles.
2008-04-13 15:40:20.839 Assuming RTjpeg for now.
2008-04-13 15:40:20.840 NVR: Error, unknown audio codec
VIDIOCGCAP:: Invalid argument
2008-04-13 15:40:21.179 TVRec(1): Changing from WatchingLiveTV to None
2008-04-13 15:40:21.219 Finished recording : channel 4294967295
2008-04-13 15:40:21.227 MythSocket(8197c70:-1): writeStringList: Error, socket went unconnected.
2008-04-13 15:42:17.096 Expiring  from Sun Apr 13 15:40:20 2008, 0 MBytes, forced expire (LiveTV recording)

Please i dont want to go back to windows.:(

---

