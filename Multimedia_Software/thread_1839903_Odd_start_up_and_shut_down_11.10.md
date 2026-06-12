---
title: "Odd start up and shut down 11.10"
date: 2011-09-06
forum: Multimedia Software
---

### Post by the_blue_box on 2011-09-06
Hi all
I have been running Ubuntu 11.10 on my compaq presario CQ61 laptop as soon as Beta 1 was released.
But I have a bit of an odd start up and shut down.
It goes like this...

START UP
00:00 switch on
00:02 compaq screen
00:04 black screen with blinking cursor
00:09 blank purple screen
00:10 black screen with blinking cursor
00:28 black screen saying...
_* PulseAudio configgured for per-user sessions
saned disabled; edit /etc/default/saned
  *Starting web server apache2
  *Cheking battery state...          [OK]
00:29 black screen with blinking cursor
00:30 white screen
00:31 login screen



why am I getting so much "black screen with blinking cursor" and where is the lovely Ubuntu [Loading screen]("http://lunduke.com/wp-content/uploads/2010/05/10.jpg")?




SHUT DOWN
00:00 Click "shut down"
00:05 black screen saying...
... waiting

00:08 black screen saying...
... waiting          [OK]
Stopping spacenavd daemon
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
  * Stopping the winbind daemon winbind          [OK]
  * Stopping bluetooth          [OK] 
Checking for running unattended-upgrades:
  * Asking all remaining processes to terminate...          [OK]

00:20 black screen saying...
... waiting          [OK]
Stopping spacenavd daemon
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
  * Stopping the winbind daemon winbind          [OK]
  * Stopping bluetooth          [OK] 
Checking for running unattended-upgrades:
  * Asking all remaining processes to terminate...          [OK]
  * Killing all remaining processes...          [[COLOR=Red]**FAIL**[/COLOR]]
modem-manager [533]: <info>   Caught signal 15, shutting down...

nm-dispatcher.action: Caught signal 15, shutting down...
  * Deconfiguring network interfaces...          [OK]
  * Deconfiguring swap...          [OK]
  * Will now halt...

00:23 it shuts down

why am I seeing all this text and why am I seeing a "fail"?



Can anyone shed some light on this?

Regards,
[COLOR=Navy]The Blue Box[/COLOR]

---

### Post by jfm on 2011-09-09
I'm seeing the exact same thing, but have not found a solution yet. Any ideas is very much appreciated.

---

### Post by the_blue_box on 2011-09-09
I'm still in the dark about this. I'm the most concerned about "* Killing all remaining processes...          [[COLOR=Red]**FAIL**[/COLOR]]" 
I don't know why but seeing [**[COLOR=Red]FAIL[/COLOR]**] in red makes me nervous :)

---

### Post by pinta83 on 2011-10-14
My fresh ubuntu 11.10 boots up for like 5 minutes.... And on shut down it says something about caught signal 15 Failed but eventually shut's down/restart if i leave it for 5 mins......

11.04 worked like a charm.... both fresh installs :(

---

### Post by plwalsh88 on 2011-11-07
I just installed the official 64-bit 11.10 on my netbook and I'm seeing the exact same screens on start up and shut down.  However, I am also seeing the "lovely ubuntu loading screen" you attached...  

Has anyone found out anything more on this?

---

