---
title: "MythTV won't install. Can't get past &quot;Launch MythTV Setup&quot;"
date: 2008-04-07
forum: Mythbuntu
---

### Post by Mugsy323 on 2008-04-07
This is incredibly annoying for someone that simply wanted to see his ATI "HDTV Wonder" card working in Ubuntu 7.10.

I tried installing MythTV the other day, but didn't know what I was doing (I'm a PC tech so I usually only RTFM after I get stuck) and ended up uninstalling everything when it started asking me for "Server" info I didn't have.

I didn't know about selecting "backend/frontend" roles and used the defaults.

After some online RTFM reading, I decided to give MythTV a second try. But uninstalling must have left some information behind because the reinstall didn't proceed the same way (different screens).

After reinstalling all of the packages and rebooting through the nice "mythbuntu" login screen, I try launching "Mythbuntu Control Centre" from the System | Admin" menu.

"System Role" is set to "Primary Backend", "Frontend" and "Ubuntu Desktop".

[COLOR="Red"]Next step, "MythTV Configuration". All boxes (correctly) grayed out. Clicking the "Launch MythTV Setup" produces a dialog stating "Mythbackend must be closed before continuing". I click OK and a terminal window opens and I get three lines, the last stating "New DB connection, total: 1".

Closing that window gives a second dialog asking, "Would you like to run mythfilldatabase?" Clicking OK gives me another window (this time using the Linux CLI instead of Terminal) with the same "New DB connection, total: 1" response on the last line (of two).

Closing that Window simply returns me to the "Control Centre", grayed boxes and Launch button, right where I left off, no further along than when I started. I've tried clicking "Cancel" on the dialogs in every combination, but it always comes out the same: I can't get past the Launch button screen.[/COLOR]

I've tried rebooting and logging off, but I can't get past this step. I've tried changing Roles and enabling MySQL, but nothing I've tried has gotten me any further along.

[COLOR="Green"]I did discover that if I launch "MythTV Backend Setup" from the System menu, it does the exact same thing, with the two dialogs and Terminal & CLI windows. So apparently, clicking the "Launch MythTV Setup" from the Control Centre is simply running the same "Backend setup", and when done, simpy returns to the Control Centre app.[/COLOR]

This is irritating. Why on Earth should something like this be so astoundingly complicated simply to get an HDTV player/recorder?

---

### Post by warp99 on 2008-04-07
MythTV is a complete PVR setup that is usually setup as a backend/frontend on a machine specific for that purpose. Frontends can be setup on a regular desktop and content is can be streamed from a backend to the frontend over the network. I have a media server with a MythTV backend/frontend plus regular desktops with just frontends all around the house.

If you just want to just see HDTV content you can use another program. such as tvtime, kwintv, or motv. If you want a complete PVR solution then install [Mythbuntu]("http://www.mythbuntu.org/") which is based on Ubuntu and MythTV. Much easier then trying to install Ubuntu and then the MythTV packages.

---

### Post by Cyborg28 on 2008-04-10
> 
[COLOR="Red"]Next step, "MythTV Configuration". All boxes (correctly) grayed out. Clicking the "Launch MythTV Setup" produces a dialog stating "Mythbackend must be closed before continuing". I click OK and a terminal window opens and I get three lines, the last stating "New DB connection, total: 1".

Closing that window gives a second dialog asking, "Would you like to run mythfilldatabase?" Clicking OK gives me another window (this time using the Linux CLI instead of Terminal) with the same "New DB connection, total: 1" response on the last line (of two).

Closing that Window simply returns me to the "Control Centre", grayed boxes and Launch button, right where I left off, no further along than when I started. I've tried clicking "Cancel" on the dialogs in every combination, but it always comes out the same: I can't get past the Launch button screen.[/COLOR]

I've tried rebooting and logging off, but I can't get past this step. I've tried changing Roles and enabling MySQL, but nothing I've tried has gotten me any further along.

[COLOR="Green"]I did discover that if I launch "MythTV Backend Setup" from the System menu, it does the exact same thing, with the two dialogs and Terminal & CLI windows. So apparently, clicking the "Launch MythTV Setup" from the Control Centre is simply running the same "Backend setup", and when done, simpy returns to the Control Centre app.[/COLOR]


Bump.

Having similar problems to OP, using clean basic install of Mythbuntu.  I can't seem to get as far as the OP as running mythtv configuration or backend setup simply sends me to the login window.

Please help,

:confused:Cyborg28

---

### Post by Sef on 2008-04-10
Moved to Mythbuntu forum.

---

### Post by Mugsy323 on 2008-04-10
> **warp99 said:**
> If you just want to just see HDTV content you can use another program. such as tvtime, kwintv, or motv.
Thanks for all the good info.

