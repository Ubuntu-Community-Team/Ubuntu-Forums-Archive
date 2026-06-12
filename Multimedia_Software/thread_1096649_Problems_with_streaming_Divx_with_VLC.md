---
title: "Problems with streaming Divx with VLC"
date: 2009-03-15
forum: Multimedia Software
---

### Post by Squinty on 2009-03-15
Hi, i'm a new Ubuntu 8.10 user and think it's fantastic compared to windows.  Wish I had moved over years ago!  However I do have a problem playing Divx streams on Firefox.  I have installed VLC and the Mozilla plugin as described on other posts but no joy.

On a related note, I can't even select vlc as the default player for avi streams in the Firefox settings.

Any help would be appreciated as it's starting to get to me!

---

### Post by germanix on 2009-03-15
Hi Squinty,
I have had the same problem since I installed Ubuntu one year ago. I have posted this problem many times and I have had some help and suggestions but none seemded to work. I did find one site where I was able to stream divx movies but could not stop and start, nor could I make the screen go full size using the VLC player. On other sites I could not stream at all. Only this morning I followed the advice as given on this forum > The Ubuntu Forum Community > Main Support Categories > Multimedia & Video Comprehensive Multimedia & Video Howto. 
For your information I did the following:
IMPORTANT: If you haven't already, you need to enable the Medibuntu repository. The first command below is aimed at Ubuntu Family 8.10 Intrepid Ibex users, as are the manual instructions, so if you are using a different version of Ubuntu, you will have to slightly edit the command and sources. If you do have to edit the command, you can do so within the terminal by navigating to the word "intrepid" with the keyboard arrow keys, change it to whatever version you are running, then move the cursor back to the end of the line before executing the command.

Quick Method: Open the terminal (Applications > Accessories > Terminal or KMenu > System > Terminal Program (Konsole) in Kubuntu and Applications > System > Terminal in Xubuntu) and paste these wget commands into it:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

I then did the following:
32-Bit Ubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

I then followed this option:
OPTION 1, GECKO MEDIA PLAYER


Gecko Media Player is similar to mplayerplug-in, as it uses GNOME MPlayer to play virtually all formats, but works well without the need of adding any configuration options. Installation and setup is simple, just copy and paste the following commands into the terminal:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer

or if you're running Kubuntu, you might want the KDE front-end for MPlayer/Xine:

sudo apt-get install kmplayer gecko-mediaplayer

Restart your web browser and test the plug-in here. If you have problems viewing the trailers, please refer to the troubleshooting section.

Note: Please REBOOT if you are not carrying on with the rest of the howto, as you have made lot's of changes to your system and could have some strange problems until you start a fresh session. If you still have problems after rebooting, please read the troubleshooting section at the bottom.

After this I found that I could now (with the gecko player) stream divx on the site where it was previously also possible (movielab.tv) but now I could stop and start as well as go full screen size, but on all of the other sites (Kino.to) I still cannot stream divx, so it only solved the problem partly and not much help I am afraid.
I wish you better luck
Why it works on one site and not on others I am at a loss to explain

---

