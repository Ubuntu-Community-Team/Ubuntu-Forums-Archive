---
title: "Playing DVDs"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by insaneidiot on 2007-10-29
I can't seem to get DVD play back to work.  The DVD plays in Totem but the image is all scrambled.  How do I fix that and what video player would you recommend?

---

### Post by markusf21 on 2007-10-29
Totem can't handle DVD  menus try mplayer

---

### Post by insaneidiot on 2007-10-29
So I installed Mplayer but I get this error: FATAL: Could not initialize video filters (-vf) or video output (-vo).

---

### Post by sonicsmooth on 2007-10-29
If you load mplayer from the applications menu then it will give you a gui from which you can choose your video source.

Otherwise the -vo option tells it what video driver to use.  The vf option I think has to do with the codec or something.  I've never been sure about that and have been very frustrated with the *nix mentality when it comes to writing media applications -- way too many damn options!  I just want the freakin' thing to work.

---

### Post by insaneidiot on 2007-10-29
I do launch Mplayer from the applications menu but when I select DVD as the source, it gives me that error.

---

### Post by sonicsmooth on 2007-10-29
Hm... this is where I get stuck with mplayer.  In the preferences are options for video driver (-vo) and filter (-vf).  I've never figured out which one to pick.  Sorry I can't be more help.

michael

---

### Post by DeadToad on 2007-10-29
insane,
try this.
DeadToad

vlc VideoLAN download for Linux Ubuntu Gutsy Gibbon v7.10

ADDITIONAL DVD PLAYBACK CODEC INSTALLATION:
After doing a fresh install of any one of the Ubuntu-based Linux distributions, some packages needed for DVD playback are not installed by default because of Ubuntu's commitment to completely free multimedia formats. This section covers what packages are needed and how to acquire and install them onto your system.

After doing a fresh install of Feisty, be it Ubuntu or Kubuntu, there are two packages not installed by default that need to be installed for DVD playback to work. There's a third package (libdvdcss2) needed to play encrypted DVDs.
They are:
    * libdvdread3
    * libxine1-ffmpeg (Also requires libmad0, therefore libmad0 will be installed automatically along with this package)
    * libdvdcss2 (Needed to play encrypted DVDs)

libdvdread3 and libxine1-ffmpeg are in the Ubuntu repository.

libdvdcss2 is not part of the Ubuntu repository because of Ubuntu's commitment to completely free multimedia formats.
===

VLC media player for Ubuntu Linux:
Ubuntu Gutsy Gibbon 7.10
Ubuntu Feisty Fawn 7.04
Ubuntu Edgy Eft 6.10

Installation instructions for libdvdcss2 and w32codecs in Ubuntu, to play DVDs in MPlayer and VLC:

To add libdvdcss2 and win32codecs to your Ubuntu installation, you have to add the Medibuntu package repository to your /etc/apt/sources.list file.

To do this, you have to:
1. Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
gksudo gedit /etc/apt/sources.list to open it in the GUI text editor
or
sudo vim /etc/apt/sources.list to open it in the Vim command line text editor

2. Add the following lines to add the Medibuntu repository to the file:

## Medibuntu - Ubuntu 7.10 â€œgutsy gibbonâ€
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free

If you are running Feisty or some other release, other than gutsy, replace the word â€œgutsyâ€ in the three lines above with the name of the release you are using.

3. Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

4. Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:
In a terminal execute the following command:
sudo apt-get update

5. Now you can install libdvdcss2 and w32codecs using the following command:
sudo apt-get install libdvdcss2 w32codecs

NOTE: If you receive any error messages during the above Steps, ignore them.
Close terminal window.

6. To install/reinstall VLC Media Player:
Open Synaptic (System -> Administration -> Synaptic Package Manager).
Type your password.
Click Settings -> Repositories.
Under "Ubuntu Software" check the first four items, making sure you have the "universe" repository checked.
Do NOT check "source code".
Under "Third-Party Software" check all items.
Under "Updated/Ubuntu Updates" check the first two items.
Click "Close", twice if necessary.
Now back at the Synaptic Package Manager main window:
Click "Search".
Type "vlc".
Click "Search" button.
"vlc" will be shown in the left window.  left-click it once to highlight it.
In the right window, click on these additional files: vlc-plugin-esd and mozilla-plugin-vlc, then click "Mark for installation" for each file.
(libdvdcss2 which will be installed later, as it is NOT in a repository).
Click "Apply".
Click "Apply" again, if necessary to begin download.
After "Changes applied", click "Close".
Close "Synaptic Package Manager" window.

