---
title: "VLC 0.8.6 VP62 and NSV support?  Help please!"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by mocha on 2007-02-19
Hey all.  I just upgraded to Edgy from Dapper.  The upgrade took a long time but worked without any trouble.  Kudos to the developers and docs updaters for that.

Anyway, I was wondering if there is any way to view the Shoutcast TV streams available in VLC 0.8.6?  Apparently I do not have the codec for VP62 and NSV streams.  On my Windoze 2000 box at work I am able to see these videos using VLC 0.8.6 for windows.  I'm not sure if that's because of the codec installed on that system or not.

Is there anyway to install the appropriate codecs in Edgy?  I searched the forums and Kubuntu forums and all I found were a few other posts asking the same question.  Thanks for any assistance you can provide.

---

### Post by Xantane on 2007-05-25
seems we will have to wait for version 0.9.0 the problem seems to reside in the Video codec VP61

---

### Post by dansen926 on 2007-08-27
Aw, man! That is NOT what I want to hear!

---

### Post by dansen926 on 2007-09-05
I wonder if I could run a portable version of VLC for Windows through Wine. Maybe that would do the trick.:confused:

---

### Post by kosak on 2007-11-15
Original text by **"Redleer"** from AZNV.TV forums ([http://aznv.tv/en/community/vtopic/10941/](http://aznv.tv/en/community/vtopic/10941/))

"http://www.videolan.org/vlc/download-ubuntu.html

Graphical way

Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).

Command line way

You need to check that you have a "universe" mirror in your /etc/apt/sources.list.

   % sudo apt-get update
   % sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc



with only that i got aznv.tv streams working on ubuntu yesterday Smilie: Grin (mayby were lucky haha not working well this time) "

then from **"erunesuto"**, AZNV.TV forums ([http://aznv.tv/en/community/vtopic/10941/](http://aznv.tv/en/community/vtopic/10941/))

"Well all it's about the repositories and multiverse and universe plugins.
TO STREAM M3U IN UBUNTU U HAVE TO DO THIS!!!!!
FIRST INSTALL VLC media player
HOW?
IN TO THE KONSOLE OR TERMINAL HAVE TO WRITE:
$sudo apt-get install vlc
Then put your password and is all, maybe 1 or 2 "Y"(Confirmation to do something)
Then install mplayer , the same way(U ask why?: Because we need some codecs, that's why, ok? )Smilie: Cool!
How?
$sudo apt-get install mplayer 
Then put your password and is all, maybe 1 or 2 "Y"(Confirmation to do something)
Next but no least important. install the some plugins to make able to play DVD and Streaming Indee is a bunch of PLUGINS that gonna help us too much with this and all the media some media works with totem other with mplayer BUT 4 ME WORKS ALLMOST ALL WITH VLC PLAYER(SUPER USEFULL)
install from the console this:
With the entire Medibuntu repository
If you have added the entire Medibuntu repository, you just need to install the package using APT:
sudo apt-get install libdvdcss2
With individual packages
If your wish to install just libdvdcss2, you can first download the individual package and then install the package.
i386:
wget -c [http://packages.medibuntu.org/pool/free/libd/](http://packages.medibuntu.org/pool/free/libd/) ...
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb

Playing Non-Native Media Formats
There are a few formats such as certain Windows formats, Real, and Apple Quicktime which do not have native codecs under Linux. To work around this issue, external binary codecs are used instead to play these formats. MPlayer and xine use such external codecs and these codecs are stored in the MPlayer website in their codecs directory located at [http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/).
Medibuntu distributes a package which contains these codecs. The codecs are under the non-free component of the repository. If you followed the directions above to exclude the non-free component, follow the steps again to add the Medibuntu repository to your system's list of APT repositories and skip the step to exclude the non-free component.
Below are the instructions for installing the packages using the command line. For other methods, please refer to Installing Software.
With the entire Medibuntu repository
If you have added the entire Medibuntu repository, install the package using APT.
For i386, the package is called w32codecs:
sudo apt-get install w32codecs

With individual packages
If you wish to install just the individual external codecs package, you can first download the individual package and then install the package.
For i386, the package is called w32codecs:
wget -c [http://packages.medibuntu.org/pool/non-free/w](http://packages.medibuntu.org/pool/non-free/w) ...
sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

IF U HAVE MAC OR 64bit SYSTEMS or maybe i386 info too GET SOLVE HERE;
[https://help.ubuntu.com/community/Medibuntu#h](https://help.ubuntu.com/community/Medibuntu#h) ...

WELL TRYING TO HELP TO THE LINUX COMUNITY AND ALSO [WWW.AZNV.TV](WWW.AZNV.TV) THE BETTER PLACE 4 MOVIES IN THE NET(MY HUMBLE OPINION) "

                                                                  --------------

From my behalf, I had all that done through automatix, although i missed vlc-plugin-esd, mozilla-plugin-vlc, so only audio played from my machine .... 

Finally, restart your machine. Then download the m3u file to your desktop. Then right click to Properties --> Open With --> VLC.

next time when you open it from Firefox it will open automatically!

---

