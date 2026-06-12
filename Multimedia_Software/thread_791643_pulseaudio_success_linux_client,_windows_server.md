---
title: "pulseaudio success: linux client, windows server"
date: 2008-05-12
forum: Multimedia Software
---

### Post by kswenson on 2008-05-12
I just finished setting up pulseaudio with a windows machine attached to my sterio and a linux client on my laptop...
  here are the steps that I used:

Server side (windows):
1) download the binary from [http://www.cendio.com/pulseaudio](http://www.cendio.com/pulseaudio)
2) unzip it and put it in a permanent place.
3) follow directions at [http://mpd.wikia.com/wiki/PulseAudio#On_Windows](http://mpd.wikia.com/wiki/PulseAudio#On_Windows)
4) write down the IP of the windows machine on the LAN and save it for later.


Client side (linux):
1) start with a normal install of ubuntu 8.04

2) do steps from [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio).  only do the steps from the "Installing PulseAudio" and "Adding Users to the PulseAudio groups" sections.

3) now open "Applications" -> "Sound & Video" -> "PulseAudio Device Chooser".
   `-> this should put a little icon on your gnome panel

4) click the icon and choose "Default Server" -> "Other...".

5) enter the IP of your windows machine in the box that comes up.

Now when you click the icon and choose "Manager" it should show you information from you windows machine.  If it doesn't, click "Disconnect" and then "Connect".

You may have to go to "System" -> "Sound" and fix some the preferences to make them "PusleAudio Sound Server" for those types of media you want to play over the server.
However, for me a good test was to use the terminal version of mplayer which sent the music I was playing to the other machine immediately.

---

