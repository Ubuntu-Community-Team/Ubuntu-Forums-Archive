---
title: "Zoneminder on Lucid Howto"
date: 2010-07-21
forum: Multimedia Software
---

### Post by wyliecoyoteuk on 2010-07-21
Noticed a lot of questions about this, couldn't easily find a simple  answer ( a lot of them were far too involved)

So I am posting this in the hope that it will help.

Install zoneminder from the repositories.
Apache and MySQL will also be installed, if they are not already.
It will ask you for a MySQL root username and  password DO NOT FORGET THIS.

Add a link in the apache (webserver) config directory

  $ sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf

If apache is not running, start it

$ sudo /etc/init.d/apache2 start

If apache is already running, restart it

           $ sudo /etc/init.d/apache2 force-reload



setup zm

           $ sudo chmod 4755 /usr/bin/zmfix

           $ zmfix -a

           $ sudo adduser www-data video



Shared memory settings need to be chnaged for ZoneMinder 

$ sudo nano /etc/sysctl.conf

add this at bottom (128 MB) 

kernel.shmall = 134217728 kernel.shmmax = 134217728

save and exit.

TEST [http://localhost/zm](http://localhost/zm)  should open Zoneminder screen. 
Default user=admin password=admin

Good luck:)

(Thanks to the various posts that I garnered this from)

I am running this on my Mythbuntu install, but it should work for Standard Ubuntu too.

---

### Post by Tomy on 2011-02-01
Thanks, that was easy.

I'm running Ubuntu 10.10 Maverick and this HowTo worked perfectly.

---

### Post by wyliecoyoteuk on 2011-02-02
Glad to be of help :)

---

### Post by wyliecoyoteuk on 2011-02-08
Just updated Mythbuntu to 10.10, had to redo the shared memory entry in sysctrl, but it still works fine.

---

### Post by wkulecz on 2011-02-09
Thanks great starting pont.

Two quick questions.