7. Now, you just need to REINSTALL livdvdcss2 to get VLC and Totem MPlayer to play DVDs:
"libdvdcss2_1.2.9-1_i386.deb" is here: 
[http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html](http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html)
(This is the version that works).
If not found, google "libdvdcss2_1.2.9-1_i386.deb" for an active link.

libdvdcss2-dev_1.2.9-1_i386.deb is here: [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb)
or here: [http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/](http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/)
or here: [http://www.free-dvd.org.lu/libdvdcss/debian/](http://www.free-dvd.org.lu/libdvdcss/debian/)
If not found, google "libdvdcss2-dev_1.2.9-1_i386.deb" for an active link.
(This version does not work).

Just click the link, then "open" it with the default selection (do NOT save it).
Then click "Install Package", and let it finish.
After that, VLC Media Player and Totem MPlayer will play your DVDs.

8. Reboot computer, then run Update Manager again for additional updates (libdvdread3):
System/Administration/Update Manager.

9. You may need these two additional CODECS to play DVDs:
libdvdread3 and libxine1-ffmpeg (in the Ubuntu repository).
To install them through the command line, type the following:
sudo apt-get install libdvdread3 libxine1-ffmpeg
===

---

### Post by insaneidiot on 2007-10-29
I did the VLC install and it works!  For VLC only though.  It works fine in VLC but Totem still says that i need to download plugins.  Oh well.  At least VLC works.  Thanks for the help!  :)

---

### Post by DeadToad on 2007-10-30
insane,
One one of my compooters, VLC worked after my instructions, But, Totem MPlayer would NOT work, UNTIL I performed Steps 8 and 9.

First, try Step 8.
See if Totem MPlayer plays DVDs.

If not, try Step 9 also.
Good luck.
DeadToad \\:D/

---

### Post by insaneidiot on 2007-10-30
I did all 9 steps and Totem still doesn't work.  Oh well.  VLC's good enough for now.

Also, I was wondering how to get a video player to disable the screen saver and screen dimming when they're playing.  Any clues?

---

### Post by hobbes_ba on 2007-10-31
Well, I am using a X86_64 version of Ubuntu Gutsy.

Using Totem-xine is not an option for me, because it screws mp3 p&#314;ayback on Totem-Mozilla plugin and besides that Totem-gstreamer has better subtitles.

So, my DVD player of "choice"  is VLC, but I am having problems with it.

Here is my problem.

VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Heroes Disc 1
libdvdnav: DVD Serial Number: 4722B36B00002710
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/user/.dvdnav/Heroes Disc 1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000172
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001881f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001993f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0019b81d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0019b84a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0019ed4e
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'en' not found, using 'pt' instead
libdvdnav: Menu Languages available: pt 
libdvdnav: Language 'en' not found, using 'pt' instead
libdvdnav: Menu Languages available: pt 
libdvdnav: Language 'en' not found, using 'pt' instead
libdvdnav: Menu Languages available: pt 
libdvdnav: Language 'en' not found, using 'pt' instead
libdvdnav: Menu Languages available: pt 
libdvdnav: Language 'en' not found, using 'pt' instead
libdvdnav: Menu Languages available: pt 

*** libdvdread: CHECK_VALUE failed in ifo_read.c:663 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:664 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:665 ***
*** for pgc->cell_position_offset == 0 ***

libdvdnav: ifoRead_PGCI_UT failed - CRASHING!!!
vlc: vm.c:210: ifoOpenNewVTSI: Afirmação `0' falhou.
Cancelado (core dumped)


This is an ALL REGION DVD and VLC fails to play the disc on DVD MENU mode.

It can be played on DVD Single mode, by the way. But certainly is not an valid option.

Can anyone help me?

---

