---
title: "Launchig XBMC from Mythtv main menu"
date: 2010-07-11
forum: Mythbuntu
---

### Post by rulet on 2010-07-11
To launch XBMC from MythTV main menu I do this:

sudo gedit /usr/share/mythtv/themes/defaultmenu/mainmenu.xml

 and putting in a file f.e. this:


    <button>
        <type>MENU_UTILITIES_SETUP</type>
        <text lang="RU">&#1052;&#1045;&#1044;&#1048;&#1040;&#1058;&#1045;&#1050;&#1040;</text>
        <action>EXEC xbmc</action>
    </button>

And the button apears in mythtv main menu, but when I want to close XBMC the system freezes completly, I know that's because of pulseaudio, but how to resolve it without deleting pulseaudio?

---

### Post by brianafischer on 2010-07-12
I am also struggling with the same (and other) issues running XBMC and Myth concurrently.  I have not had time to solve this issue on my system.

I experience complete lockup upon attempting to play a video in XBMC.  How did you get video working?  I believe this may be related to audio settings in both Myth and XBMC.

There are a lot of other threads with work-arounds only or no solution:

[LIST]
[*][Run XBMC without PulseAudio]("http://www.gossamer-threads.com/lists/mythtv/users/410069#410069")
[*][Same issue on mythtv-users]("http://www.gossamer-threads.com/lists/mythtv/users/421488")
[*][Lockup on video playing on XBMC forums]("http://forum.xbmc.org/showthread.php?p=565577")
[/LIST]

The only work-arounds I know of:

1. Kill MythFrontend and start XBMC via a script
2. Create a custom script that will enable/disable PulseAudio when launching XBMC


Please post if you find a solution!

---

### Post by brianafischer on 2010-07-13
I had time last night to remove PulseAudio and it seems to change the lockups to long delays.  Sometimes it takes 1-2 minutes for XBMC to exit, but it no longer locks up the desktop.

I removed pulseaudio in attempt to fix XBMC lockup issues using the thread from [here]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9297829&postcount=146")

Notes on the thread linked above:
[LIST]
[*]Did not install esound.  A lot of others did not think it was required and I don't think Myth or XBMC use it.
[*]The line with sed did not work either (permission denied).  I just continued with the steps below and it seemed to work.  I am not sure what that line was supposed to do...
[*]I didn't have to change any sound settings after the reboot which was unexpected.  I was preparing to spend hours customizing the alsa files.
[/LIST]

```

sudo cp /usr/share/alsa/alsa.conf /usr/share/alsa/alsa.conf.bak
sudo apt-add-repository ppa:dtl131/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install libesd-alsa0 alsa-base alsa-tools alsa-utils alsa-oss linux-sound-base python-alsaaudio gnome-media libsdl1.2debian-alsa
sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol

```

---

