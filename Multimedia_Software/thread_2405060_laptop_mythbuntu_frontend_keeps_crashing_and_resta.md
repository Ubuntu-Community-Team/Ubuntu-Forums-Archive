---
title: "laptop mythbuntu frontend keeps crashing and restarting"
date: 2018-10-31
forum: Multimedia Software
---

### Post by linuxhippy on 2018-10-31
A couple weeks ago I did a fresh install of the 64 bit version of mythbuntu 16.04.5 on an old Samsung R540 laptop.  I just installed the frontend software on this laptop since my backend/frontend setup is on a networked tower.  The install seemed to go just fine but on restart the frontend of mythtv kept crashing with exit code 130 and restarting.  I was able to able to disable it autostarting and just use the short cut to start the program, but I'm not sure if there is a log file that would explain why it keeps crashing.  Maybe it's a video problem as it probably doesn't have a video card.

Any help to point me in the right direction would be appreciated.

Thanks!!

Marty

---

### Post by linuxhippy on 2018-11-01
I ran mythfrontend from the terminal and got some info that is helpful.  The problem is a connection problem to the backend and not a video problem.  This is one of the errors I see:

> Connection to master server timed out.  Either the server is down or the master server settings in mythtv-settings does not contain the proper IP address


I think everything on the backend is setup correctly.  I found this on the mythtv wiki for a frontend:

> Start by launching the frontend, either using the launch icon in the desktop menu or by running mythfrontend. This can be run on the same system as the backend or on another machine that has a network connection to the backend (remote frontend). As long as the backend is running the frontend will find it.

If you see a screen which asks for your Country and Language, then the frontend has failed to find the backend. This could be because your backend is not running, or the backend is on a separate network from the frontend.

This screen with the Country and Language is what I see but making the needed input makes it crash and restart.

---

### Post by linuxhippy on 2018-11-02
Here's some screenshots from the backend that may help u see my settings:

[ATTACH=CONFIG]281511[/ATTACH]

[ATTACH=CONFIG]281512[/ATTACH]

This is what I see in my frontend terminal:

2018-11-02 07:32:59.603866 E  MythSocket(7f3538004230:-1): Failed to connect to (127.0.0.1:6543) Connection refused
2018-11-02 07:32:59.604080 E  Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

Handling Segmentation fault


Why is it looking at my local frontend IP address rather than on the network?

---

### Post by linuxhippy on 2018-11-02
got it working on the frontend.  MythTV does work on laptops without special video cards.  The settings get saved in your home directory under 2 directories being .mythtv and .mythbuntu.  Rename or delete the directories once everything on the backend is set right and then run mythfrontend on the frontend computer and these directories get recreated.  Here's my directory listing before getting mythfrontend working:

[ATTACH=CONFIG]281513[/ATTACH]

---

