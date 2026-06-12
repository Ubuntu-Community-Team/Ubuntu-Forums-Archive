---
title: "playing dvd problems"
date: 2009-11-21
forum: Multimedia Software
---

### Post by w1ll1am on 2009-11-21
here is my problem I want to play dvd's in ubuntu 9.10 and I can not get it to work. i have tried VLC and movie player. I have gone to [https://help.ubuntu.com/community/RestrictedFormats ]("https://help.ubuntu.com/community/RestrictedFormats")and installed everything it has told me. My region code is set to 1 and I am in the U.S. so I am assuming that is right. VLC says   p, li { white-space: pre-wrap; }  [COLOR=Red][COLOR=#FF0000][COLOR=Black]"[/COLOR]Playback failure:[/COLOR][/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc." I am kind of new to computers and especially ubuntu well any distro so please if you can explain it as simple as possible. 
[/COLOR]
[COLOR=#000000]       I ran cvlc -v dvd:// to get and errors so you can see them below but i do not know how to interpret it so if you can help please let me know. [/COLOR]




william@william-desktop:~$ cvlc -v dvd://
VLC media player 1.0.2 Goldeneye
[0x96b2a08] main demux warning: no access_demux module matching "file" could be loaded
[0x96b8ef8] main interface error: no interface module matched "globalhotkeys,none"
[0x96b8ef8] main interface error: no suitable interface module
[0x9618140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x96b8f60] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 44409076 (GEAR):
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/william/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
*** Zero check failed in ifo_read.c:841
    for pgc->zero_1 = 0x00ea

*** libdvdread: CHECK_VALUE failed in ifo_read.c:860 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:861 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:862 ***
*** for pgc->cell_position_offset != 0 ***

*** Zero check failed in ifo_read.c:854
    for pgc->still_time = 0x01
*** Zero check failed in ifo_read.c:854
    for pgc->still_time = 0x80
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x7f

*** libdvdread: CHECK_VALUE failed in ifo_read.c:856 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:857 ***
*** for pgc->cell_playback_offset == 0 ***

*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0xea

*** libdvdread: CHECK_VALUE failed in ifo_read.c:856 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:842 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:860 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:861 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:862 ***
*** for pgc->cell_position_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
[0xb7303a10] dvdnav demux error: cannot set title (can't decrypt DVD?)
[0xb7303a10] main demux error: Playback failure
[0xb7303a10] main demux error: VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
*** Zero check failed in ifo_read.c:854
    for pgc->still_time = 0x75

*** libdvdread: CHECK_VALUE failed in ifo_read.c:856 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:857 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:858 ***
*** for pgc->cell_position_offset == 0 ***

*** Zero check failed in ifo_read.c:854
    for pgc->still_time = 0x80
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x80

*** libdvdread: CHECK_VALUE failed in ifo_read.c:858 ***
*** for pgc->cell_position_offset == 0 ***

*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0xea

*** libdvdread: CHECK_VALUE failed in ifo_read.c:856 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:857 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:858 ***
*** for pgc->cell_position_offset == 0 ***

*** Zero check failed in ifo_read.c:841
    for pgc->zero_1 = 0x000b
libdvdread: Unable to read VTS_TMAPT.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_01_0.IFO).
[0xb7303a10] dvdread demux error: fatal error in vts ifo
[0xb7303a10] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[0xb7303a10] main demux warning: no access_demux module matching "dvd" could be loaded
[0x96cfe90] main access error: no access module matched "dvd"
[0xb7300ec0] main input error: open of `dvd://' failed: no access module matched "dvd"
[0xb7300ec0] main input error: Your input can't be opened
[0xb7300ec0] main input error: VLC is unable to open the MRL 'dvd://'. Check the log for details.

---

### Post by cariboo on 2009-11-21
You need to install libdvdcss2 in order to decrypt DVDs. Libdvdcss2 is available in the mediabuntu repositories.

To enable the Medibuntu repositories go [here]("http://https://help.ubuntu.com/community/Medibuntu")

---

### Post by gordong11 on 2009-11-21
IF you are new please goto the link below. I would even suggest backing up your goodies and re-install following this exact step by step guide.

It's the best thing I have ever seen, and I still use it whenever I do a fresh install.

[http://www.futuredesktop.org/](http://www.futuredesktop.org/)

Take note of the info in step 7a.

---

### Post by gordong11 on 2009-11-21
Make sure you have libdvdcss2 installed.

Check VLC preferences audio and make sure all looks ok.

---

### Post by w1ll1am on 2009-11-21
> **cariboo907 said:**
> You need to install libdvdcss2 in order to decrypt DVDs. Libdvdcss2 is available in the mediabuntu repositories.

To enable the Medibuntu repositories go [here]("http://https://help.ubuntu.com/community/Medibuntu")

Thanks I can play all my dvd's now but they are kind of in black in white I am not sure why can you help.

---

### Post by gordong11 on 2009-11-21
sudo wget [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get -y --force-yes install medibuntu-keyring

sudo apt-get remove --purge flashplugin-* nspluginwrapper

sudo apt-get remove -y icedtea6-plugin openjdk-6-jre openjdk-6-jre-lib gcj

sudo apt-get install --reinstall sun-java6-jre ubuntu-restricted-extras non-free-codecs libdvdcss2 sun-java6-fonts

sudo apt-get install --reinstall flashplugin-nonfree

pkill firefox

---

### Post by w1ll1am on 2009-11-21
Thanks but that did not work? it is still black and white well it is not black and white it has some color but not like it should. can you think of anything else thanks so much for your help

---

### Post by w1ll1am on 2009-11-22
i think i have it fixed i changed the hue in totem and put it all the way to the left and it looks perfect so i guess it is fixed. thank you so much for your help so far i have had problems with linux but they are all not to hard to fix unlike problems in windows. I am liking ubuntu and everyone who has helped me so far has reply very quickly thanks so much!

---

