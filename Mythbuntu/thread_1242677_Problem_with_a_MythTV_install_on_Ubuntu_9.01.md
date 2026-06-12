---
title: "Problem with a MythTV install on Ubuntu 9.01"
date: 2009-08-17
forum: Mythbuntu
---

### Post by Doctoxic on 2009-08-17
Hi
I have been trying to get Myth TV working using this guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

But i can't get anything to play - situation is as follows:

When i run the front-end and select &#8220;Watch TV&#8221; the screen goes blank for a few seconds and then exits back to the main menu.

Any ideas what might be causing this and how to fix it?
Please note that i did possibly mess up the back-end in that i answered YES instead of no to this bit:

==========================
Testing the Configuration
Now you can exit the setup utility. It will ask you if you want to run mythfilldatabase. Answer NO because we&#8217;re using the EIT.
==========================
I don&#8217;t know if this makes any difference at all or if it does how to correct it.


ALSO - when finishing off the back end installation it asked me if i wanted it to correct some directories for me - however it wouldn't do it (permission problem??) and it couldn't create //.test as the directory was not writeable


Here is the output from the terminal which should help:

doctoxic@quad-64bit:~$ mythfrontend
2009-08-17 16:51:15.396 Using runtime prefix = /usr
2009-08-17 16:51:15.572 XScreenSaver support enabled
2009-08-17 16:51:15.572 DPMS is active.
2009-08-17 16:51:15.573 Empty LocalHostName.
2009-08-17 16:51:15.573 Using localhost value of quad-64bit
2009-08-17 16:51:15.578 New DB connection, total: 1
2009-08-17 16:51:15.582 Connected to database 'mythconverg' at host: localhost
2009-08-17 16:51:15.583 Closing DB connection named 'DBManager0'
2009-08-17 16:51:15.584 Primary screen 0.
2009-08-17 16:51:15.584 Connected to database 'mythconverg' at host: localhost
2009-08-17 16:51:15.585 Using screen 0, 1440x900 at 0,0
2009-08-17 16:51:15.590 New DB connection, total: 2
2009-08-17 16:51:15.590 Connected to database 'mythconverg' at host: localhost
2009-08-17 16:51:15.591 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-17 16:51:15.591 Enabled verbose msgs:  important general
2009-08-17 16:51:15.763 No theme dir: /home/doctoxic/.mythtv/themes/Mythbuntu-8.04
2009-08-17 16:51:15.764 Primary screen 0.
2009-08-17 16:51:15.764 Using screen 0, 1440x900 at 0,0
2009-08-17 16:51:15.764 No theme dir: /home/doctoxic/.mythtv/themes/Mythbuntu-8.04
2009-08-17 16:51:15.765 Switching to square mode (Mythbuntu-8.04)
2009-08-17 16:51:15.777 Using the Qt painter
2009-08-17 16:51:15.778 JoystickMenuClient Error: Joystick disabled - Failed to read /home/doctoxic/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-08-17 16:51:15.778 lirc_init failed for mythtv, see preceding messages
2009-08-17 16:51:16.270 Specified base font 'medium' does not exist for font clock
2009-08-17 16:51:16.271 Specified base font 'medium' does not exist for font small
2009-08-17 16:51:16.271 Specified base font 'medium' does not exist for font medium
2009-08-17 16:51:16.271 Specified base font 'medium' does not exist for font large
2009-08-17 16:51:16.271 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-17 16:51:16.322 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-17 16:51:16.349 Registering Internal as a media playback plugin.
2009-08-17 16:51:16.405 No theme dir: /home/doctoxic/.mythtv/themes/Mythbuntu-8.04
2009-08-17 16:51:18.113 Connecting to backend server: xxx.xxx.x.x:6543 (try 1 of 5) ** i have edited out the IP number**
2009-08-17 16:51:18.114 Using protocol version 40
2009-08-17 16:51:18.259 TV: Attempting to change from None to WatchingLiveTV
2009-08-17 16:51:18.259 Using protocol version 40
2009-08-17 16:51:19.774 GetEntryAt(-1) failed.
2009-08-17 16:51:19.775 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2009-08-17 16:51:19.775 TV Error: LiveTV not successfully started
2009-08-17 16:51:19.775 TV Error: LiveTV not successfully started
2009-08-17 16:51:19.863 TV: Deleting TV Chain in destructor
2009-08-17 16:51:19.865 DPMS Deactivated 
2009-08-17 16:51:19.866 DPMS Reactivated.
2009-08-17 16:51:23.102 Deleting UPnP client...



