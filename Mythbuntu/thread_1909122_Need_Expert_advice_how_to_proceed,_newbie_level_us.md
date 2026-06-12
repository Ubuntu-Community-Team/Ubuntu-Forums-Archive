---
title: "Need Expert advice how to proceed, newbie level user."
date: 2012-01-14
forum: Mythbuntu
---

### Post by Shabakthanai on 2012-01-14
Kubuntu 11.04
Kde 4.6.5
pcHDTV HD-5500 tuner card
EVGA GTX460 1024mb gddr5 GPU

After a fresh Install of Kubuntu 11.04, I attempted to compile the stable version of MythTV from the source code.  I am lost and confused and need advice whether to continue to compile, or to remove my incomplete attempt to compile, or to re-install the OS and start fresh once more.  If removal is recommended, how do I do this safely?

I want to continue to retain a KDE desktop with MythTV installed.  Thank you.:)

---

### Post by bluexrider on 2012-01-14
add myth tv to your software sources 
```

sudo apt-add-repository ppa:mythbuntu/0.24
```
Update
```
sudo apt-get update
```
Install
```
sudo apt-get install mythtv
```

---

### Post by Buntumatic on 2012-01-14
Considering all the information you've provided I'd conclude something may be wrong.

Alright, you are not happy with MythTV provided in repos. Why?
Are you trying to use analog or digital part of your card?
What version of MythTV are you trying to build?
Where you get stuck with compilation?

---

### Post by Shabakthanai on 2012-01-14
Are Kubuntu and Ubuntu the same when installing MythTV?  Are superuser privileges required?

I selected Alt+F2>: kdesudo mythtv-setup, sudo mythtv-setup, kdesudo mythtv, and sudo mythtv; none of these options opened the configuration page.  I opened mythtv from the GUI to get the following:

"MythTV could not connect to the database.  Please verify your database settings below."

Is 'localhost' the correct entry for "*Hostname"?
Is 'mythconverg' the correct entry for "Database name:"?
Is 'mythtv' the correct entry for "User:"?
Is 'mythtv' the correct entry for "Password:"?

If I leave Database Configuration 2/2 as is, should the configuration be complete?  Thank you.

With all the entries as above, when I click on 'Finish', I get a small window that says:  Cannot and OK.  When I click on OK it returns to the Database Configuration 1/2 page.

---

### Post by Buntumatic on 2012-01-14
You can run setup as user, mythtv-setup. After setting it up you need to start mythbackend as root, then you can run mythfrontend as user.

---

### Post by Shabakthanai on 2012-01-14
My first attempt to configure was as user, but the settings were not accepted.  I was returned to 1/1 with the initial preset configuration.  That was the reason for the individual questions in the previous post.  Then when I tried sudo or kdesudo, they were not accepted either.

There are only 2 screens to configure with mythtv-setup.  When I finished 2/2 and clicked on 'finish', instead of presenting new options, it reverted to 1/1.

My concern is that I am not entering the proper name where 'localhost' is pre-entered; my IP address is: 192.168.0.111, should I have used that instead of 'localhost'? as Hostname and mythtv as the password, or is there a computer generated password that should be used instead of mythtv, or do I just accept all the default entries and click on 'finish'?  And if that is the case, what is the purpose of me setting the configuration at all?  Sorry for the confusion.

You said, "You can run setup as user, mythtv-setup."  When I open the panel entry, Kmenu>Applications>System>mythtv-setup ('MythTV Backend Setup' is grayed out and below that entry) that is where I have been starting each attempt at configuration, which results in a loop.

Next, you said, "After setting it up you need to start mythbackend as root"; is that an Alt+F2>'sudo(or kdesudo) mythbackend' entry, which then opens mythbackend configuration in 'root'?

Next you said, "then you can run mythfrontend as user.".  Do I type 'mythfrontend' in the command line to open further options for configuration?

I am trying to confirm that I understand your terminology.  Yes, I am confused.

Thanks for any clarification.

And finally, to clarify a question I have never been sure I understood, "is the shortcut 'Alt+F2' the same as opening a command line?"  I want to be sure I am not mixing two different procedures.

I hope you will continue to be patient with me.  Thanks if you do?

---

### Post by Buntumatic on 2012-01-14
Sorry, I do not use GUI for administrative tasks. All commands I mentioned were to be run from terminal.
Let's start from beginning. If you run mythtv-setup from terminal as user, what do you get.

BTW, you did not answer my question about analog/digital. FYI the chances are slim analog part of this particular card would work with MythTV 0.24.

---

### Post by Shabakthanai on 2012-01-15
That was just great; I ran 'sudo mythtv-setup, which opened a group of configurable windows.  I tried to fill them out as well as I could figure them out.

In response to your question re: analog, before, when I had mythtv working for a while, I included both analog and digital tuners.  The TVtuner Card I have has both.  This time, when I attempted to designate both analog and digital, the name of my card was not among the choices, however I did find a digital card that showed my card when I clicked on it, so I hope I have my card identified, both digital and analog.  

I still have not gotten to a part of configuration where channels are sought, etc.

I typed in sudo mythfrontend and a GUI opened with a window which said:  Could not connect to the master backend server.  It is running??  Is the IP address set for it in mythtv-setup correct? Could not connect to the master backend server.  It is running?  Is the IP address set for it in mythtv-setup correct?  I clicked OK and new configurable choices appeared.  What do I do about "Could not connect to the master backend server.  It is running??  Is the IP address set for it in mythtv-setup correct? Could not connect to the master backend server.  It is running?"

My lack of understanding is causing me to be confused again.  Also, the mouse is not visible on the configurable screen.  Why is this? and what can I do to locate the items?  There is not even an underscored letter to engage using the Alt key.  I tried Alt+O to see if it would click the OK, it didn't work.

It does look like I am getting closer to finish again, though.  Can you help me get back on track?  Thanks in advance.

---

### Post by nickrout on 2012-01-15
> **Shabakthanai said:**
> That was just great; I ran 'sudo mythtv-setup, which opened a group of configurable windows.
why? you should NOT run it as sudo. Simply run it and the script will ask for a pssword to do the appropriate seteps that require root user privileges>   I tried to fill them out as well as I could figure them out.

