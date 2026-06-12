---
title: "MythVideo playback issues"
date: 2008-12-27
forum: Mythbuntu
---

### Post by Boppy3125 on 2008-12-27
I am having a hard time with this one.  I recently moved my movies around due to space issues.  After moving them all my VIDEO_TS folders changed to video_ts, that cost me an hour of troubleshooting and then renaming.  Now I still can't play any.  I can browse to the shared folder from my windows machine and play with VLC, so I know the folder structures and such are right.  These worked prior to my moving them in myth.  I have messed with ownership to see if it mattered if mythtv or my user owned the folders and files, but that didn't seem to matter.  I am missing something else possibly obvious.  Here is what I see in mythfrontend.log when I try to select one:

```
2008-12-27 00:10:11.989 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/video-ui.xml
2008-12-27 00:10:14.399 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/curt/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2008-12-27 00:10:14.400 Opened DVD device at /var/lib/myth1/videos/Ava/Little Mermaid II
2008-12-27 00:10:14.400 There are 1 titles on the disk
2008-12-27 00:10:14.400 Title 0 has 0 parts.
2008-12-27 00:10:14.516 DPMS Deactivated 
2008-12-27 00:10:14.670 NVP: Couldn't find a matching decoder for: /var/lib/myth1/videos/Ava/Little Mermaid II
2008-12-27 00:10:14.671 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-12-27 00:10:14.671 TV: Changing from None to WatchingPreRecorded
2008-12-27 00:10:14.673 Marking recording as watched using offset 4 minutes
2008-12-27 00:10:14.673 TV: Attempting to change from WatchingPreRecorded to None
2008-12-27 00:10:14.673 TV: Changing from WatchingPreRecorded to None
2008-12-27 00:10:15.722 DPMS Reactivated.
```

Is that normal stuff from libdvd from a folder of a ripped movie?  All my searches for the NVP: Couldn't find matching... message came up with older LiveTV problems.

I am running mythbuntu 8.10 recently checked for updates.  VIDEO_TS is set to use Internal player.  Any thoughts from anyone?:confused:

---

### Post by Boppy3125 on 2008-12-27
No one out there this week or no ideas what is wrong with my internal player.  So, does anyone know how to reset everything without reinstalling.  My thoughts now is just a fresh re-install, but I have to save off all of these movies first.  If I can do something to basically clear MythTV and then start over, without doing the base OS, that might be my answer.  (this is my secondary front end, Mythbuntu 8.10.)

---

