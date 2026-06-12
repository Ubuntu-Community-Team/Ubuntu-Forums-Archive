---
title: "lirc remote, and dvd playback problems MythFrontend 0.27"
date: 2014-01-01
forum: Mythbuntu
---

### Post by johalareewi on 2014-01-01
I am doing a standalone tivo replacement system (front and backend on same PC).  I have installed the latest MythBuntu and used MCC to move to MythTV 0.27.  The mobo is an Asus M5A78L-MUSB3 and I am using a Hauppauge Nova-TD500 freeview card.  Everything is working fine except the remote, and DVD playback.

The remote is not working 100% because when lirc is setup by MCC for the Nova-T500 remote, it configures the remote at /dev/lirc0.
But the remote is not there. In the current version it is at /dev/input/event13.  I can manually craft the hardware.conf and lircd.conf and get the remote to work but, whenever I run MCC, it zaps the lirc setup.  How do I stop MCC doing this?

DVD playback doesn't work.  The hardware would appear to be fine because it works when running windows7.  With MythBuntu, neither MythTV or VLC Player can play a DVD.  MythBuntu can read the DVD files but it is not possible to play the VOBs.  I have tried to install the propriatory codecs in MCC but this seems to fail even though there are no error messages.

frontend log...

Jan  1 13:33:01 MYTH mythfrontend.real: mythfrontend[2752]: I CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to change from None to WatchingDVD
Jan  1 13:33:01 MYTH mythfrontend.real: mythfrontend[2752]: I CoreContext DVD/dvdringbuffer.cpp:458 (OpenFile) DVDRB: Opened DVD device at //dev/dvd
Jan  1 13:33:03 MYTH mythfrontend.real: mythfrontend[2752]: E CoreContext DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:04 MYTH mythfrontend.real: mythfrontend[2752]: I CoreContext DVD/dvdringbuffer.cpp:509 (StartFromBeginning) DVDRB: Resetting DVD device.
Jan  1 13:33:04 MYTH mythfrontend.real: mythfrontend[2752]: I CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from None to WatchingDVD
Jan  1 13:33:04 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:576 (GetChapterTimes) DVDRB: Failed to retrieve chapter data
Jan  1 13:33:06 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:06 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:06 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:06 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:06 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:07 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:07 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:08 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:08 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:08 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:08 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:09 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:09 MYTH mythfrontend.real: mythfrontend[2752]: I CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to change from WatchingDVD to None
Jan  1 13:33:09 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:09 MYTH mythfrontend.real: mythfrontend[2752]: E Decoder DVD/dvdringbuffer.cpp:710 (safe_read) DVDRB: Failed to read block: Error reading from DVD.
Jan  1 13:33:09 MYTH mythfrontend.real: mythfrontend[2752]: I CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from WatchingDVD to None

---

### Post by johalareewi on 2014-01-01
update:

Following the advice in this thread, 
[http://ubuntuforums.org/showthread.php?t=2131140](http://ubuntuforums.org/showthread.php?t=2131140)

I got this VLC output


libdvdnav: Using dvdnav version 4.2.0
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: FUTURAMA_COMPLETE_SEASON_6_D3
libdvdnav: DVD Serial Number: 3F554E04
libdvdnav: DVD Title (Alternative): FUTURAMA_COMPLETE_SEASON_6_D3
libdvdnav: Unable to find map file '/home/alan/.dvdnav/FUTURAMA_COMPLETE_SEASON_6_D3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
[0x7f310c000b78] main input error: ES_OUT_RESET_PCR called
[0x7f310c000b78] main input error: ES_OUT_RESET_PCR called
[0x7f310c000b78] main input error: ES_OUT_RESET_PCR called
[0x7f310c000b78] main input error: ES_OUT_RESET_PCR called
libdvdnav: demux error! 00 00 00 (should be 0x000001) 

Looks like MCC is not installing the extra stuff. :(

---

### Post by johalareewi on 2014-01-01
Update:
Tried manual install of libdvdcss

alan@MYTH:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2014-01-01 16:09:23--  [http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
Dynamic fetch failed; Falling back to static fetch
--2014-01-01 16:09:29--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'

---

### Post by johalareewi on 2014-01-01
[SIZE=2][FONT=arial]Sorted:
System > Ubuntu Software Center
Edit > Software Sources
Other Software
Add
[COLOR=#4D4D4D]deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /[/COLOR]
Add
[COLOR=#4D4D4D]deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
[/COLOR]Make sure both are ticked

Now MCC Proprietary Codecs install should work.

References:
[http://ubuntuforums.org/showthread.php?t=1979010&page=3](http://ubuntuforums.org/showthread.php?t=1979010&page=3)
[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/Repositories/Ubuntu#what](https://help.ubuntu.com/community/Repositories/Ubuntu#what)



[/FONT][/SIZE]

---