doctoxic@quad-64bit:~$ tail -f /var/log/mythtv/mythbackend.log
2009-08-17 17:04:40.888 Reschedule requested for id -1.
2009-08-17 17:04:40.929 Scheduled 0 items in 0.0 = 0.04 match + 0.01 place
2009-08-17 17:04:54.060 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-17 17:04:54.098 ProgramInfo, Error: GetPlaybackURL: '1001_20090817161920.mpg' should be local, but it can not be found.
2009-08-17 17:04:54.136 ProgramInfo, Error: GetPlaybackURL: '1001_20090817162011.mpg' should be local, but it can not be found.
2009-08-17 17:04:54.178 ProgramInfo, Error: GetPlaybackURL: '1001_20090817162558.mpg' should be local, but it can not be found.
2009-08-17 17:04:54.219 ProgramInfo, Error: GetPlaybackURL: '1001_20090817163359.mpg' should be local, but it can not be found.
2009-08-17 17:04:54.261 ProgramInfo, Error: GetPlaybackURL: '1001_20090817164929.mpg' should be local, but it can not be found.
2009-08-17 17:04:54.302 ProgramInfo, Error: GetPlaybackURL: '1001_20090817165031.mpg' should be local, but it can not be found.
2009-08-17 17:04:54.344 ProgramInfo, Error: GetPlaybackURL: '1001_20090817165118.mpg' should be local, but it can not be found.



thanks

Doc

---

### Post by klc5555 on 2009-08-17
A Mythtv backend installed on Ubuntu expects to have created for itself a user "mythtv", which user has ownership and group rights to the whole directory structure under /var/lib/mythtv. Including /var/lib/mythtv/recordings, where mythtv by default expects to record everything including livetv. Permissions for the .../recordings directory should likely be 775. Your own username should also have been added to the "mythtv" group.

If you are using additional or different directories in your default storage group (specified in the backend setup), they all have to be set as above. If there's even one that "mythtv" can't write to, you get kicked back out to the main menu when you try to access livetv.

If the //.test couldn't be written because the directory wasn't writable, you probably need to fix your user/group/permissions on the directory(ies) in your default storage group.

The main difference in adding Mythtv packages to an existing Ubuntu installation from using a Mythbuntu install is that adding the packages does not give you the multiple partition setup that a clean installation of Mythbuntu would give you by default. This means that on a single-drive system, your recordings storage is likely to be in your root partition. This is OK up to the moment when your root partition fills to the last byte with a recording, whereupon you will have a Big Problem. If this setup scenario applies to you, then once you're up and running comfortably, you may wish to set up a different partition (or add a drive) for storage.

---

### Post by Doctoxic on 2009-08-17
thanks klc5555

seems too complex for my very rudimentary understanding - as its a fresh install i will retry with the mythbuntu install

cheers

doc

---

### Post by Doctoxic on 2009-08-17
hmmm

tried Mythbuntu
mostly same problems

it wouldn't set up the LiveTV and DB Backup directories

and

"Watch TV" is still blank and throws me back to the menu:

Are there any other alternatives to MythTV for Linux only this is driving me nuts

thanks

Doc

---

### Post by dallas8101 on 2009-10-03
Not having the logs or other important information to go on, I do see a similar appearance if I do not have the cards setup correctly in the backend.  If you are using a Haupaugge MPEG card like the PVR series (150, 350, etc) there are 2 options that seems to work when you are selecting, but I have only gotten the IVTV MPEG drivers to work with the PVR cards.  If you have a HVR 2250 or another newer card then the V4L option may be the one you want, you have to research the card to find out which is the appropriate driver.  If I have the wrong encoder driver selected when I try to watch TV it comes up to a black screen for few seconds and then exits.  Then again since I am still a beginner user, I may be sending you in the wrong direction.  Good luck.

---

### Post by TopEnder on 2009-10-12
> **Doctoxic said:**
> hmmm

tried Mythbuntu
mostly same problems

it wouldn't set up the LiveTV and DB Backup directories

and

"Watch TV" is still blank and throws me back to the menu:

Are there any other alternatives to MythTV for Linux only this is driving me nuts

thanks

Doc
G'Day, I am having the same problem with mythtv (but I will sort it out in the next ten years before I turn 80).  As an alternative "me TV" works well for me and the is help available from: [https://launchpad.net/me-tv](https://launchpad.net/me-tv)
Happy watching

---

