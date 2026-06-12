---
title: "Mythtv Set-up"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by *desk* on 2007-01-30
I'm in the process of installing Mythtv.
It's gone fine untill almost the end when I get the following info:-

 mythtv-setup must be run in order to complete MythTV installation         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; You must run mythtv-setup as the 'mythtv' user in order to complete       &#9474;  
 &#9474; mythtv configuration.  Note that this program requires an X display, so   &#9474;  
 &#9474; you must either login to an X session as the 'mythtv' user, or otherwise  &#9474;  
 &#9474; arrange for that user to have access to your X display.                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; You must complete all four steps presented in the program.                &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Once you have done this, you may start the backend by executing the       &#9474;  
 &#9474; following command as root:    

As a virtual beginner I don't fully uderstand what I'm supposed to do.
Please can you advise.
Thank you

---

### Post by kebes on 2007-01-30
I assume you've been following some sort of HOW-TO?

At some point they probably told you to create a user called "mythtv". What they are telling you to do is to now login to your desktop (Gnome?) as the user "mythtv". to do this, you would click on the "shutdown icon" (upper right in Gnome), and then select "log off". When presented with a login option, instead of picking your normal user account, login as the user "mythtv."

Once logged in, go to a terminal (Applictions > Accessories > Terminal) and run the command:
mythtv-setup

After hitting enter you should be brought into a series of configuration screens where you'll be able to enter the information about your setup/preferences.

---

### Post by *desk* on 2007-01-30
All I did was...  sudo apt-get install mythtv and it seemed to be going well.
But I don't know how to create a user called 'mythtv'.

---

### Post by dannyboy79 on 2007-01-30
follow these instructions and you'll be set! [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by majoridiot on 2007-01-30
log out and at the prompt where you normally enter your user name and password, instead login using:

user: mythtv
password: myth

then, open a terminal and run:

```
# mythtv-setup
```

and continue with the setup.

---

### Post by dannyboy79 on 2007-01-31
can't you just do su mythtv, then enter myth? that would be easier than logging out and then logging back in. or you can even just run myth-setup as mythtv by typing in su mythtv mythtv-setup, then enter your password and you'll be running the setup as mythtv instead of actually switching user's to that user.

---

### Post by *desk* on 2007-01-31
[SIZE="5"]Thank you all....I'm almost there.....but....[/SIZE]

des@deskins:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-01-31 17:50:11.764 Using runtime prefix = /usr
2007-01-31 17:50:11.786 Gnome-Screensaver support enabled
2007-01-31 17:50:11.787 DPMS is active.
2007-01-31 17:50:11.849 New DB connection, total: 1
2007-01-31 17:50:11.859 Connected to database 'mythconverg' at host: localhost
2007-01-31 17:50:11.866 Total desktop dim: 1440x900, with 1 screen[s].
2007-01-31 17:50:11.872 Using screen 0, 1440x900 at 0,0
2007-01-31 17:50:12.096 Current Schema Version: 1160
2007-01-31 17:50:12.097 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-01-31 17:50:12.097 Enabled verbose msgs:  important general
X Error: BadValue (integer parameter out of range for operation) 2
  Major opcode:  153
  Minor opcode:  2
  Resource id:  0x81ab
DisplaResX: XRRSetScreenConfigAndRate() call failed.
2007-01-31 17:50:12.788 SwitchToGUI: xrandr failed for 1440 x 900
2007-01-31 17:50:12.788 Total desktop dim: 1440x900, with 1 screen[s].
2007-01-31 17:50:12.790 Using screen 0, 1440x900 at 0,0
2007-01-31 17:50:12.792 Switching to square mode (blue)
libGL warning: 3D driver claims to not support visual 0x4b
2007-01-31 17:50:12.915 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-01-31 17:50:14.424 Joystick disabled.
2007-01-31 17:50:14.785 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-01-31 17:50:15.498 Registering Internal as a media playback plugin.
2007-01-31 17:50:18.045 Using NV NPOT texture extension
2007-01-31 17:50:38.926 New DB connection, total: 2
2007-01-31 17:50:38.927 Connected to database 'mythconverg' at host: localhost
2007-01-31 17:50:39.003 Connecting to backend server: localhost:6543 (try 1 of 1)
2007-01-31 17:50:39.004 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-01-31 17:50:44.667 TV: Attempting to change from None to None
2007-01-31 17:50:47.606 Connecting to backend server: localhost:6543 (try 1 of 1)
2007-01-31 17:50:47.606 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
des@deskins:~$ 

[SIZE="4"]I also get an error message :-
"Could not connect to the master backend server--Is it running?
Is the IP address set for it in the set-up program correct?"[/SIZE]

---

### Post by majoridiot on 2007-01-31
if you are running the frontend and backend on the same machine, make sure the backend
server address is set to 127.0.0.1 in both the frontend and backend setup.  if they are running 
on seperate machines connected through a router, you can discover the local address of the 
backend by:

```
# iwconfig
```

and looking for the address on the network connection you are using... eth0, etc.

---