In response to your question re: analog, before, when I had mythtv working for a while, I included both analog and digital tuners.  The TVtuner Card I have has both.  This time, when I attempted to designate both analog and digital, the name of my card was not among the choices, however I did find a digital card that showed my card when I clicked on it, so I hope I have my card identified, both digital and analog.  

I still have not gotten to a part of configuration where channels are sought, etc.

I typed in sudo mythfrontend  again NO. mythfrontend should not be run via sudo, or by root at all. It should be run a as your ordinary user> and a GUI opened with a window which said:  Could not connect to the master backend server.  It is running??  Is the IP address set for it in mythtv-setup correct? Could not connect to the master backend server.  It is running?  Is the IP address set for it in mythtv-setup correct?  I clicked OK and new configurable choices appeared.  What do I do about "Could not connect to the master backend server.  It is running??  Is the IP address set for it in mythtv-setup correct? Could not connect to the master backend server.  It is running?"

My lack of understanding is causing me to be confused again.  Also, the mouse is not visible on the configurable screen.  Why is this? and what can I do to locate the items?  There is not even an underscored letter to engage using the Alt key.  I tried Alt+O to see if it would click the OK, it didn't work.

It does look like I am getting closer to finish again, though.  Can you help me get back on track?  Thanks in advance.

---

### Post by Buntumatic on 2012-01-15
> **Buntumatic said:**
> You can run setup as user, mythtv-setup. After setting it up you need to start mythbackend as root, then you can run mythfrontend as user.

I thought this information was clear enough, run setup as user, start backend as root, run frontend as user.
What did I miss? Why I wasn't understood?

---

### Post by Shabakthanai on 2012-01-15
Referring to your #7 post, I ran mythtv-setup from the shell.  I get a screen to choose English US, next page Configuration 1/2.  First entry says "MythTV could not connect to the database.  Please verify your database settings below."  At this point I do not know what to do.

