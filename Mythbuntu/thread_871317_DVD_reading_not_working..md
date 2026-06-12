---
title: "DVD reading not working."
date: 2008-07-26
forum: Mythbuntu
---

### Post by DadAgain on 2008-07-26
I've just run up Mythbuntu 8.04 having had a complete failure to get ANYTHING working with Mythdora5! (ran on FC4+FC6 Mythtv for 2 years - but then foolishly rebuilt!)

Anyway - I've got a problem with DVDs. 

If I try and play one - I get to the DVD menu ok, but after selecting the language required and seeing the copyright warning it throws me back to the MythDVD page...

heres the mythfrontend log:
```
2008-07-27 09:39:34.907 Connecting to backend server: 192.168.1.XXX(dont want to post this):6543 (try 1 of 5)
2008-07-27 09:39:34.909 Using protocol version 40
2008-07-27 09:39:34.916 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Encrypted DVD support unavailable.
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title:
libdvdnav: DVD Serial Number: 4498B3D9 (GEAR):
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/username/.dvdnav/ MY_MOVIE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
2008-07-27 09:39:37.729 Opened DVD device at //dev/dvdrw
2008-07-27 09:39:37.730 There are 7 titles on the disk
2008-07-27 09:39:37.730 Title 0 has 0 parts.
2008-07-27 09:39:37.730 Title 1 has 13 parts.
2008-07-27 09:39:37.730 Title 2 has 1 parts.
2008-07-27 09:39:37.730 Title 3 has 2 parts.
2008-07-27 09:39:37.730 Title 4 has 2 parts.
2008-07-27 09:39:37.730 Title 5 has 84 parts.
2008-07-27 09:39:37.730 Title 6 has 1 parts.
2008-07-27 09:39:37.791 DPMS Deactivated
2008-07-27 09:39:38.987 AFD: Opened codec 0x84eeb10, id(MPEG2VIDEO) type(Video)
2008-07-27 09:39:38.987 NVP: Disabling Audio, params(-1,-1,-1)
2008-07-27 09:39:39.050 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-07-27 09:39:39.196 OSD Theme Dimensions W: 640 H: 480
2008-07-27 09:39:40.079 TV: Changing from None to WatchingPreRecorded
2008-07-27 09:39:40.186 Video timing method: USleep with busy wait
2008-07-27 09:39:40.786 AFD: Warning, video codec 0x84eeb10 id(MPEG2VIDEO) type (Video) already open.
2008-07-27 09:39:40.907 AFD: Opened codec 0x9a47ed0, id(DVD_SUBTITLE) type(Subtitle)
2008-07-27 09:39:40.913 AFD: Warning, video codec 0x84eeb10 id(MPEG2VIDEO) type (Video) already open.
2008-07-27 09:39:40.913 AFD: Opened codec 0x9a48ed0, id(DVD_SUBTITLE) type(Subtitle)
2008-07-27 09:39:41.101 DPMS Reactivated.
2008-07-27 09:39:43.705 DPMS Deactivated
2008-07-27 09:39:43.706 DPMS Reactivated.
2008-07-27 09:39:46.914 DPMS Deactivated
2008-07-27 09:39:47.016 Error reading block from DVD: Error reading NAV packet.
2008-07-27 09:39:47.049 TV: Attempting to change from WatchingPreRecorded to None
2008-07-27 09:39:47.076 TV: Changing from WatchingPreRecorded to None
2008-07-27 09:39:48.116 DPMS Reactivated.

```

Any ideas what "Error reading block from DVD: Error reading NAV packet." means? Is this some kind of region encoding problem? Anyone got a fix?

FWIW If I try and rip the disk I get the follwoing in mtd.log
```
09:43:44: a client socket has been opened
09:44:00: launching job: job dvd 1 1 -1 0 -1 /var/lib/mythtv/videos/MY_MOVIE
09:44:00: Using DVD source: /dev/dvdrw
09:44:00: ISO DVD image copy to: /var/lib/mythtv/videos/MY_MOVIE_001of
09:44:14: Error: DVDISOCopyThread dvd device read error
09:44:15: job failed: job dvd 1 1 -1 0 -1 /var/lib/mythtv/videos/MY_MOVIE
```

Any help would be appreciated

---

### Post by funkydan2 on 2008-07-27
Have you installed 'libdvdcss'?

Comercial DVDs are encrypted, so that even though you've paid for the DVD and you've paid for the DVD player/drive, you can't read the DVD without a decryption key that can't be included with Ubuntu for legal reasons (i think).

Anyway, it's really easy to get this working in mythbuntu.  You need to open the control centre (Applications->System->Mythbuntu Control Centre on my computer) then go down to the menu entry on the left that says 'Proprietary Codecs'.  Select 'libdvdcss' (and the other entries as well!) then click apply.  You should now be able to play DVDs.

Daniel

---

### Post by DadAgain on 2008-07-27
Seems I'd installed it (from command line) - but not told MythTV to use it!

Mythbuntu Control Centre was the hint I needed THANKS a bunch!:)

---

