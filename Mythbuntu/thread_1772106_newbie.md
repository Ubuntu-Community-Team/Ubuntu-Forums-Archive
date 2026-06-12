---
title: "newbie"
date: 2011-05-31
forum: Mythbuntu
---

### Post by posfan12 on 2011-05-31
I just installed Mythbuntu on top of an existing Ubuntu 11.04 install. However, I don't understand how to start the program. I tried logging out and switching to a different session, but Mythbuntu did not appear in the list.

What do I need to do?

Thanks.

---

### Post by klc5555 on 2011-05-31
Well, first off read the instruction manual for mythtv itself at [http://www.mythtv.org/wiki/](http://www.mythtv.org/wiki/) which is up to date, and/or the mythbuntu installation manual at [http://mythbuntu.org/wiki](http://mythbuntu.org/wiki) which is old (i.e. 'buntu 9.10, myth about 0.22) but the general configuration is still valid.

Basically mythtv is not a program. It's at least two major programs (mythbackend and mythfrontend), and a whole array of lesser programs and tools that, when the whole mess is set up correctly,  fly in formation together.

mythbackend will take care of starting tuner cards, changing channels, executing recording schedules, talking to the MySQL database of program listings, and stuff like that.

mythfrontend is concerned with displaying recordings, displaying videos, user interaction with the database when scheduling recordings, and similar. 

The swarm of other mythtv utilities, plugins, programs and scripts are used or not as your need for them may arise.

A mythtv installation has to have at least one working and properly configured mythtv backend before anything else can happen. After reading the docs, you can get the backend configuration party started with a "sudo mythtv-setup"

Have fun.

---

### Post by BicyclerBoy on 2011-05-31
I think you need to install the mythbuntu-desktop package..
(That was how it worked with 8.04)
Then when you logout to the login/welcome screen, you will find a mythbuntu session available in the drop-down/up list.

Mythbuntu used Xfce desktop manger in the past...it may do now ?

---

### Post by posfan12 on 2011-05-31
Thanks, that worked! MythTV is now automatically starting on bootup.

However, there don't seem to be any menu options for logging off or shutting down the computer. Is this intentional? How would I go about adding them?

---

### Post by BicyclerBoy on 2011-05-31
@newbie
Did my advice work ? or the previous poster ?

When you exit mythfrontend does it not ask to shutdown (1 of 3 options) ?

You could have a look at mythwelcome package ..on 2nd thoughts this does not seem the right soln.
Else you have to add some gadgets to the window manager panels...
Add shutdown function to a remote key press or ?

FWIW (forgot where i was)
There are startup/shutdown scripts that work very well with backend/combined FE-BE.
They might work just fine on frontend..just don't know ..never tried.
But when the frontend is not running it can not do anything ..
Maybe you need to install the backend package just to manage the powerdown-when-idle.

---

### Post by posfan12 on 2011-06-01
Your comments in your previous post are what got me up and running. Thanks!

As for shutting my computer down, no there are not 3 options; there are only 2 - exit MythTV and cancel. I guess restoring the third option would be the thing to do if I knew how.

I can shut down from the Ubuntu desktop, though it is inconvenient.

---

### Post by BicyclerBoy on 2011-06-03
That's odd...it is possible the mythtv packages I use have different build options..

Both of my mythfrontend only boxes prompt the user with (3) options on exiting mythfrontend..one option is to exit & shutdown..

---

### Post by tgm4883 on 2011-06-04
You don't get the shutdown option if the backend is installed. Most users don't want to stop the backend, as it's used for recording. (might just be the master backend that does this). There is an option in the frontend settings that allow you to change this, but you'll have to poke around to find it.

---

### Post by posfan12 on 2011-06-11
What exactly is the backend needed for? If all I want to do is play local files, do I even need it? And, how do I uninstall it?

---

### Post by klc5555 on 2011-06-11
> **posfan12 said:**
> What exactly is the backend needed for? If all I want to do is play local files, do I even need it? And, how do I uninstall it?

The backend runs the tv tuner cards, handles scheduling of recordings and runs the database. Like I wrote way back in the original reply. Mythtv doesn't run without at least one backend connected. Mythtv is a PVR suite of applications : if you don't need a backend at all, because you just want to play local files, then you don't need mythtv. There are lots of simple file-player applications out there --any of them fit this need better than mythtv does.

---

### Post by tgm4883 on 2011-06-11
> **klc5555 said:**
> The backend runs the tv tuner cards, handles scheduling of recordings and runs the database. Like I wrote way back in the original reply. Mythtv doesn't run without at least one backend connected. Mythtv is a PVR suite of applications : if you don't need a backend at all, because you just want to play local files, then you don't need mythtv. There are lots of simple file-player applications out there --any of them fit this need better than mythtv does.

+1. I'd recommend XBMC if you don't need PVR functionality

---

### Post by ktmom on 2011-06-12
You could even use boxee and watch local or remote media.

---