I Googled "mythtv-setup".  [http://www.mythtv.org/wiki/Mythtv-setup](http://www.mythtv.org/wiki/Mythtv-setup)

It suggest that running "mythtv-setup", a gui menu should appear offering the following options:  General, Capture Cards, Video sources, Input connections, Channel Editor, Storage Directories, and System Events.

I do not get this at all.  The first screen opens with Country on the left "United States" and Language on the right "English (United States).  I click 'save'.  The next screen has a small box in the center of the screen that says No/UPnP/OK.  I click on that box and the next screen says:  Screen title, "Database Configuration 1/2"

First entry says, " MythTV could not connect to the database.  Please verify your database settings below.  Required fields are marked with an asterisk (*).

Next title says, "Database Server Settings"
     *Hostname:  localhost
     x Ping test server?        Port:  'empty'
     Database name:    mythconverg
     User:    mythtv
     Password:  mythtv
                                       Next

I click on next and get title, "Database Configuration 2/2
     x  Use custom identifier for frontend preferences  (not required, so I do not check it.  The x is to show there is a checkbox.)
     x  Enable database server wakeup  (again not required, so I do not check it.)

The final entry is "Finish" in the lower right corner of the screen.  I click on "Finish" and the screen returns to the previous page.  

If I have made any changes on page 1/2, they return to the default entries I showed above.

The only way I can get the screen that is described in the mythtv tutorial is to open it using sudo.

When it opens, the "Backend Setup" shows my IP address:  192.168.0.111, Port as 6543, Status Port as 6544, Security PIN as 0000, then the title Master Backend and my IP address and port.

When I close "sudo mythtv-setup", a window appears that says, "Would you like to start the mythtv backend? I click No and a window appears that says, "Would you like to run mythfilldatabase, what I describe when I open NOT in sudo or what I get when I open in sudo?

What should I get for a screen when I run 'mythtv-setup' from the command line?

---

### Post by nickrout on 2012-01-15
> **Shabakthanai said:**
> Referring to your #7 post, I ran mythtv-setup from the shell.  I get a screen to choose English US, next page Configuration 1/2.  First entry says "MythTV could not connect to the database.  Please verify your database settings below."  At this point I do not know what to do.

I Googled "mythtv-setup".  [http://www.mythtv.org/wiki/Mythtv-setup](http://www.mythtv.org/wiki/Mythtv-setup)

It suggest that running "mythtv-setup", a gui menu should appear offering the following options:  General, Capture Cards, Video sources, Input connections, Channel Editor, Storage Directories, and System Events.

I do not get this at all.  The first screen opens with Country on the left "United States" and Language on the right "English (United States).  I click 'save'.  The next screen has a small box in the center of the screen that says No/UPnP/OK.  I click on that box and the next screen says:  Screen title, "Database Configuration 1/2"

First entry says, " MythTV could not connect to the database.  Please verify your database settings below.  Required fields are marked with an asterisk (*).

Next title says, "Database Server Settings"
     *Hostname:  localhost
     x Ping test server?        Port:  'empty'
     Database name:    mythconverg
     User:    mythtv
     Password:  mythtv
                                       Nextyou need to put in the correct password. It was randomly generated and reported to you when you first set up mythtv from the ubuntu packages. Look in /home/USER/.mythtv/mysql.txt and /root/.mythtv/mysql.txt and see if the password is in there. (Where USER = your user name)> 

I click on next and get title, "Database Configuration 2/2
     x  Use custom identifier for frontend preferences  (not required, so I do not check it.  The x is to show there is a checkbox.)
     x  Enable database server wakeup  (again not required, so I do not check it.)

The final entry is "Finish" in the lower right corner of the screen.  I click on "Finish" and the screen returns to the previous page.  

If I have made any changes on page 1/2, they return to the default entries I showed above.

The only way I can get the screen that is described in the mythtv tutorial is to open it using sudo.

When it opens, the "Backend Setup" shows my IP address:  192.168.0.111, Port as 6543, Status Port as 6544, Security PIN as 0000, then the title Master Backend and my IP address and port.

When I close "sudo mythtv-setup", a window appears that says, "Would you like to start the mythtv backend? I click No and a window appears that says, "Would you like to run mythfilldatabase, what I describe when I open NOT in sudo or what I get when I open in sudo?

What should I get for a screen when I run 'mythtv-setup' from the command line?

---

### Post by nickrout on 2012-01-15
PS you can re-set up the password by running the following commands in a terminal:

```
sudo dpkg-reconfigure mythtv-database
```

answer yes to the question posed

```
sudo dpkg-reconfigure mythtv-common
```

the first question **Database to be used to hold MythTV data**" - the answer is **mythconverg **(should be the default)

The second question **Username used by MythTV to access its database**: - answer is **mythtv **(should be the default)

The third question **Password used by MythTV to access its database** you can leave blank, and get a random password, or insert something you can remeber, i suggest you do the latter and use **mythtv** for the password.

Then when you start mythtv-setup OR mythfrontend, you will know what the password is supposed to be.

PS there is a 4th question about what computer the database is on, leave this as **localhost**

---

### Post by Shabakthanai on 2012-01-18
I applied your instructions, including changing the password and Host.  The result was just more of the same that I have been experiencing.

I did an additional google search and came up with this website:

/wiki/User_Manual:Detailed_configuration_Frontend#Database_Configuration_1.2F2I

Since using the 'localhost' did not work, I tried 127.0.0.1.  There was a place for a pin number that was different from the manual, so I changed it to 0000 as advised.  As a result of these changes, I have been able to configure the frontend and lock about 18 channels.  I used the manual settings throughout the process, however when it came to starting the TV, I got an error that asked if the backend was working.

There are so many parts to this installation, that I am unable to be absolutely certain, but there was a point prior to attempting to open the TV that I clicked 'Yes' if I wanted the backend started as well as mythfilldatabase, so I believe there is something that prevents front and backend from communicating.

Is there some kind of command line entry that would help diagnose this part of the problem?  Additionally, I am unable to get the selection of screen theme choices that were available before.  As a result, I am unfamiliar with the theme I am using.  It may not be important, but it would certainly help if I had the previous menu's to work with.

I realise you must be frustrated with me, but I have been attempting to follow your instructions faithfully and still have probably made some mistakes.  I will be grateful if you are willing to stay with me on this one.  Thanks for your ongoing patience.

---

### Post by nickrout on 2012-01-18
I think you mean you configured the backend to get 18 channels. Please be precise. mythtv-setup sets up the BACKend.

Now you can't start the frontend? Try```
ps aux|grep [b]ackend
```

That will show if the backend is running. Here is my output:

> nick@dell:~$ ps aux|grep [b]ackend
mythtv    2118  0.4  0.5 280596  7728 ?        Sl   Jan12  44:17 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv

By the way 'ps aux' lists all system processes, piping it though 'grep [b]ackend' searches for a process with the name including the name 'backend'

If it is NOT running, start it with ```
sudo service mythtv-backend start
```

Then run the ps command (as above)  again to check it is running.

Once you are sure the backend is running, run the frontend from the command line, and it will spit any debugging messages to the terminal you ran it from.```
mythfrontend
```

---

### Post by Shabakthanai on 2012-01-19
Here is what I got:

steven@Yeshuah:~$ ps aux|grep [b]ackend
mythtv    9568  0.0  0.9 578916 36832 ?        Sl   Jan17   1:06 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
steven@Yeshuah:~$ mythfrontend
2012-01-19 17:12:13.548 mythfrontend version: fixes/0.24 [v0.24.1-120-g294968b] [www.mythtv.org](www.mythtv.org)
2012-01-19 17:12:13.548 Using runtime prefix = /usr
2012-01-19 17:12:13.548 Using configuration directory = /home/steven/.mythtv
2012-01-19 17:12:13.548 Configuration::Load - Error parsing: /home/steven/.mythtv/config.xml at line: 1  column: 1
2012-01-19 17:12:13.548 Configuration::Load - Error Msg: unexpected end of file
2012-01-19 17:12:13.548 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
2012-01-19 17:12:14.204 Unable to read configuration file mysql.txt
2012-01-19 17:12:14.204 Empty LocalHostName.
2012-01-19 17:12:14.204 Using localhost value of Yeshuah
2012-01-19 17:12:14.204 Configuration::Load - Error parsing: /home/steven/.mythtv/config.xml at line: 1  column: 1
2012-01-19 17:12:14.204 Configuration::Load - Error Msg: unexpected end of file
2012-01-19 17:12:14.220 New DB connection, total: 1
2012-01-19 17:12:14.222 Connected to database 'mythconverg' at host: localhost
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
2012-01-19 17:12:14.225 Closing DB connection named 'DBManager0'
2012-01-19 17:12:14.225 Connected to database 'mythconverg' at host: localhost
2012-01-19 17:12:14.226 Current locale en_US
2012-01-19 17:12:14.226 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-01-19 17:12:14.434 DPMS is disabled.
2012-01-19 17:12:14.492 Desktop video mode: 3600x1080 60.000 Hz
2012-01-19 17:12:14.542 Enabled verbose msgs:  important general
2012-01-19 17:12:14.561 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2012-01-19 17:12:14.563 Loading en_us translation for module mythfrontend
2012-01-19 17:12:14.591 MythUIHelper, Warning: No theme dir: '/usr/share/mythtv/themes/Mythbuntu'
2012-01-19 17:12:14.591 Could not find theme: Mythbuntu - Switching to Terra
2012-01-19 17:12:14.592 Desktop video mode: 3600x1080 60.000 Hz
2012-01-19 17:12:14.595 Trying 640x480 0.000 Hz
DisplaResX: Desired Resolution and FrameRate not found.
2012-01-19 17:12:14.595 SwitchToGUI: xrandr failed for 640x480 0.000  Hz
2012-01-19 17:12:14.637 LIRC: Successfully initialized '/dev/lircd' using '/home/steven/.mythtv/lircrc' config
2012-01-19 17:12:14.637 JoystickMenuThread: Joystick disabled - Failed to read /home/steven/.mythtv/joystickmenurc
2012-01-19 17:12:14.700 Using Frameless Window
2012-01-19 17:12:14.700 Using Full Screen Window
2012-01-19 17:12:14.703 Using the OpenGL painter
2012-01-19 17:12:14.801 OpenGL: OpenGL vendor  : NVIDIA Corporation
2012-01-19 17:12:14.801 OpenGL: OpenGL renderer: GeForce GTX 460/PCI/SSE2
2012-01-19 17:12:14.801 OpenGL: OpenGL version : 4.1.0 NVIDIA 270.41.06
2012-01-19 17:12:14.801 OpenGL: Max texture size: 16384 x 16384
2012-01-19 17:12:14.801 OpenGL: Max texture units: 4
2012-01-19 17:12:14.801 OpenGL: Direct rendering: Yes
2012-01-19 17:12:14.801 OpenGL: Initialised MythRenderOpenGL
2012-01-19 17:12:15.407 Current MythTV Schema Version (DBSchemaVer): 1264
2012-01-19 17:12:16.299 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-01-19 17:12:16.299 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-01-19 17:12:16.317 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-01-19 17:12:16.317 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-01-19 17:12:16.616 Registering Internal as a media playback plugin.
2012-01-19 17:12:16.639 No plugins directory /usr/lib/mythtv/plugins
2012-01-19 17:12:16.654 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.654 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.654 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.655 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.655 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.655 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.656 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.657 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.657 MediaMonitorUnix::AddDevice() - empty device path.
2012-01-19 17:12:16.831 Found mainmenu.xml for theme 'Terra'
2012-01-19 17:12:17.124 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-01-19 17:12:17.124 Using protocol version 63
2012-01-19 17:12:26.999 TV: Attempting to change from None to WatchingLiveTV
2012-01-19 17:12:26.999 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-01-19 17:12:27.000 Using protocol version 63
2012-01-19 17:12:27.048 Spawning LiveTV Recorder -- begin
2012-01-19 17:12:27.304 Spawning LiveTV Recorder -- end
2012-01-19 17:12:27.304 GetEntryAt(-1) failed.
2012-01-19 17:12:27.304 It appears that your backend may be misconfigured.  Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors.  This issue is commonly caused by failing to complete all setup steps properly.  You may wish to review the documentation for mythtv-setup.
2012-01-19 17:12:27.304 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2012-01-19 17:12:27.304 TV Error: HandleStateChange(): LiveTV not successfully started
2012-01-19 17:12:27.304 We have a RingBuffer
2012-01-19 17:12:27.304 TV Error: LiveTV not successfully started
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
2012-01-19 17:12:46.852 Failed to mount /dev/sdc.
2012-01-19 17:12:47.669 OpenGL: Deleting OpenGL Resources
2012-01-19 17:12:47.710 Deleting UPnP client...
2012-01-19 17:12:48.383 Trying 3600x1080 50.000 Hz
2012-01-19 17:12:48.383 SwitchToGUI: Switched to 3600x1080 60.000 Hz
steven@Yeshuah:~$ sudo service mythtv-backend start
[sudo] password for steven: 
start: Job is already running: mythtv-backend
steven@Yeshuah:~$ 

The theme is unrecognisable to me and doesn't have the options I expect, and it does not play any TV.  I am sure that I locked in several channels.  Also, Notice it says trying '3600x1080';  I think that is what caused the dwarf like images before.  My primary monitor has an 16x 9 ratio and is 1920x1080.

If 3600x1080 is wrong how do I change it?  I attempted to change it in system settings, but it would not accept 1980x1080 and reverted to the 3600x19080 configuration.

I thought my backend was running, but when I couldn't get mythfrontend to function, I went ahead and entered your second command line instruction; it said it is already running: mythtv-backend.

By the way thanks for your ongoing patience.

It is below freezing cold with minor snow here; how is the sunshine in your neck of the woods?

---

### Post by Buntumatic on 2012-01-19
Shabakthanai,

I'm in this time for a generic advice. In any UNIX when you see the word **error** that usually means anything after that is meaningless. The error you are getting has to be fixed before proceeding. You may get a new error then, and it has to be fixed, too. Once you do not see any more errors in log you can expect things start working.
In this case it's quite clear your mythtv-setup didn't succeed. I recommend checking permissions on your ~/.mythtv directory and files, it's possible you screwed it up when running mythtv-setup as root.

---

### Post by nickrout on 2012-01-19
> 2012-01-19 17:12:27.304 It appears that your backend may be misconfigured. Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors. This issue is commonly caused by failing to complete all setup steps properly. You may wish to review the documentation for mythtv-setup.

Clearly you didn't finish mythtv-setup

---

### Post by Buntumatic on 2012-01-19
Oh, and it was 75 F degrees today, I fired up my Harley and rode it for an hour, I really enjoyed it, thanks for asking. :D What's your zip?

---

### Post by Shabakthanai on 2012-01-19
Under "Properties" for '.mythtv', both Owner and Group can view and modify content; x Only owner can rename and delete folder content.

Ownership is User: steven and Group: steven

Most of the time when I see an error message, I do not understand how to fix the problem. This is a good example.  

The way I understand your comment, something is wrong with my permissions in the .mythtv folder.

I apparently have the permission to modify .mythtv, but do not yet understand how to do that.

Some of my replies to posts have included the readout of a command-line entry where errors are present.  When I ask about them, I don't believe I have gotten a reply.

Gradually I am getting more understanding, but perhaps not fast enough or good enough to get the help I need.  It is a difficult thing to be technically less-gifted.  I expect it is very frustrating to help someone like me.  I do appreciate the kindness extended though.

In my previous reply, I included the readout from a 'mythfrontend' command.

First error reads:

2012-01-19 17:12:13.548 Configuration::Load - Error parsing: /home/steven/.mythtv/config.xml at line: 1 column: 1
 2012-01-19 17:12:13.548 Configuration::Load - Error Msg: unexpected end of file

[COLOR="black"]**When I open that file, there is no content at all.  The page is blank.  IF the second error message is about that same configuration file, it is without data too.**[/COLOR]

2012-01-19 17:12:14.204 Unable to read configuration file mysql.txt

**This line does not say it has an error, but when I open mysql.txt, that txt file is also a blank page with no information.**

012-01-19 17:12:14.204 Configuration::Load - Error parsing: /home/steven/.mythtv/config.xml at line: 1 column: 1
 2012-01-19 17:12:14.204 Configuration::Load - Error Msg: unexpected end of file

**These errors are same as before, the file does not contain any information at all.**

2012-01-19 17:12:14.492 Desktop video mode: 3600x1080 60.000 Hz

**This doesn't post as an error, however my primary monitor is 1920x1080 (16x9) and my secondary monitor is 1680x1050 (16x10)**

2012-01-19 17:12:16.299 ThemeInfo, Warning: Unable to open themeinfo.xml for 

**I have no idea what the cure for this might be.**

2012-01-19 17:12:16.299 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.

**How would I supply the missing information?**

2012-01-19 17:12:16.317 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
 2012-01-19 17:12:16.317 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
 2012-01-19 17:12:16.616 Registering Internal as a media playback plugin.
 2012-01-19 17:12:16.639 No plugins directory /usr/lib/mythtv/plugins

**Are these items something I could enter using Synaptic Package Manager?**

2012-01-19 17:12:27.304 It appears that your backend may be misconfigured. Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors. This issue is commonly caused by failing to complete all setup steps properly. You may wish to review the documentation for mythtv-setup.
 2012-01-19 17:12:27.304 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
 2012-01-19 17:12:27.304 TV Error: HandleStateChange(): LiveTV not successfully started

**I do not have the knowledge or experience to answer these questions without help.**

2012-01-19 17:12:27.304 TV Error: LiveTV not successfully started
 mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
 2012-01-19 17:12:46.852 Failed to mount /dev/sdc.
 2012-01-19 17:12:47.669 OpenGL: Deleting OpenGL Resources
 2012-01-19 17:12:47.710 Deleting UPnP client...

**Where do I find the missing SDC and do I put it in both fstab and mtab when I have located it?**

I posted that command line entry looking for help finding the solution to the problems it contained.  I don't know what to do without outside help.

I would copy the contents of the files that I found empty, but they did not even contain even one letter or digit.  They are blank files.

---

### Post by Shabakthanai on 2012-01-20
Dear Buntumatic,  My zip is 45402.  Years ago, I used to ride.  Great feeling of freedom and power.  I used to live in San Diego and went in the first Harley Shop many times.  A couple of pretty roudy pubs near it with lots of Harley riders.  I met one of the riders named "Filthy Frank McNasty who was married to McPig". Interesting fellow who parked his Harley in his living room. Pretty funny, huh.

---

### Post by Buntumatic on 2012-01-20
Alright, let's start from beginning, as I said only the first error makes sense, following errors are usually just meaningless as they are the result of first one.  In this case, however, the first two need to be addressed. 

Have you tried removing  /home/steven/.mythtv/config.xml and /home/steven/.mythtv/mysql.txt and re-running mythtv-setup as user.

---

### Post by Shabakthanai on 2012-01-21
Maybe now things will change, this screen has always started with errors:

MythTV Setup Terminal:

2012-01-21  13:11:39.523  Using localhost value of Yeshuah
2012-01-21  13:11:39.523  New DB connection, total: 1
2012-01-21  13:11:39.523  Unable to connect to database!
2012-01-21  13:11:39.523  Driver error was [1/1045]:
QMYSQL:  Unable to connect
Database error was:
Access denied for user 'mythtv'@;localhost' (using password: YES)
....................................................................

2012-01-21  13:11:41:775  UPnPautoconf() - No UPnP backends found
2012-01-21  13:11:41:775  No UPnP backends found
2012-01-21  13:11:41:777  Could not find theme:  - Switching to Terra
2012-01-21  13:11:41:788  Desktop video mode:  3600x1080 60.000 Hz
2012-01-21  13:11:41:797  get_ip:  No address associated with hostname
2012-01-21  13:11:41:797  LIRC, Error:  Failed to parse IP address ''
2012-01-21  13:11:41:797  JoystickMenuThread:  Joystick disabled - Failed to read /home/steven/.mythtv/joystickmenurc
2012-01-21  13:11:41:809  Using Frameless Window
2012-01-21  13:11:41:809  Using Full Screen Windoow
2012-01-21  13:11:41:811  Using the Qt painter

At this point a gui appears:

Country (on the left screen w/flags) Language ( on the right screen with different government names).  I select 'English (United States and Save)to continue.  I cannot continue because I have to solve the above errors first, and need help with that.

---

### Post by nickrout on 2012-01-21
> **Shabakthanai said:**
> Maybe now things will change, this screen has always started with errors:

MythTV Setup Terminal:
really? looks more like mythfrontend to me. mythtv-setup and mythfrontend are DIFFERENT things. If you are running mythfrontend do NOT say you are running mythtv-setup, it just confuses things. > 

2012-01-21  13:11:39.523  Using localhost value of Yeshuah
2012-01-21  13:11:39.523  New DB connection, total: 1
2012-01-21  13:11:39.523  Unable to connect to database!
2012-01-21  13:11:39.523  Driver error was [1/1045]:
QMYSQL:  Unable to connect
Database error was:
Access denied for user 'mythtv'@;localhost' (using password: YES)
....................................................................

2012-01-21  13:11:41:775  UPnPautoconf() - No UPnP backends found
2012-01-21  13:11:41:775  No UPnP backends found
2012-01-21  13:11:41:777  Could not find theme:  - Switching to Terra
2012-01-21  13:11:41:788  Desktop video mode:  3600x1080 60.000 Hz
2012-01-21  13:11:41:797  get_ip:  No address associated with hostname
2012-01-21  13:11:41:797  LIRC, Error:  Failed to parse IP address ''
2012-01-21  13:11:41:797  JoystickMenuThread:  Joystick disabled - Failed to read /home/steven/.mythtv/joystickmenurc
2012-01-21  13:11:41:809  Using Frameless Window
2012-01-21  13:11:41:809  Using Full Screen Windoow
2012-01-21  13:11:41:811  Using the Qt painter

At this point a gui appears:

Country (on the left screen w/flags) Language ( on the right screen with different government names).  I select 'English (United States and Save)to continue.  I cannot continue because I have to solve the above errors first, and need help with that.

The following screen should have a place to put in the password you set up in my post earlier. I suggested using mythtv as the password. If you took my advice then put mythtv in as the password and continue.

---

### Post by Shabakthanai on 2012-01-23
No, that was 'mythtv-setup' run from the command-line.  I copied the content of the 'mythtv Setup Terminal until finally everything just ended up like you see on the previous post.

If I continue with the configuration of the pages that follow the screen with the flags and US language, when I get to the 'Finish' instruction, it reverts back to screen 1/2 like in a loop.

This time the data in the MythTV Setup Terminal is slightly different, however the result is the same.  If I could copy and paste the data, I would have presented it again, but it takes a while to re-type the data, and I need you to want it before I do that again.

This time, the first line of MythTV Setup Terminal is as follows:

2012-01-23 20:17:12.696 Using runtime prefix = /usr - instead of 2012-01-21 13:11:39.523 Using localhost value of Yeshuah

---

### Post by Shabakthanai on 2012-02-05
Almost did not recover from food poisoning, but I am back.  Apparently nickrout has given up on me, because I have been gone for quite a while and there is no response to my last reply to his instructions.

I would really like to get Mythtv to work.  If I am told how to completely remove and purge all entries of what I have previously done, I will be happy to start from the beginning of installation with conscientious and careful attention to a single helper.

I suspect I made a mistake earlier in the help process to result in such a long and unsuccessful post.  I am sorry for any frustration I caused to those who have tried to help me and will be extremely careful to follow the letter of instructions.

Would some expert have compassion with this old man and try again.  Thanks!

---

### Post by nickrout on 2012-02-06
> **Shabakthanai said:**
> Almost did not recover from food poisoning, but I am back.  Apparently nickrout has given up on me, because I have been gone for quite a while and there is no response to my last reply to his instructions.

I would really like to get Mythtv to work.  If I am told how to completely remove and purge all entries of what I have previously done, I will be happy to start from the beginning of installation with conscientious and careful attention to a single helper.

I suspect I made a mistake earlier in the help process to result in such a long and unsuccessful post.  I am sorry for any frustration I caused to those who have tried to help me and will be extremely careful to follow the letter of instructions.

Would some expert have compassion with this old man and try again.  Thanks!

I suggest you do a purge, and start again.

Following the instructions make it really easy.

---

### Post by Shabakthanai on 2012-02-06
Thanks for returning.  I am embarrassed, but unless I use a GUI, I do not know how to purge from the shell.

Please give me specific code.  Then, if you will, explain the code for installing the mythtv-setup.  Does this install everything I need, including dependencies?  When completed, do I update and upgrade and dpkg --configure -a prior to continuing?  Thank you.

---

### Post by nickrout on 2012-02-06
```
dpkg -l myth*|egrep ^ii
dpkg -l mysql*|egrep ^11
```

Make a note of all the packages listed.

```
sudo aptitude purge (the list of packages you noted above)
```

This should work. I am not going to try it directly as I don't want to purge my system.

---

### Post by Shabakthanai on 2012-02-06
Just to make sure I don't start poorly, I will show my application of your instruction:

steven@Yeshuah:~$ dpkg -l myth*|egrep ^ii
ii  mythtv                                2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 A personal video recorder application (client and server)
ii  mythweb                               2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 Web interface add-on module for MythTV
steven@Yeshuah:~$ dpkg -l mysql*|egrep ^11
steven@Yeshuah:~$  sudo aptitude purge ii  mythtv                                2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 A personal video recorder application (client and server)
bash: syntax error near unexpected token `('
steven@Yeshuah:~$ ii  mythweb                               2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 Web interface add-on module for MythTV
The program 'ii' is currently not installed.  You can install it by typing:
sudo apt-get install ii
steven@Yeshuah:~$ 

Before I continue the install, is this the command line entry that I should use?  'sudo apt-get install mythtv-setup'

---

### Post by nickrout on 2012-02-06
> **Shabakthanai said:**
> Just to make sure I don't start poorly, I will show my application of your instruction:

steven@Yeshuah:~$ dpkg -l myth*|egrep ^ii
ii  mythtv                                2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 A personal video recorder application (client and server)
ii  mythweb                               2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 Web interface add-on module for MythTVMaybe this is why things are not working. You don't appear to have mythtv-frontend, mythtv-backend, mythtv-common and a whole raft of other packages installed that you need for mythtv. It might have been helpful to tell us that!> 
steven@Yeshuah:~$ dpkg -l mysql*|egrep ^11

obviously not supposed to be  egrep ^11? I meant egrep ^ii> 
steven@Yeshuah:~$  sudo aptitude purge ii  mythtv                                2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 A personal video recorder application (client and server)
bash: syntax error near unexpected token `('
steven@Yeshuah:~$ ii  mythweb                               2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 Web interface add-on module for MythTV
The program 'ii' is currently not installed.  You can install it by typing:
sudo apt-get install ii
steven@Yeshuah:~$ 

God damn NO. I said to purge the list of packages, there is no package ii. ii at the beginning of the line in the output of dpkg means the package is installed.

There is no package "mythweb2:0.24.2+fixes.20120205.a7acb7b-0ubuntu0mythbuntu3 Web interface add-on module for MythTV" The package name is mythweb.

Given the output of the dpkg line your purge would be written

```
sudo aptitude purge mythtv mythweb
```

However hold tight on that as something is very wrong here.

> Before I continue the install, is this the command line entry that I should use?  'sudo apt-get install mythtv-setup


NO there is no package called mythtv-setup.

I think you already have a working kubuntu machine. In that case

```
sudo aptitude install mythbuntu-control-centre
```

And then run mythbuntu-control-centre and configure what you want from there.

BUT hold on, lets purge your packages properly first.

Please let us have the output of 

```
dpkg -l myth*
dpkg -l mysql*
```

Copied and pasted if possible.

---

### Post by Shabakthanai on 2012-02-07
steven@Yeshuah:~$ dpkg -l myth*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythtv         2:0.24.2+fixes A personal video recorder application (clien
ii  mythweb        2:0.24.2+fixes Web interface add-on module for MythTV
steven@Yeshuah:~$ dpkg -l mysql*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  mysql-client   <none>         (no description available)
un  mysql-client-4 <none>         (no description available)
un  mysql-client-5 <none>         (no description available)
ii  mysql-client-5 5.1.54-1ubuntu MySQL database client binaries
ii  mysql-client-c 5.1.54-1ubuntu MySQL database core client binaries
ii  mysql-common   5.1.54-1ubuntu MySQL database common files, e.g. /etc/mysql
un  mysql-common-4 <none>         (no description available)
ii  mysql-server   5.1.54-1ubuntu MySQL database server (metapackage depending
un  mysql-server-4 <none>         (no description available)
un  mysql-server-5 <none>         (no description available)
ii  mysql-server-5 5.1.54-1ubuntu MySQL database server binaries and system da
un  mysql-server-c <none>         (no description available)
un  mysql-server-c <none>         (no description available)
ii  mysql-server-c 5.1.54-1ubuntu MySQL database server binaries
steven@Yeshuah:~$ 

I hope this is what you want.  I am unable to understand command-line data.  My prior attempts to install Mythtv involved using the package manager.  I realise this is the better way to install, it is just very new for me.  I am sorry to frustrate you; I could see I have tested your patience.  Thank you for continuing.  I installed 'aptitude' so I can install mythbuntu-control-center when you say.  I have a kubuntu natty OS, though, not mythbuntu OS.  Will that make a difference?  If OK, I would prefer to keep my Kubuntu OS.

---

### Post by nickrout on 2012-02-07
please give the output of ```
which mythtv-setup
dpkg -S $(which mythtv-setup)
```

---

### Post by Shabakthanai on 2012-02-07
steven@Yeshuah:~$ 
steven@Yeshuah:~$ which mythtv-setup
/usr/bin/mythtv-setup
steven@Yeshuah:~$ dpkg -S $(which mythtv-setup)
mythtv-backend: /usr/bin/mythtv-setup
steven@Yeshuah:~$

---

### Post by nickrout on 2012-02-07
```
dpkg -l mythtv-backend
dpkg -l myth\*
```

---

### Post by Shabakthanai on 2012-02-09
steven@Yeshuah:~$ dpkg -l mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythtv-backend 2:0.24.2+fixes A personal video recorder application (serve
steven@Yeshuah:~$ dpkg -l myth\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  mythappearance <none>         (no description available)
ii  mytharchive    2:0.24.2+fixes create and burn DVD's from MythTV - binary f
un  mytharchive-da <none>         (no description available)
ii  mythbrowser    2:0.24.2+fixes A web browser for MythTV
ii  mythbuntu-comm 0.59-0ubuntu1  Mythbuntu application support functions
un  mythbuntu-cont <none>         (no description available)
ii  mythbuntu-lirc 0.25-0ubuntu2  Mythbuntu Lirc Configuration Generator
ii  mythbuntu-live 0.55-0ubuntu1  Mythbuntu Live CD Installation and Configura
un  mythcontrols   <none>         (no description available)
un  mythdvd        <none>         (no description available)
un  mythes-en-gb   <none>         (no description available)
ii  mythes-en-us   1:3.3.0-2ubunt English Thesaurus for LibreOffice/OpenOffice
un  mythes-en-za   <none>         (no description available)
un  mythes-thesaur <none>         (no description available)
un  mythes-thesaur <none>         (no description available)
ii  mythexport     2.2.3-0ubuntu1 Export MythTV recording to portable media pl
un  mythflix       <none>         (no description available)
ii  mythgallery    2:0.24.2+fixes Image gallery/slideshow add-on module for My
ii  mythgame       2:0.24.2+fixes Emulator & PC Game frontend module for MythT
un  mythmovies     <none>         (no description available)
ii  mythmusic      2:0.24.2+fixes Music add-on module for MythTV
ii  mythnettv      7+dfsg-0ubuntu Plugin to download video from RSS feeds
ii  mythnettv-gui  1.0-0ubuntu3   Gui frontend for MythNetTV
un  mythnettv-svn  <none>         (no description available)
ii  mythnetvision  2:0.24.2+fixes A Internet Video Player plugin for MythTV
ii  mythnews       2:0.24.2+fixes An RSS feed news reader module for MythTV
ii  mythplugins    2:0.24.2+fixes Metapackage package for MythTV plugins
un  mythstream     <none>         (no description available)
ii  mythtv         2:0.24.2+fixes A personal video recorder application (clien
ii  mythtv-backend 2:0.24.2+fixes A personal video recorder application (serve
ii  mythtv-backend 2:0.24.2+fixes Metapackage to setup and configure a "Master
ii  mythtv-common  2:0.24.2+fixes A personal video recorder application (commo
ii  mythtv-databas 2:0.24.2+fixes A personal video recorder application (datab
ii  mythtv-doc     2:0.24.2+fixes A personal video recorder application (docum
ii  mythtv-fronten 2:0.24.2+fixes A personal video recorder application (clien
ii  mythtv-status  0.9.3-1        Show the status of a MythTV backend
ii  mythtv-theme-a 2:0.24.2+fixes The arclight MythTV Theme
un  mythtv-theme-b <none>         (no description available)
un  mythtv-theme-b <none>         (no description available)
un  mythtv-theme-b <none>         (no description available)
ii  mythtv-theme-c 2:0.24.2+fixes The childish MythTV Theme
un  mythtv-theme-g <none>         (no description available)
ii  mythtv-theme-g 2:0.24.2+fixes The graphite MythTV Theme
un  mythtv-theme-g <none>         (no description available)
un  mythtv-theme-i <none>         (no description available)
un  mythtv-theme-i <none>         (no description available)
ii  mythtv-theme-m 2:0.24.2+fixes The metallurgy MythTV Theme
un  mythtv-theme-m <none>         (no description available)
ii  mythtv-theme-m 2:0.24.2+fixes The mythbuntu MythTV Theme
un  mythtv-theme-m <none>         (no description available)
un  mythtv-theme-m <none>         (no description available)
un  mythtv-theme-n <none>         (no description available)
un  mythtv-theme-p <none>         (no description available)
un  mythtv-theme-p <none>         (no description available)
un  mythtv-theme-r <none>         (no description available)
un  mythtv-theme-t <none>         (no description available)
ii  mythtv-themes  2:0.24.2+fixes Themes for MythTV
ii  mythtv-transco 2:0.24.2+fixes Utilities used for transcoding MythTV tasks
ii  mythtvfs       0.6.1-2        userspace filesystem client for MythTV
ii  mythvideo      2:0.24.2+fixes A generic video player frontend module for M
ii  mythweather    2:0.24.2+fixes Weather add-on module for MythTV
ii  mythweb        2:0.24.2+fixes Web interface add-on module for MythTV
steven@Yeshuah:~$ 

This is the output of those commands, what next?  Thanks for your endurance and patience.

---

### Post by nickrout on 2012-02-09
OK now purge the installed myth and mysql packages as described above.

note:[LIST=1]
[*]the installed packages are the ones with ii at the start of the line
[*]only the package name is needed on the purge line ie aptotude purge mythtv-frontend NOT aptitude purge mythtv-frontend 2:
[/LIST]

---

### Post by Shabakthanai on 2012-02-12
In your instruction, under #2. and after 'ie' you use spelling 'aptotude', and after NOT you use the spelling 'aptitude'.  That appears the only difference between the two comments.  Then you suggest I purge only that identified by 'ii'.

Apparently I am way less experienced that you think.  I have read the instruction over and over; I do not understand what I am to do.

I googled 'aptotude' and it doesn't seem to be a real word.

---

### Post by nickrout on 2012-02-13
Sorry for my spelling mistake.

However my message remains the same. You need to purge the package name not anything more.

---

### Post by Shabakthanai on 2012-02-14
Is the command:

'sudo aptitude purge ii mythtv'?

---

### Post by nickrout on 2012-02-15
> **Shabakthanai said:**
> Is the command:

'sudo aptitude purge ii mythtv'?

NO IT ISN"T.

Sorry for shouting but you simply don't listen.

purge all the packages, by name.

ii is part of the output of dpkg -l, it indicates the package is installed.

you need to purge all the myth* packages. ie all the packages that were listed when you listed them via dpkg -l myth\*

The package name is the second field in the output line, the bit I have highlighted below in a sample output:

```
ii  **mythgallery**               2:0.24.2+fixes.20120124.e Image gallery/slideshow add-on module for MythTV
```

you can include as many package names in the purge line, like

```
sudo aptitude purge packagename1 packagename2
```

---

### Post by Shabakthanai on 2012-02-18
Please feel free to yell, but please do not give up on me.  

I attempted your instruction.  I copied and pasted all packages preceded by 'ii' then pressed enter (with a space between each package).  Nothing happened but the cursor going to the beginning of the next line with a blinking cursor following '>'.  I waited quite some time for something to happen, then closed out the shell and tried the same with only one package.  The same thing happened again.  No apparent progress of purging the application.  This time I waited 10 minutes for any progress of the purge process.  Here is a copy of what I typed in the command line followed by pressing the enter key:

steven@Yeshuah:~$ sudo aptitude purge ii mytharchive 2:0.24.2+fixes create and burn DVD's from MythTV - binary f
> 

Did I enter the command properly?  If I did, why did nothing happen?  Usually when I type a command the computer immediately responds and executes the command.

Thanks for your incredible patience.

---

### Post by nickrout on 2012-02-18
My patience is wearing thin. Understand the following, which I am sayng for the third time I think: There is no package called ii. There is no package called 2:0.24.2+fixes. There is no package called create.

If you want to purge mytharchive then run this:

```
sudo  aptitude purge mytharchive
```

if you want to purge mytharchive and mythtv-frontend then run

```
sudo aptitude purge mytharchive mythtv-frontend
```

How bloody hard is it?

---

### Post by Shabakthanai on 2012-02-20
Thank you, I believe I was successful.  When I made the removal, there was quite a list of dependencies that were removed that I probably should not have removed, but I was unable to view the whole list.  When I clicked on the up arrow, to try to review the whole list, strange code was written where the request for a Y/N/?.  And, I do not know how to remove only some from the list anyway.  I do not have a proper understanding of how to use the command line.  

I then tried page up to see if I could review the list of items.  And finally when I was unable to review the entire list of items to be removed, I just typed y and continued the purging.  Things like Aconadi, kmail and other things were removed as dependencies of mythtv application.  Then when I reinstalled Kontact and attempted to configure kmail, I was unable to get kmail configured or to work because of missing packages.  I saved the list of missing packages, but I can't find them to review the whole list.  I looked in the documents folder, but they were not there.  They are probably saved in some log folder that I do not know how to find. 

More frustration for you, I suppose, but I do not know some of the things that are common for you to know, like when you said to just remove the ones with 'ii' preceding and did not say that the numbers that follow a package name and identify the installed version of the package are not a part of the package name. Sorry, I just did not know that.  I am sure that that type of description is not needed when you are explaining a fix for someone who has experience.

Again, If you continue to be willing, I want to continue.  I have learned quite a bit just with this last step.  Thanks for that.

Now what do I do?  Do I install mythtv, and is it a command like this:

sudo apt-get install mythtv ?  And, will that include the much needed dependencies, including the wrongly removed ones that I just removed?

Thanks again for your ongoing patience.  Sorry for my stupidity.

---

### Post by nickrout on 2012-02-20
aptitude keeps its logs under /var/log

to get myth installed I think I have already said to install mythbuntu-control-centre and then use that to install the parts of mythtv you want.

I am not sure why kmail and so on would be regarded as dependencies of any myth package, but when you use aptitude to reinstall kmail all it's dependencies will be restored.

---