I tried "tvtime", but all it could do is standard "Composite" TV, not HD (and I couldn't get the sound to work either). I'll try some of those other apps.

I knew Myth was probably overkill for what I wanted, but could find no other Linux app for displaying HDTV.

Transmitting HDTV over a home network sounds enticing, but for myself alone, I have no need. Sounds cool though.

Thanks.

---

### Post by Calash on 2008-04-10
How long did you wait when the window said "New DB connection, total: 1"?

This part can take some time to open (A couple of minutes over SSH -X, a minute on my backend)

This part should open up the full MythTV control panel, not just hang at that point.

---

### Post by trubblemaker on 2008-04-13
I recently ran into a similar issue.  Turns out that I had the minumum RAM requirement.  That wasn't sufficient for running both backend and frontend on the same machine.  How much ram are you using?

---

### Post by tidderd on 2008-04-14
I seem to have the same problem with it running the CLI terminal screen and making the Db connections but then not running the GUI part of the set.

I have 2GB of Ram and a AMD 2 4200+ cpu so there should be no problem there, plus it used to work but then I did an update :( thats when it all went soo wrong.

Actually thinking about copying the music/vids/pics off and rebuilding the **** thing!

---

### Post by flscott on 2008-05-05
I am having the same issues as mentioned above. I did a fresh install of Mythbuntu. I have the frontend and backend running on the same machine. Any guidance or places to look to address this would be great.

---

### Post by superm1 on 2008-05-05
the best way to start debugging this is to launch mythtv-setup from a terminal (NO sudo)

```
mythtv-setup
```

**If** you get the same behavior then launch it like this:

```
mythtv-setup.real
```

Your root cause should be in the terminal.

---

### Post by Weidbrewer on 2008-05-09
> **Mugsy323 said:**
> 

I tried "tvtime", but all it could do is standard "Composite" TV, not HD (and I couldn't get the sound to work either). I'll try some of those other apps.



Thanks.

As for the sound, I might be able to help.  I'm not familiar with the card you're using first hand, but mine (PCHDTV 5500) has a cable to connect to the line in.  In Myth, it uses the capture setting and in TV time it uses the line in.  (or the other way around.)  Check your ALSA settings and make sure that you don't have anything muted or turned down.  (Also, in the preferences, make sure that you have the sliders for both line-in and capture 1 and 2 selected and visible.)

---

### Post by ozybushwalker on 2008-05-12
When I run mythtv-setup.real it dies reporting "Illegal Instruction".

here's the details
```

arthur@kubuntu:~$ mythtv-setup.real -v all
2008-05-12 22:06:46.071 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-12 22:06:46.229 XScreenSaver support enabled
2008-05-12 22:06:46.237 DPMS is active.
2008-05-12 22:06:46.239 Empty LocalHostName.
2008-05-12 22:06:46.239 Using localhost value of kubuntu
2008-05-12 22:06:46.243 MCP::DefaultUPnP() - No default UPnP backend
2008-05-12 22:06:46.398 New DB connection, total: 1
2008-05-12 22:06:46.505 Connected to database 'mythconverg' at host: localhost
2008-05-12 22:06:46.527 Closing DB connection named 'DBManager0'
2008-05-12 22:06:46.528 Clearing Settings Cache.
2008-05-12 22:06:46.579 Primary screen 0.
2008-05-12 22:06:46.580 Connected to database 'mythconverg' at host: localhost
2008-05-12 22:06:46.584 MSqlQuery: SELECT data FROM settings WHERE value = 'RunF
rontendInWindow' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.585 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname IS NULL;
2008-05-12 22:06:46.586 Using screen 0, 800x600 at 0,0
2008-05-12 22:06:46.587 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.588 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname IS NULL;
2008-05-12 22:06:46.589 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.590 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname IS NULL;
2008-05-12 22:06:46.592 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.593 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-05-12 22:06:46.594 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.595 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2008-05-12 22:06:46.597 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.598 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2008-05-12 22:06:46.650 Enabling Settings Cache.
2008-05-12 22:06:46.650 Clearing Settings Cache.
2008-05-12 22:06:46.669 MSqlQuery: CREATE TABLE IF NOT EXISTS schemalock ( schemalock int(1));
2008-05-12 22:06:46.670 MSqlQuery: LOCK TABLE schemalock WRITE;
2008-05-12 22:06:46.673 New DB connection, total: 2
2008-05-12 22:06:46.674 Connected to database 'mythconverg' at host: localhost
2008-05-12 22:06:46.676 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.693 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname IS NULL;
2008-05-12 22:06:46.695 MSqlQuery: UNLOCK TABLES;
2008-05-12 22:06:46.695 Current Schema Version: 1214
2008-05-12 22:06:46.697 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillFixProgramIDsHasRunOnce' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.698 MSqlQuery: SELECT data FROM settings WHERE value = 'DBMSVersionOverride' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.699 MSqlQuery: SELECT data FROM settings WHERE value = 'DBMSVersionOverride' AND hostname IS NULL;
2008-05-12 22:06:46.700 MSqlQuery: SELECT VERSION();
2008-05-12 22:06:46.702 Clearing Settings Cache.
2008-05-12 22:06:46.721 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.722 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname IS NULL;
2008-05-12 22:06:46.724 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeWidth' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.725 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeWidth' AND hostname IS NULL;
2008-05-12 22:06:46.726 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeHeight' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.727 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeHeight' AND hostname IS NULL;
2008-05-12 22:06:46.766 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.767 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname IS NULL;
2008-05-12 22:06:46.768 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.769 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname IS NULL;
2008-05-12 22:06:46.798 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname = 'kubuntu' ;
2008-05-12 22:06:46.799 MSqlQuery: SELECT data FROM settings WHERE value = 'DispaySizeHeight' AND hostname IS NULL;
Illegal instruction
arthur@kubuntu:~$

```

---