### Post by kebes on 2007-01-31
Also, make sure the backend is running! On a commandline, go:

pgrep myth -l

You should see something like:
4460 mythbackend

If you don't see "mythbackend" listed, then you need to first start it by going:
mythbackend &

(The "&" puts it into the background, and is optional. If you don't put it there then you'll see the output from the backend server and you'll need to use another terminal to try "mythfrontend" again.)


Once you have the backend/frontend working, you can set "mythbackend" to start on boot, and "mythfrontend" to start at login time (if that's what you want).

---

### Post by kebes on 2007-01-31
> **majoridiot said:**
> # iwconfig

Note that "iwconfig" is for wireless connections. If you're using an ethernet connection, the commandline "ifconfig" is what you want instead.

---

### Post by majoridiot on 2007-01-31
> **kebes said:**
> Note that "iwconfig" is for wireless connections. If you're using an ethernet connection, the commandline "ifconfig" is what you want instead.

hehe... correct.  typo.

---

### Post by *desk* on 2007-01-31
[SIZE="5"]Sorry, but I don't understand what this means:-[/SIZE]

des@deskins:~$ sudo pgrep myth -l
des@deskins:~$ mythbackend &
[1] 15778
des@deskins:~$ 2007-01-31 20:25:02.489 Using runtime prefix = /usr
2007-01-31 20:25:02.552 New DB connection, total: 1
2007-01-31 20:25:02.562 Connected to database 'mythconverg' at host: localhost
2007-01-31 20:25:02.571 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

---

### Post by kebes on 2007-01-31
I believe mythbackend is saying that you need to configure MythTV. So you need to run:

mythtv-setup

This will launch a config program where you have the option to enter all the parameters for your setup. Once you're done with that, close it, and then try starting mythbackend and then mythfrontend.


P.S.: If you're following one of the how-to's, it would help to tell us which one and which step you are at. That is, which steps worked and which step you tried but didn't work.

---

### Post by *desk* on 2007-01-31
To be honest Kebes  I've tried so many things I have lost track on what I've done and what I haven't......This is from your latest suggestion..........should I scrap it and try again?

des@deskins:~$ sudo mythtv-setup
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-01-31 20:51:27.518 Using runtime prefix = /usr
2007-01-31 20:51:27.533 DPMS is active.
2007-01-31 20:51:27.594 New DB connection, total: 1
2007-01-31 20:51:27.604 Connected to database 'mythconverg' at host: localhost
2007-01-31 20:51:27.609 Total desktop dim: 1440x900, with 1 screen[s].
2007-01-31 20:51:27.615 Using screen 0, 1440x900 at 0,0
2007-01-31 20:51:27.844 Current Schema Version: 1160
DisplaResX: XRRSetScreenConfigAndRate() call failed.
2007-01-31 20:51:27.881 SwitchToGUI: xrandr failed for 1440 x 900
2007-01-31 20:51:27.882 Total desktop dim: 1440x900, with 1 screen[s].
2007-01-31 20:51:27.884 Using screen 0, 1440x900 at 0,0
2007-01-31 20:51:27.887 Switching to square mode (G.A.N.T.)
libGL warning: 3D driver claims to not support visual 0x4b
2007-01-31 20:51:28.006 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-01-31 20:51:29.242 Joystick disabled.
2007-01-31 20:51:29.961 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-01-31 20:51:30.302 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-01-31 20:51:47.569 RecordFilePrefix is not set?
des@deskins:~$

---

### Post by kebes on 2007-01-31
Quick question: are you running this from a terminal program inside Gnome, or are you running this in a "pure tty" (like a ssh login or a virtual terminal or whatever).

The reason I ask is because the "mythtv-setup" program is a GUI (graphical) setup utility, so you need to run it from inside Gnome (or KDE). So in your desktop environment you open a terminal (Applications > Accessories > Terminal) and type "mythtv-setup" and hit enter.


If the above is exactly what you've done, then does the mythtv-setup GUI appear on screen at all? The error codes from your last post suggest that it can't attach to the display properly.

---

### Post by *desk* on 2007-01-31
Yes I'm using the desktop terminal and run....mythtv-setup....I get a background only.

When I run from Applications < Sound & Video  <MythTV Frontend....I get the complete GUI. It only keeps reminding me that it can't connect to the Master Backend Server and asking if the IP address is set up correctly.

---

### Post by kebes on 2007-01-31
Try running "mythtv-setup" without using "sudo".

Also, did you end up creating a user "mythtv" on your system? Did you install mythtv as that user, or as user "des"? You could try logging in as that user, and then running "mythtv-setup", and see if that works.

(Again I'm not exactly sure what you've done so far...)

---

### Post by *desk* on 2007-01-31
Without Sudo....no change.
I couldn't log in using Mythtv.

I'm sorry Kebes, I don't know what I've done.

---

### Post by *desk* on 2007-01-31
Hi Kebes
I'm sorry I have given you some false information.
It is running with setup.
Thr GUI holds the background for about 12 seconds before it carries on....I wasn't patient.
I don't know if all is well now but I'll let you know.
Thank you.

---

### Post by Daminator on 2007-02-03
I'm having pretty much the exact same problems. I think there must be something wrong with the ubuntu guide we followed.
I'fe tried loads to patch it up, but not getting anywhere fast.

---

### Post by fenian on 2007-02-03
Mythtv creates the mythtv user automatically.To set the mythtv user password,login as the main user and type in a terminal
> 
sudo passwd mythtv
enter the password you want for the mythtv user when prompted.Then you need to edit the group file so run
> sudo gedit /etc/group
in the file that pops up add ",mythtv"(without the quotes) to the line that starts with "admin" do the same for the lines that start with "plugdev" and "cdrom".
Log out and log back in as mythtv with the password you just made.Do not start mythbackend it cannot be running when you run mythtv-setup.
In a terminal run
> mythtv-setup
just like that no sudo.After you set all your settings run
> /etc/cron.daily/mythtv-backend
it will take some time to download all the program guide (5+minutes).Then type
> sudo /etc/init.d/mythtv-backend restart
test to see if it's running with
> ps -p `cat /var/run/mythtv/mythbackend.pid`
it wil give you output like
>   PID TTY          TIME CMD
30711 ?        00:00:00 mythbackend
then run
> mythfrontend

---

### Post by Daminator on 2007-02-03
Ok, I went through that. Breaks down in two places for me.

$ /etc/cron.daily/mythtv-backend
Password:
nice: tv_grab_uk_rt: No such file or directory
Error in 1:1: unexpected end of file


and


$ ps -p 'cat /var/run/mythtv/mythbackend.pid'
ERROR: Process ID list syntax error.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty 
etc....

Damian

---

### Post by fenian on 2007-02-03
I think the second error is because mythbackend never started up.The first error has to do with xmltv,I think that the tv_grab_uk file need to go in the /usr/bin directory.I don't really know xmltv but there is some info here...
[http://www.mythtv.org/wiki/index.php/Uk_xmltv](http://www.mythtv.org/wiki/index.php/Uk_xmltv)

---

### Post by nattugglan on 2007-05-03
Hi guys.

I've been following the "MythTV Feisty Backend Frontend Desktop" guide @ [help.ubuntu.com]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop") from scratch.

**Has anyone gotten MythTV working without problems after following this guide?**
I've had a long row of different error messages and weird things.

I will start over from scratch again, but I'll list some of the problems and error messages I've gotten.:

The first thing that doesn't work is channel scanning in MythTV (I have a Hauppauge WinTV-Nova-T-500). This might be related to the bug in the Feisty 2.6.20 kernel.
Scanning channels with dvb-utils, however, worked - and I was able to get the channels into MythTV by manually importing the channels from the channels.conf file I created using dvb-utils.

Message from syslogd@mybox:
```
kernel: [ 5058.399119] Oops: 0002 [#1]
```
- A bug related to the Hauppauge card.

When checking if the backend was running I didn't get the expected output. I got this:
```
$ ps -p 'cat /var/run/mythtv/mythbackend.pid'
ERROR: Process ID list syntax error.
```

However, restarting the MythTV backend seemed to work OK (no error messages were displayed).
```
$ sudo /etc/init.d/mythtv-backend restart
```

The following message appeared in the mythbackend.log.
```
2007-05-01 17:53:16.572 Database Schema upgrade complete, unlocking.
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
```

When running sudo mythfilldatabase --manual:
```
Connected to database 'mythconverg' at host: 192.168.1.11
Can't use an undefined value as an ARRAY reference at /usr/bin/tv_grab_se_swedb line 174.
```

Another message related to the master backend/IP address:
```
Could not connect to the master backend server -- is it running?
Is the IP address set for it in the setup program correct?
```

The IP number was configured correctly however (per the instructions in the guide).

I was surprised to get so many problems after following the guide.
One really surprising result was the permissions on the recorded (and timeshifted) files (and the folders). When following the guide one creates a normal user. When starting configuring MythTV this user gets added to the MythTV group, but the user will not have full permissions to the recorded files.

Right now, the behavior of MythTV has for some reason changed after the box was off during the night. Now whenever I try to start the MythTV frontend it displays the initial screen to choose the preffered language. This screen was not shown the first time I started the frontend! But now, for some reason, it is shown. After that the following message is displayed on the following screen:
```
Myth could not connect to the database. Please verify your database set
```
..tings. - I imagine it should read (the message gets truncated).
The settings are all fine (IP, name, password..), but after choosing finish the frontend doesn't start - and when trying again the language screen is shown again.

I will try again, from scratch, but..

nattugglan

---

### Post by Titus A Duxass on 2007-05-03
I have never followed the How-To for a combined Backend/frontend/Desktop setup but I have followed the stand alone backend/frontend How-To and have no problems. I believe that both were written by SuperM1, so if one works the other one should.

I sometimes take two or three runs to get used to the install process and to achieve success.

It looks like most of your problems are Backend related, make sure that you carry out the mythtv-setup process correctly.

Which user are you logged in as when you do mythtv-setup?

Are you starting with a clean install?

---

