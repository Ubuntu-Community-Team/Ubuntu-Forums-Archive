---
title: "can an xbox 360 stream video from linux?"
date: 2009-01-29
forum: Multimedia Software
---

### Post by hexdsl on 2009-01-29
there are alot of threads on this forum talking about streaming video to an xbox, however most are dated at a time when the 360 did not support AVI files inside the dash.

when i have windows XP installed (AND Windows media player 11) i can go to my 360, select a video file and watch it, right there no problems.

now i have linux installed and dont wasnt to use windows any more i have worked hard getting my games working and setting up my desktop so my family can use it with little problems, now they want more :( they want to watch my AVI files on the xobx like they did last month when i was using XP... please help.


I am currently trying to make this work with media tomb as a forum pointed me at that as an option, little success so far.

i am using n Ubuntu 8.10 - the Intrepid Ibex - released in October 2008, i have applied ALL updates the system has offered me.

i can play ALL the video files in question on my PC, no issues this end, the problem is the console end..

what software should i be using? is there a definitive answer for this yet? 

thanks for any interest guys, i doubt i am alone on this one.

---

### Post by nealien on 2009-01-30
i am using ushare.  you can install from synaptic by searching ushare.  you will have to edit the conf file to get it to work.  i have mine working but my xbox can't see any media cus i have my music installed on an extra hard drive with an ntfs partition.  i'm not quite sure what to write in as the directory of my media so it doesn't see anything.  


still waiting for a reply on that one.  but this should fix u up.  just copy slowspeeds conf file in this thread.

[http://ubuntuforums.org/showthread.php?p=6643052#post6643052](http://ubuntuforums.org/showthread.php?p=6643052#post6643052)

---

### Post by hexdsl on 2009-01-30
thanks, looking into it today :)

---

### Post by hexdsl on 2009-01-30
got ushare installed and setup with the CONF file but my 360 cant see it 
still

---

### Post by hexdsl on 2009-01-30
after a reset and some .conf editing i have it working for video PERFECTLY! but the audio (mp3) files still dont show up. hummmmm................

---

### Post by falken78 on 2009-02-12
This is something I am interested in also - I got my Ubuntu (8.10) woring well with Fuppes Upnp mediaserver. Meaning that I can see movies, pictures and my music. (My tip to all of you who like to try fuppes is to install it then grab the example conf files from the fuppes forum).

BUT - my issue then... Fuppes uses an index (as many other upnp clients I guess) meaning this index needs to be updated when a file is added... This I think fuppes does automaticlly, but since you have to use Virtual folders also to get things presented in a OK way on the xbox 360 this does not matter - meaning I still need to "press" update on fuppes virtualfolders everytime a file is added... 

Anyone got around this issue? ( I am open to changeing from fuppes.... to another solution).

Also I only index my movies since with it takes to long to update the virtualfolders with all pictures and all music every time a file is added....

---

### Post by ouija on 2009-02-12
> **falken78 said:**
> BUT - my issue then... Fuppes uses an index (as many other upnp clients I guess) meaning this index needs to be updated when a file is added... This I think fuppes does automaticlly, but since you have to use Virtual folders also to get things presented in a OK way on the xbox 360 this does not matter - meaning I still need to "press" update on fuppes virtualfolders everytime a file is added... 

Anyone got around this issue? ( I am open to changeing from fuppes.... to another solution).

Also I only index my movies since with it takes to long to update the virtualfolders with all pictures and all music every time a file is added....

I've created a script to that address this very issue.

**I used these for Fuppes SVN-r578 on Ubuntu Hardy amd64 version without issues.**

First off, the "rebuildfuppes.sh" script will rebuild your fuppes library when it is executed.  It can automatically detect your network interface and IP address, **but the port needs to be specified in the script itself to which port fuppes is using** (you can configure this by editing the script with any text editor and reading the instructions at the top of the file)  It is set to use the default value of course, which is port 5080, but this will need to be adjusted to match your fuppes configuation if different.

Then, just give the script execution privileges and copy it to the "/etc/cron.hourly" folder, and then the fuppes library should automatically be rebuilt ever hour [I](providing fuppes is running and the port is correctly configured, not to mention that your crontab file is correctly configured to run crons properly -- which is should be by default unless you have previously edited it)
[/I]
This has the same effect as browsing to the options page on the fuppes server and clicking the update database link / create virtual container each hour on the hour. 

Now this isn't going to speed up the process of indexing your files, but it should help in that it will cause fuppes to update in the background automatically every hour.

If you happen to find that updating every hour isn't ofter enough, or say you recently added a file that you want to access immediately, then you can simply run the script from the terminal (while fuppes in loaded) or you can login to the fuppes server address and manually update that way.

Let me know if you run into any issues using this script, and I'll do my best to help you out. :)

---

### Post by ouija on 2009-02-12
**AUTO-LOAD FUPPES ON SYSTEM START SCRIPT**

I've created another useful script that aids in the use of Fuppes under Ubuntu (Hardy amd64 but I'm sure it'll work for other flavors as well) which address an issue regarding startup and especially wireless networks.  

Normally, you could simply create an entry to have fuppes load upon startup in Ubuntu (under 'System-Preferences-Sessions') but if your network doesn't connect immediately or if it takes time to connect, then fuppes fails to load because there is no active connection detected.

The way this script addresses this issue is that once executed, it will look for a network connection EVERY 5 SECONDS for the FIRST MINUTE that the script is running, and then it will check for an active connection thereout every MINUTE for a 5 MINUTE PERIOD -- meaning that if no active network connection or IP is detected within the first 6 minutes that your operating system is loaded, then fuppes WILL NOT START! Otherwise, it should run fine.

Simply give this script execution privileges and copy the file to the "/bin" folder of your system and then under the "SYSTEM -> PREFERENCES -> SESSIONS" menu, add an entry under the "Startup Programs" tab and point to the script in your bin folder in the "command" field. (see attached screen shot) and ensure it is enabled and voila -- fuppes on startup!

[[IMG]http://img4.imageshack.us/img4/351/screenshotvc0.png[/IMG]](http://imageshack.us)
[[IMG]http://img4.imageshack.us/img4/screenshotvc0.png/1/w507.png[/IMG]](http://g.imageshack.us/img4/screenshotvc0.png/1/)

[COLOR="Red"]**UPDATE:**[/COLOR] Please note that if any of the attached scripts are NOT working (ie: they fail to launch in the terminal even after granting them execution privileges) then simply open the scripts in a text editor and copy and paste the entire thing to a new file, save it to your desktop or whereever and then try granting execution privileges and copying to the specified folder (I believe this to be an issue in the way this forum treats attachments)

---

### Post by mediccby on 2009-02-13
Ok I am kinda new to this Ubuntu stuff. Here is what I am trying to do. I have a fresh install of Ubuntu 8.10. And I am wanting to use ushare to stream Videos to my Xbox 360. I also want to set up a FTP server so that I can Download/Up to my file that will hold my movies and music. I also want to host a web site so that I can stream my movies does any one have any ideas on how to do this and what I need to do to make it work? Any links to any guides would be helpful. Should I work with a GUI or not I did not Install a GUI.

---

### Post by ouija on 2009-02-13
> **mediccby said:**
> Ok I am kinda new to this Ubuntu stuff. Here is what I am trying to do. I have a fresh install of Ubuntu 8.10. And I am wanting to use ushare to stream Videos to my Xbox 360. I also want to set up a FTP server so that I can Download/Up to my file that will hold my movies and music. I also want to host a web site so that I can stream my movies does any one have any ideas on how to do this and what I need to do to make it work? Any links to any guides would be helpful. Should I work with a GUI or not I did not Install a GUI.

For an FTP and/or website, you can simply get a NAS device and easily set something like this up, without needing to run anything but a router with your internet and the drive.

One that I recently purchased is the 2TB GigaNAS by MRT found here: 
[http://www.mrt-communication.com/35HD-DUAL-NAS-E.htm](http://www.mrt-communication.com/35HD-DUAL-NAS-E.htm)

Hell, you can even use a USB memory stick and simply buy this: [http://www.mrt-communication.com/WANSER-R.htm](http://www.mrt-communication.com/WANSER-R.htm) :p

---