I didn't get a password prompt for the initial setup login and can't seem to monitor the image from my camera. (edit:  doh! after I closed the monitor setup window, clicking the "name" "Monitor-1 opened the watch window.)


How do I configure it to activate the X10 interface?  The X10 tab in the Monitor setup window is missing.

---

### Post by wyliecoyoteuk on 2011-02-09
Sorry, no idea about X10, I don't have any X10 devices.
I would start at the X10 tab in the options screen

Edit, click on "options" on the left hand side of the screen, then enable x10 in the x10 tab.
You can then configure it in the monitor setup.

---

### Post by wkulecz on 2011-02-14
There was an checkbox option in console->options window to enable X10 support which made the X10 tab appear on the device setup window.  Unfortunatley seems X10 support is broken in this version -- found a blurb about it with possible workaround here:
[http://www.zoneminder.com/forums/viewtopic.php?t=15792](http://www.zoneminder.com/forums/viewtopic.php?t=15792) but for now I've dsabled X10 support again.

Unfortunatley I've bigger problems, while zoneminder seems to work great once I figured out how to configure it, it has locked up three times since Saturday, worst was this morning when the whole system was dead -- not even a caps lock LED toggle.  Had to powercycle to reboot :(   Up to now this system has not been down except for power outages and reboot required updates since I installed it in April 2010 so I have to suspect either zoneminder or the no reboot required updates that waited for me on Saturday.

Its a quard core file server with 8GB of RAM and letting it do the video security system makes a lot of sense.  I had a dedicated Windows based DVR video security system that has been more reliable than the power company (as long as I remembered to reboot it every 45 days) untill it died when we had a "rolling blackout" during last weeks cold snap.  Both these systems are on APC UPSes and stay up for 20-30 minutes after the power goes down so short interruptions cause no outages.

If zoneminder keeps crashing I'll need to buy another windows box or dedicated DVR video system this week :(

How is zoneminder working for you?

---

### Post by wyliecoyoteuk on 2011-02-14
I run Zoneminder on an Athlon 4850e with 2GB of ram.It also runs MythTV, with no trouble.

I remember having similar problems with the driver for my UVC camera, until I switched off verbose mode, it kept filling /var/logs with error messages, to the extent that my root partition filled up.
I redirected the log file to /dev/null until I could figure it out.

---

### Post by wkulecz on 2011-02-15
I turned off all the logging, statistics, and debugging & X10 stuff I could find.  It has stayed up for 24 hours since the bad crash/lockup.  Mine's a quad core,  I suspect there might be issues with "true parallism" in the controlling scripts when changing things to figure out what modes best meet my needs.  I also doubled the intervals at which the various perl scripts are run when I could find such an option.

I've three video cards and six cameras, but over 1.5TB free space on the root partition.

So far its totally immune to false alarms compared to my old system, but its got to be more reliable than the power company to be useful.  TIme will tell.  I also like getting Emailed video clips instead of five or six still.

Where are the video clips it Emails stored?  I can't seem to find them.  I'm a little unclear on the "archive" feature, but I doubt I want to archive anything.  I made a filter to delete events older than 1-day and it seems to work, eventually I'd make this maybe a week or two, no need to save anything more than that.

---

### Post by wyliecoyoteuk on 2011-02-15
I would look on the Zoneminder Wiki and forums.
I am not really a Zoneminder expert, just posted this to help some people struggling to make sense of the basic install, as there seemed a lot of conflicting information, when setting it up was really pretty straightforward.

---

### Post by wkulecz on 2011-02-16
The Zoneminder Wiki is pretty poor.  Its not yet updated for the version of Zoneminder in the repo (1.24.2).  Its trivial to find stuff that is just plain wrong -- perldoc ZoneMinder::SharedMem fer instance.

This is not helpful to folks trying to figure things out for the first time.

Also important stuff is in the FAQ that is not in the "Documentation" section at all.

The Zoneminder forum mixes all 1.24.x questions together from all distributions and installation options which makes it hard to tell what is relavent to what I've installed.

I had looked at zoneminder when the Mandrake liveCD version was mostly current, and saw potential.  Now that potential, while mostly realized, is greatly held back by poor and conflicting documentation.

Only time will tell if it will be reliable, but I do like what I have working so far.

I'm hoping the stability problems I had were from changing the config and then quickly generating alarms with a camera on my desk to get an idea of how all the settings interacted to get the motion detection setup -- I may have been going too fast to let are the interacting scripts complete to a fully stable state between starts, stops, and alarms.

So far its working fine since that horrid, worst Ubuntu lockup ever, I awoke to Monday morning.  Just got a video alert, seems that darn mud dauber is trying to build a nest behind my outdoor camera again! Looks like a cheasy 1950's scifi monster. :)

---

### Post by KEBDARGE on 2011-05-20
looks like what I am looking for!

Can someone confirm if this walkthrough will also get zoneminder running on 11.04?
Or did some things change?

I followed most of the steps.
But two things went wrong:

1) I did forget the MySQL root username and password so I deleted the zm table from the MYSQL database
2) I am unsure if I entered the 'Shared memory settings' at the right place in the file...

Hence, when checking [http://localhost/zm](http://localhost/zm) nothing works...

thnx for any help on this!

---

### Post by wyliecoyoteuk on 2011-05-21
If the shared memory setting is wrong, that will not stop the web page opening, it will just stop the cameras working.
If there is nothing on localhost/zm, you need to check that Apache is running and the symlinks are in the right place.
I am running it on 11.04 with no problems.
ZM needs the database to run, so it might be worth uninstalling it and starting again.

---

### Post by wkulecz on 2011-06-17
Followup.

I've found Zonemider to be sometimes unstable when changing configuration settings -- forcing several reboots to clear lockups.  But once I managed to get it configured to meet my needs, its been rock solid and has worked very well.

---

### Post by wyliecoyoteuk on 2011-06-17
I think that it is just very slow sometimes in applying settings, waiting for a process to finish. If you restart the service using the buttons on the webpage, you don't need to reboot.

---

### Post by wyliecoyoteuk on 2011-12-13
Just installed Zoneminder on Ubuntu 11.10 server, and the shared memory settings are no longer needed. 1.24.4 has mapped memory by default, which doesn't need the shmall and shmmax settings.

---

### Post by wyliecoyoteuk on 2012-06-09
Just moved this to 12.04, no changes

---

