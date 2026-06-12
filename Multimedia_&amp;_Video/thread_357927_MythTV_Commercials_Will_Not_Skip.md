---
title: "MythTV Commercials Will Not Skip"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by jlr4u on 2007-02-10
When I first setup MythTV, commercial skipping worked fine. Now it no longer works.
In the backend MythTV Setup and verified that:

Start Auto commercial flagging jobs when the recording starts is turned on.

In the FrontEnd Utilities/Setup/Setup/TV Settings/General I verified

Commercial flag New recordings is turned on and Commercial flag methods is set to all available methods.

Can someone help!

---

### Post by barney_1 on 2007-02-10
Do you have mythweb installed?  If so, open it up in a web browser, click on Backend Status and see what it says for Job Queue.  There could be an error in the job queue of your database.

I would fix that using PhpMyAdmin because I'm not saavy with mysql database commands.  If you open up PhpMyAdmin, login to the mythconverg database, select JobQueue from the left panel, click browse in the right window, and delete the queued jobs this might fix it.

That is only if you you have a Job Queue that isn't getting run.

---

### Post by jlr4u on 2007-02-11
I tried to load MythWeb a few weeks ago and did not complete the installation.  I did not have the password set up correctly and did not relate this with the commercial skipping.  Anyway, I corrected the password, but now I am getting another permissions issue:

Data directory is not writable by www-data. 

I assume this is related to file permissions somewhere in
/var/www/mythweb

I could un-install MythWeb, but wanted to at least check it out.  
Can you Help?
Thanks in Advance

---

### Post by jlr4u on 2007-02-11
I found the commands to get MythWeb File permissions.

```
sudo chown -R www-data:www-data /usr/share/mythtv/mythweb/data
sudo chmod 775 /usr/share/mythtv/mythweb/data
sudo chmod +t /usr/share/mythtv/mythweb/data
sudo chmod 777 /var/lib/mythtv
```

---

