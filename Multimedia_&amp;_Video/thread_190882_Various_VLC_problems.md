---
title: "Various VLC problems"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by Soup4Brains on 2006-06-06
I used synaptic to get VLC, and while it seems to handle audio files perfectly, video scarcely works at all. Some video files play with only sound, others play with no sound, and when trying to view embedded video in Firefox I ALWAYS get a (no picture) message.

I like Ubuntu infinitely better than Windows XP, but when webpages become near-unviewable because of this sort of thing it discourages me from using it.

Any help would be greatly appreciated.

---

### Post by terrukallan on 2006-06-06
When playing embedded video, the VLC plugin always displays the "no picture" message until enough of the file has downloaded to actually start playing.  This is a poor design choice, but it *does* work (for me at least).  Wait a bit and see if your file starts playing after a few minutes.

There are, unfortunately many other problems with VLC in Ubuntu...

---

### Post by Soup4Brains on 2006-06-07
I've switched to mplayer but now I can't get WMV's to play properly and I don't know how to get it to support wmv3. Rawr. :mad:

---

### Post by LinkofHyrule on 2007-10-30
My gamma settings are all messed up in VLC. I try to adjust them, but nothing changes. When I'm watching animé, I can't even make out the faces.

---

### Post by DeadToad on 2007-10-30
You may need to install the codec libraries for VLC and Totem MPlayer to play videos and DVDs.
Hope this helps.
DeadToad

----
vlc VideoLAN Media Player download for Linux Ubuntu Gutsy Gibbon v7.10

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
---

Installation instructions for libdvdcss2 and w32codecs in Ubuntu, to play DVDs in MPlayer and VLC:

To add libdvdcss2 and win32codecs to your Ubuntu installation, you have to add the Medibuntu package repository to your /etc/apt/sources.list file.

To do this, you have to:
1. Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
gksudo gedit /etc/apt/sources.list to open it in the GUI text editor
or
sudo vim /etc/apt/sources.list to open it in the Vim command line text editor

2. Add the following lines to add the Medibuntu repository to the file:

## Medibuntu - Ubuntu 7.10 gutsy gibbon
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free

If you are running Feisty or some other release, other than gutsy, replace the word "gutsy gibbon"in the first line with the name of the release you are using.  In the third and fourth lines above replace "gutsy" with the name of the release you are using.

3. Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

4. Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:
In a terminal execute the following command:
sudo apt-get update

5. Now you can install libdvdcss2 and w32codecs using the following command:
sudo apt-get install libdvdcss2 w32codecs

NOTE: If you receive any error messages using the above Steps, ignore them.
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

