---
title: "libdvdcss2 &amp; w32codecs but still dvd playback problems"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by stepheny on 2007-11-04
I recently upgraded to Fiesty Fawn and have a problem playing DVD's that played without problems in Dapper. Libdvdcss2 is installed and also the w32codecs. 
Most of my DVD's play but some do not. All are legal originals bought in Europe. Some, such as "The Old Grey Whistle Test" play the music and intro chapters but will not play the interview chapters.When I attempt to play these chapters I get a message that an error has occured and I am asked if  I am  trying to play an encoded DVD without libdvdcss2. Some DVD's will not play at all, I get the same message I mentioned above.
I have tried everything I can think of to fix this, even installing and using Easyubuntu to be sure I am not missing anything.
Any suggestions would be very welcome.

---

### Post by damotor on 2007-11-04
Try using vlc, I think it comes with all the codecs so there should be no problem

---

### Post by stepheny on 2007-11-04
Thanks for the reply but:
a) I would still like to know how to play a dvd with xine, totem etc.
b) could you be more specific as to how I can play a dvd using vic. The dvd player doesn't have an ip address.

---

### Post by Gremlinzzz on 2007-11-04
This worked for me using gutsy but its for feisty.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

---

### Post by stepheny on 2007-11-04
I have done all that but the problem remains. Thanks anyway.

---

### Post by DeadToad on 2007-11-04
stepheny,
These steps will get DVD playback working in Totem MPlayer and VLC Media Player.
You MUST reinstall w32codecs and libdvdcss2, even if it is already installed.
Good luck,
DeadToad

Installation instructions for libdvdcss2 and w32codecs in Ubuntu, to play DVDs in Totem MPlayer and VLC:

To add libdvdcss2 and win32codecs to your Ubuntu installation, you have to add the Medibuntu package repository to your /etc/apt/sources.list file.

To do this, you have to:
1. Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
gksudo gedit /etc/apt/sources.list to open it in the GUI text editor
or
sudo vim /etc/apt/sources.list to open it in the Vim command line text editor

2. Add the following lines to add the Medibuntu repository to the file:

## Medibuntu - Ubuntu 7.10 “gutsy gibbon”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free

If you are running Feisty or some other release, other than gutsy, replace the words “gutsy gibbon” in the first line with the name of the release you are using, and in the last two lines above, replace "gutsy" with the name of the release you are using.

3. Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

4. Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:
In a terminal execute the following command:
sudo apt-get update

5. Now you can install libdvdcss2 and w32codecs using the following command:
sudo apt-get install libdvdcss2 w32codecs

NOTE: Ignore any error messages during any above Step.
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
Click "Apply", twice if necessary to begin download.
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
===

ADDITIONAL DVD PLAYBACK CODEC INSTALLATION:
After doing a fresh install of any one of the Ubuntu-based Linux distributions, some packages needed for DVD playback are not installed by default because of Ubuntu's commitment to completely free multimedia formats. This section covers what packages are needed and how to acquire and install them onto your system.

After doing a fresh install of Feisty, be it Ubuntu or Kubuntu, there are two packages not installed by default that need to be installed for DVD playback to work. There's a third package (libdvdcss2) needed to play encrypted DVDs.
They are:
    * libdvdread3
    * libxine1-ffmpeg (Also requires libmad0, therefore libmad0 will be installed automatically along with this package)
    * libdvdcss2 (Needed to play encrypted DVDs)

libdvdread3 and libxine1-ffmpeg are in the Ubuntu repository. To install them through the command line, type the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg

libdvdcss2 is not part of the Ubuntu repository because of Ubuntu's commitment to completely free multimedia formats.
===

---

### Post by stepheny on 2007-11-04
Thanks for the advice, but..... 

I followed it but still no joy. However in totem I no longer get the warning but the picture and sound are crypted in the interview chapters. In VLC the chapters that work in totem are very jerky.

By the way, the links ie  "deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free" no longer work, I enabled  the medibuntu repository by following the instructions at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by krystalsavage on 2007-11-04
I'm running Fiesty again after dumping Windows Vista. Unfortunately, i've added the medibuntu information to my /etc/apt/sources.list file and when i try doing this key thing:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

i get an error "gpg: no valid OpenPGP data found". I've been trying this for the past 3 days with no luck. Is medibuntu.sos-sts.com down for some reason?

Krystal

---

