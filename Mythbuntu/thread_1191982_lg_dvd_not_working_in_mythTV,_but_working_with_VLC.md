---
title: "lg dvd not working in mythTV, but working with VLC player"
date: 2009-06-19
forum: Mythbuntu
---

### Post by zapstrap on 2009-06-19
Here's my hardware:

ASUS P4P800VM
3.0GHz P4
1GB ram
40GB ATA - EXT3, holds OS, apps.
1.5TB SATA - XFS, mounted to /media/archive, holds all recordings.
LG DVD drive (new, but not bluray/hd)
Hauppauge PVR-150
eVGA e-GeForce N6200 256MB video card (not using mobo onboard video)
Mythbuntu 9.04 standalone
Installed extra codecs so DVDs will play.

If I put in a DVD, close (or don't have open in the first place) the frontend, and open vlc player, I can play the DVD, no problem.  If I try to play the same DVD via the mythTV frontend, all I get is the FBI warning screen.  The frontend locks up, and the only way out is to open a terminal window and kill the process.

Oddly enough, ripping from within mythTV seems to work, but if I try to play back the ripped file, it also won't play (it hangs at the warning screen too).  It's an ISO file, not sure how I got this, but it does appear in the mythTV recordings archive.

I've noticed mplayer is the app. is being called to play the DVD, and that seems to work if called stand-alone.

Am I missing something in the setup for playing discs?

The backend log file didn't have anything noteworthy in it, but here's my frontend log file:

2009-06-19 12:30:20.332 No theme dir: /home/lawrence/.mythtv/themes/Mythbuntu-8.04
2009-06-19 12:31:15.724 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000003fa
libdvdread: Elapsed time 0
<<<snip>>>
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003ba9e5
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: movie
libdvdnav: DVD Serial Number: 12345678 
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/lawrence/.dvdnav/movie.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2009-06-19 12:31:16.375 Opened DVD device at /dev/dvd
2009-06-19 12:31:16.535 There are 54 titles on the disk
2009-06-19 12:31:16.535 Title 0 has 0 parts.
<<<snip>>>
2009-06-19 12:31:16.537 Title 53 has 3 parts.
2009-06-19 12:31:16.546 DPMS Deactivated 
2009-06-19 12:31:16.731 AFD: Opened codec 0x8a3bda0, id(MPEG2VIDEO) type(Video)
2009-06-19 12:31:16.731 NVP: Disabling Audio, params(-1,-1,-1)
2009-06-19 12:31:16.765 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-06-19 12:31:16.810 OSD Theme Dimensions W: 640 H: 480
2009-06-19 12:31:17.195 TV: Changing from None to WatchingPreRecorded
2009-06-19 12:31:17.310 Video timing method: USleep with busy wait
2009-06-19 12:31:17.349 DPMS Reactivated.
2009-06-19 12:31:17.450 DPMS Deactivated 
2009-06-19 12:31:17.462 AFD: Warning, video codec 0x8a3bda0 id(MPEG2VIDEO) type (Video) already open.
2009-06-19 12:31:17.550 DPMS Reactivated.
2009-06-19 12:31:17.585 AFD: codec AC3 has 0 channels
2009-06-19 12:31:17.587 AFD: Opened codec 0x9491970, id(AC3) type(Audio)
2009-06-19 12:31:17.593 Opening audio device 'default'. ch 2(2) sr 48000
2009-06-19 12:31:17.593 Opening ALSA audio device 'default'.
2009-06-19 12:31:17.657 NVP: Enabling Audio
2009-06-19 12:31:17.751 DPMS Deactivated 
2009-06-19 12:31:17.812 [ac3 @ 0xb73b8744]frame CRC mismatch
2009-06-19 12:31:17.851 DPMS Reactivated.
2009-06-19 12:31:17.858 DPMS Deactivated 
2009-06-19 12:31:17.859 DPMS Reactivated.
2009-06-19 12:31:20.664 DPMS Deactivated 
2009-06-19 12:31:20.668 NVP: Disabling Audio, params(-1,-1,-1)
2009-06-19 12:31:20.764 DPMS Reactivated.
2009-06-19 12:31:20.803 AFD: Warning, video codec 0x8a3bda0 id(MPEG2VIDEO) type (Video) already open.
2009-06-19 12:31:20.923 AFD: codec AC3 has 0 channels
2009-06-19 12:31:20.924 AFD: Opened codec 0x8ad5120, id(AC3) type(Audio)
2009-06-19 12:31:20.928 Opening audio device 'default'. ch 2(2) sr 48000
2009-06-19 12:31:20.928 Opening ALSA audio device 'default'.
2009-06-19 12:31:20.932 NVP: Enabling Audio
2009-06-19 12:31:20.973 DPMS Deactivated 
2009-06-19 12:31:21.063 [ac3 @ 0xb73b8744]frame CRC mismatch
2009-06-19 12:31:21.073 DPMS Reactivated.

I've snipped out the rather lengthy list of messages reading each piece of the disc.  These all look good to me.  I also changed the movie title to "movie" and changed the serial number.  I wouldn't want to offend the copyright police.  Well, I would, but this isn't the time or place. :)

If I kill the frontend, as it's locked up at this point, and run mplayer directly, the movie plays fine.  I get a popup window with this error though:

Error!  AO: [pulse] Failed to connect to server: Connection refused.

Also, the disc won't eject after mythTV has locked up.  Pushing the eject button on the DVD player doesn't work either.  If I kill the frontend, right-click on the disc icon on the desktop, I can get it to eject, however.

---

### Post by klc5555 on 2009-06-19
> **zapstrap said:**
> Here's my hardware:

ASUS P4P800VM
3.0GHz P4
1GB ram
40GB ATA - EXT3, holds OS, apps.
1.5TB SATA - XFS, mounted to /media/archive, holds all recordings.
LG DVD drive (new, but not bluray/hd)
Hauppauge PVR-150
eVGA e-GeForce N6200 256MB video card (not using mobo onboard video)
Mythbuntu 9.04 standalone
Installed extra codecs so DVDs will play.

The title kind of says it all.  If I put in a DVD, close (or don't have open in the first place) the frontend, and open vlc player, I can load and watch the DVD, no problem.  If I try to watch a DVD via the mythTV frontend, all I get is the FBI warning screen.  The frontend locks up, and the only choice is to open a terminal window and kill the process.

Oddly enough, ripping from within mythTV seems to work, but if I try to play back the ripped file, it also won't play (it hangs at the warning screen too).  It's an ISO file, not sure how I got this, but it does appear in the mythTV recordings archive.

I've noticed mplayer is the app. is being called to play the DVD, and that seems to work if called stand-alone.

Am I missing something in the setup for playing discs?

I think this is a known bug in the internal player with stationary frames on some DVDs (not all). I don't have a real solution, but I do have a workaround. If, instead of an ".iso" rip of the entire dvd, you do a "perfect" quality rip of just the movie itself, you'll avoid the FBI-stationary-picture hang, and the ripped file will play very nicely in the internal player.

---

### Post by JoseRijo on 2009-06-21
I don't have much to add (yet) except that I have this exact issue.  I think I'm going to try to set up MythTV to use VLC player instead.

---

### Post by zapstrap on 2009-06-24
It does seem to work much better launching vlc for dvd content.  I hope I'm not setting myself up for trouble when integrating an IR remote.  Do I need to ensure all of the keys used in mythtv are the same on the vlc player?

---

### Post by bergersau on 2009-07-01
This is a known issue and it look like we will have to wait for MythTV .22 release to fix it.

[https://bugs.launchpad.net/mythbuntu/+bug/288816]("https://bugs.launchpad.net/mythbuntu/+bug/288816")

---

### Post by zapstrap on 2009-07-02
Thanks.  It just figures that Pirates is the disc I pulled off the shelf to test with.

---

