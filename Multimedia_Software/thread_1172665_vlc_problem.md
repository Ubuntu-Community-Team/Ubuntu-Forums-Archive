---
title: "vlc problem"
date: 2009-05-28
forum: Multimedia Software
---

### Post by tommah04 on 2009-05-28
hey all

tried playing a dvd through vlc just now and I got this error in the terminal.....let me know if there's anything I can do about it.... thanks!

libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: SHANGHAI_KNIGHTS
libdvdnav: DVD Serial Number: 2eb48b07
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/tweak/.dvdnav/SHANGHAI_KNIGHTS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[00000408] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_01_0.IFO).
[00000408] dvdread demux error: fatal error in vts ifo
[00000408] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000411] main access error: no access module matched "dvd"
[00000407] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"
^C[00000402] signals interface error: Caught Interrupt signal, exiting...

---

### Post by m_duck on 2009-05-28
It looks like you need to install the libdvdcss2 package for playing encrypted DVDs. Take a look at [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats/") in Ubuntu, [DVD playback]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") and the [Medibuntu repo]("http://www.medibuntu.org/").

You can get libdvdcss either by adding the medibuntu repo (what I generally do) and installing the **libdvdcss2** package, or by using the script mentioned by the instructions in the DVD link above (I have never tried this).

---

### Post by tommah04 on 2009-05-28
sweet, worked out great.... I figured it was something stupid and simple like a missing codec or something....

but here's another problem .... I have no sound....  I check a few forums and I've figured out that ubuntu recognizes the sound card and that the volume isn't mute or turned down to 0....any other ideas?

---

### Post by m_duck on 2009-05-28
Does the sound work in any other app's apart from VLC? That would narrow it down to a VLC problem rather than a system one.

---

### Post by tommah04 on 2009-05-28
no, no sound whatsoever.... not even that default start up sound

---

### Post by m_duck on 2009-05-28
Strange... Are you using a laptop or desktop? I'm probably useless if it's a laptop. If it is a desktop, how is it connected to speakers? If you are using an optical (S/P DIF) cable, you will need to check the IEC958 box to enable it.

Also, try running "alsamixer" in a terminal and ensure all of the important ones (Master, Front, PCM...) are unmuted and volumes are up. Left and right arrow keys to select the different channels, **m** to toggle mute, up and down arrow keys to increase/decrease volume.

---

### Post by tommah04 on 2009-05-28
bummer... its a laptop..... well actually a friend's laptop, heh, I talked him into getting ubuntu and now I feel bad cause he can't watch any movies, ha ha

---