### Post by wjston on 2007-02-11
My experience with commercial skipping failing always leads me to mythconverg in the MYSQL database. How I have resolved this is by logging into Mysql using phpmyadmin - just bring up firefox and type [http://localhost](http://localhost) in the address bar (hopefully you installed phpmyadmin when you installed MythTV) and login as root. 

Next, select mythconverg from the dropdown list in the left hand pane window under databases. Scroll down and use the "select all" to add a check mark in all the database boxes.  From the drop down box, select "repair table program" and then once that has completed go back into the drop down box and select "optimize tables." The repair tables program may take a few moments to complete so give it some time. Once it has completed, you should be able to scroll the database to see the results  - it should have an ok after each database (you may have to arrow right to see them. Once you have completed this process, logout and try recording a new show. If everything went well, commercial flagging should be back to normal.

Hope this helps

---

### Post by barney_1 on 2007-02-11
wjston, that's s great tip.  I wasn't aware of the auto-repair function of phpmyadmin.  I did that myself just to see how it works and every table had an OK next to it.  Does that mean that it didn't need to fix anything, or just that the repair was successful?

---

### Post by jlr4u on 2007-02-11
> **wjston said:**
> My experience with commercial skipping failing always leads me to mythconverg in the MYSQL database. How I have resolved this is by logging into Mysql using phpmyadmin - just bring up firefox and type [http://localhost](http://localhost) in the address bar (hopefully you installed phpmyadmin when you installed MythTV) and login as root. 

Next, select mythconverg from the dropdown list in the left hand pane window under databases. Scroll down and use the "select all" to add a check mark in all the database boxes.  From the drop down box, select "repair table program" and then once that has completed go back into the drop down box and select "optimize tables." The repair tables program may take a few moments to complete so give it some time. Once it has completed, you should be able to scroll the database to see the results  - it should have an ok after each database (you may have to arrow right to see them. Once you have completed this process, logout and try recording a new show. If everything went well, commercial flagging should be back to normal.

Hope this helps

Well I went through your suggestions, and I saw an OK after each table in the database for both Repair and Optimize .   I then went to MythTV and tried to record a program.  After selecting a channel to record and saving,  The program guide did not show any marking indicating that the program would record.  I tried again with the same repsonse.  Now when I try to watch TV, I get a message saying that MythTV is using all availabe inputs, and if I want to watch TV to cancel one of the recordings.  I can't find any recordings running.  
:confused:

---

### Post by wjston on 2007-02-12
> **jlr4u said:**
> Well I went through your suggestions, and I saw an OK after each table in the database for both Repair and Optimize .

That means the tables were all successfully repaired and optimized.

 > **jlr4u said:**
> ]I then went to MythTV and tried to record a program.  After selecting a channel to record and saving,  The program guide did not show any marking indicating that the program would record.  I tried again with the same repsonse.  Now when I try to watch TV, I get a message saying that MythTV is using all availabe inputs, and if I want to watch TV to cancel one of the recordings.  I can't find any recordings running.  
:confused:

If you only have one tuner card, then you can't watch and record at the same time - but I think you know that otherwise you probably wouldn't have known to go to "watch recordings" to see if it was recording. You must have other issues besides the database problem. If you know what the name of the recording was, go back into MYSQl and look for the name of the program under the recorded table and see if you can find the entry in the database. If it is there, see if there is an error message - basically why it didn't record. It probably has something to do with permissions. Or, go back into watch recordings first to see if it has recorded and you couldn't see the file until it finished recording. Have you changed any settings in the last little while?

---

### Post by jlr4u on 2007-02-12
Well after checking things out, I found out that the system was not even recognizing my PRV-500 card at all.  The problem was that Ubuntu came out with the new kernel 2.6.17.11 which I loaded at the same time as running the phpmyadmin table updates.   I did not relate the two and had to rebuild the IVTV scripts to get the dual tuner PRV-500 to work.  Now everything is back to normal except the commercial skipping is still not working.  I am trying to think of what I loaded when the problem first occurred, and the only thing I can think of is the Xine movie player.  Could this possible be a problem?  How do I tell what software is actually doing the recording?   MythTV has settings to change what player is being used.   I don’t remember changing any of those settings.

Thanks again for the tips on pmpmyadmin.

---

### Post by wjston on 2007-02-13
> **jlr4u said:**
> Well after checking things out, I found out that the system was not even recognizing my PRV-500 card at all.  The problem was that Ubuntu came out with the new kernel 2.6.17.11 which I loaded at the same time as running the phpmyadmin table updates.   I did not relate the two and had to rebuild the IVTV scripts to get the dual tuner PRV-500 to work.  Now everything is back to normal except the commercial skipping is still not working.  I am trying to think of what I loaded when the problem first occurred, and the only thing I can think of is the Xine movie player.  Could this possible be a problem?  How do I tell what software is actually doing the recording?   MythTV has settings to change what player is being used.   I don&#8217;t remember changing any of those settings.

Thanks again for the tips on pmpmyadmin.

Your quite welcome. If it wasn't for the forum help participants, I would probably have given up on getting my sytems working with MythTV. It is nice to know that I can repay the forums for all the contributions of others.

I doubt that Xine is your problem. It is more likely that installing the new kernel has caused some issues. The quickest way to narrow things down is to go back into **Utilities/Setup > Setup > TV Settings > General** and, on the third screen, make sure that **Commercial Flag New Recordings** has an **x** beside it. This may have been changed when you updated the kernel. If it is checked, then I would back out of MythTV to the Ubuntu desktop and start an Xterm. Type **mythfrontend**, hit enter and, when you get to Myth main screen, try recording a 30 minute show. When it is finished recording, immediately navigate to **Information Center > System Status** and check to ensure **Tuner Status** is not recording. Also, check under **Job Queue** to see if anything is running. If both are idle, then backexit out of MythTV and back to your Ubuntu desktop to see if there are any errors that you can see in the Xterm window. If there are, try posting that to see if we can narrow your problem down.

Good Luck

---

### Post by jlr4u on 2007-02-14
> **wjston said:**
> Your quite welcome. If it wasn't for the forum help participants, I would probably have given up on getting my sytems working with MythTV. It is nice to know that I can repay the forums for all the contributions of others.

I doubt that Xine is your problem. It is more likely that installing the new kernel has caused some issues. The quickest way to narrow things down is to go back into **Utilities/Setup > Setup > TV Settings > General** and, on the third screen, make sure that **Commercial Flag New Recordings** has an **x** beside it. This may have been changed when you updated the kernel. If it is checked, then I would back out of MythTV to the Ubuntu desktop and start an Xterm. Type **mythfrontend**, hit enter and, when you get to Myth main screen, try recording a 30 minute show. When it is finished recording, immediately navigate to **Information Center > System Status** and check to ensure **Tuner Status** is not recording. Also, check under **Job Queue** to see if anything is running. If both are idle, then backexit out of MythTV and back to your Ubuntu desktop to see if there are any errors that you can see in the Xterm window. If there are, try posting that to see if we can narrow your problem down.

Good Luck
I was wondering if you can make any sense out of my xterm when MythTV first loads.

```
X Error: [COLOR="Red"]BadDevice, invalid or uninitialized input device 169[/COLOR]
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: [COLOR="Red"]BadDevice, invalid or uninitialized input device 169[/COLOR]
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-02-14 17:39:53.068 Using runtime prefix = /usr
2007-02-14 17:39:53.096 Gnome-Screensaver support enabled
2007-02-14 17:39:53.096 DPMS is active.
2007-02-14 17:39:53.141 New DB connection, total: 1
2007-02-14 17:39:53.152 Connected to database 'mythconverg' at host: localhost
2007-02-14 17:39:53.156 Total desktop dim: 800x600, with 1 screen[s].
2007-02-14 17:39:53.161 Using screen 0, 800x600 at 0,0
2007-02-14 17:39:53.392 Current Schema Version: 1160
2007-02-14 17:39:53.393 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-02-14 17:39:53.393 Enabled verbose msgs:  important general
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
2007-02-14 17:39:54.147 Total desktop dim: 800x600, with 1 screen[s].
2007-02-14 17:39:54.149 Using screen 0, 800x600 at 0,0
2007-02-14 17:39:54.150 Switching to square mode (G.A.N.T.)
2007-02-14 17:39:54.207 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
[COLOR="Red"]lirc_init failed for mythtv, see preceding messages[/COLOR]
2007-02-14 17:39:54.434 Joystick disabled.
2007-02-14 17:39:54.520 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-02-14 17:39:54.630 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-02-14 17:39:54.669 Registering Internal as a media playback plugin.
2007-02-14 17:39:54.709 Registering MythDVD DVD Media Handler as a media handler ext()
2007-02-14 17:39:54.709 Registering MythDVD VCD Media Handler as a media handler ext()
2007-02-14 17:39:54.737 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-02-14 17:39:54.738 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
[COLOR="Red"]Failed to run 'cdrecord --scanbus'[/COLOR]
adding: ATA:0,0,0 -- DVD RW AD-7170A 
Failed to run 'cdrecord --scanbus'
2007-02-14 17:39:57.888 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-02-14 17:39:57.889 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-02-14 17:39:58.023 New DB connection, total: 2
2007-02-14 17:39:58.024 Connected to database 'mythconverg' at host: localhost
[COLOR="Red"]Failed to find network interface eth0[/COLOR]
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 

```

The lirc error is because I have not yet re-loaded the remote control scripts since the last kernel update.  I am using the keyboard for now.   I am using wireless and don't have etho even connected so that should not be a problem.   What is input device 169?

---

### Post by wjston on 2007-02-14
> **jlr4u said:**
> I was wondering if you can make any sense out of my xterm when MythTV first loads.

[CODE]X Error: [COLOR="Red"]BadDevice, invalid or uninitialized input device 169[/COLOR]
    What is input device 169?

This is an error that refers to the Wacom tablet. It is more an annoyance than anything else. To get rid of the error, remove the following (or comment it out) from your /etc/X11/xorg.conf file:
[COLOR="Red"]#Section "InputDevice"
# Driver "wacom"
# Identifier "stylus"
# Option "Device" "/dev/wacom" # Change to
# # /dev/input/event
# # for USB
# Option "Type" "stylus"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
# Driver "wacom"
# Identifier "eraser"
# Option "Device" "/dev/wacom" # Change to
# # /dev/input/event
# # for USB
# Option "Type" "eraser"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
# Driver "wacom"
# Identifier "cursor"
# Option "Device" "/dev/wacom" # Change to
# # /dev/input/event
# # for USB
# Option "Type" "cursor"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection[/COLOR]
Also, remove or comment out the following (stylus, curser, eraser) at the end of conf file
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
[COLOR="DarkRed"][COLOR="Red"]# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"[/COLOR][/COLOR]
EndSection

---

### Post by NT4usB on 2007-02-15
> **jlr4u said:**
> 
The lirc error is because I have not yet re-loaded the remote control scripts since the last kernel update.  I am using the keyboard for now.   I am using wireless and don't have etho even connected so that should not be a problem.   What is input device 169?

When you get to reloading lirc, post how you get along.
I go through the same drill every kernel upgrade. This time, the remote got quirky.
irw showed the right things and it controlled mplayer ok but it wouldn't control anything in myth.
I never found out why but in the process of trying to, I must have jiggled the right file because it started working...

ed: re commercial skipping. some thoughts...
Will it skip manually (z on the keyboard?)
Are the commercials actually flagged? (m on the keyboard while show is playing> edit program. z to show flags)
try toggling commercial skip off and on?
I find although shows are flagged and skipping is set to auto, sometimes myth forgets to skip.
selecting menu and clicking on (the already checked) skip commercials box refreshes it's memory...
...another thought. turn off all the other commercial detection options except for black frame detection & see what you get.

---

### Post by jlr4u on 2007-02-18
> **NT4usB said:**
> When you get to reloading lirc, post how you get along.
I go through the same drill every kernel upgrade. This time, the remote got quirky.
irw showed the right things and it controlled mplayer ok but it wouldn't control anything in myth.
I never found out why but in the process of trying to, I must have jiggled the right file because it started working...

ed: re commercial skipping. some thoughts...
Will it skip manually (z on the keyboard?)
Are the commercials actually flagged? (m on the keyboard while show is playing> edit program. z to show flags)
try toggling commercial skip off and on?
I find although shows are flagged and skipping is set to auto, sometimes myth forgets to skip.
selecting menu and clicking on (the already checked) skip commercials box refreshes it's memory...
...another thought. turn off all the other commercial detection options except for black frame detection & see what you get.

I was modifying the etc/X11/xorg.conf file and put comments in the wrong section and locked up Ubuntu.  I was able to use the live CD to mount the partition and edit the file to fix it.  After that, I had a lot of issues and reloaded almost everything except the lirc.  Once I got things back up, I had Unknow Channel on every channel.   I used phpmyadmin and repaired the tables and everything started working even the commercial skipping.  I am not sure exactly what fixed the problem because I reloaded everything except lirc.   Before I load the lirc, I wanted to try and fix an issue with using the keyboard commands to change channels.  I have never been able to change channels with one button using the keyboard.  If I use the up and down arrows, a mini one line program guide shows at the bottom of the screen and up, down, right, and left changes this guide.  I must use up, down, and then hit the enter key to actually change the channel.   I have not been able to figure out how to change channels with one button from the keyboard.   If you have any suggestions let me know.   When I get to reloading the lirc, I will let you know what problems I have.

---

### Post by NT4usB on 2007-02-18
did you try (frontend) Utilities/Setup>Setup>TV Settings>General: 
Check the box 'Change channels immediately without select'?

---

### Post by jlr4u on 2007-02-18
> **NT4usB said:**
> did you try (frontend) Utilities/Setup>Setup>TV Settings>General: 
Check the box 'Change channels immediately without select'?
Yes I checked and that setting was checked.  I have to change the channel by arrow up or down, and then hit the enter or space bar.    There should be a way to change the channels up or down with one button.  Does your mythTV change channels wiith one button?

---

### Post by NT4usB on 2007-02-19
way down deep in ...setup>tv settings>playback, there's a checkbox for always use browse mode. uncheck that.

---

### Post by jlr4u on 2007-02-20
> **NT4usB said:**
> way down deep in ...setup>tv settings>playback, there's a checkbox for always use browse mode. uncheck that.

That worked!! Thanks!

---

