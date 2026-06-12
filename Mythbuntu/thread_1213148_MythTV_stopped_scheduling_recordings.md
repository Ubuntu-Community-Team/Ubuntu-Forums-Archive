---
title: "MythTV stopped scheduling recordings"
date: 2009-07-14
forum: Mythbuntu
---

### Post by killcast on 2009-07-14
Ok, so a series of weird events which may or may not be related.  I run a Mythbuntu frontend and backend on separate computers.  Both systems have worked fine for months now, both with 8.10 installed on them.  I was watching a recording over the weekend when it suddenly stopped playing and MythFrontend closed.  The computer was unresponsive, causing me to reboot.  When it rebooted, it kept saying it couldn't detect a backend server.  It asked for server information, but wouldn't actually save any of the values I was entering.  Checking phpMyAdmin revealed that apache wasn't recognizing PHP files anymore, and trying to log into mysql from the Terminal revealed that mysql couldn't connect anymore (It was saying something how it couldn't connect on some sort of .sock file).  Using apt-get I reinstalled apache and mysql, and everything worked fine on my frontend.

However, the last (and most bizarre) problem involves my backend no longer being able to schedule recordings.  I've tried scheduling recordings from my frontend, MythWeb (on my backend), and then just running Myth FrontEnd on my backend server.  In MythWeb it will show me all of the programs I have setup to regularly record, but nothing in "Upcoming Recordings".  If I go into my program listings and set any program to record, it doesn't actually save the changes.  It doesn't give me an error or anything, but if I hit "Save Settings" and then return to that listing later, it will still be set to "Do not record this program".

The weird part is that I can see there's a table in mythconverg called "record", and it's populated with all of the programming that it should be set to record.  If I go into the program guide and select a random program to record, it will insert it into the "record" table, but nothing shows up in the "Upcoming Recordings" page.  I still have my program guide filled up with channel info, so I'm assuming mythfilldatabase is still working.  I checked to make sure that the "mythtv" MySQL username still had all of it's privileges, and that seems to check out.

I'm not incredibly well-versed in Linux, and therefore I really haven't made many changes to either of my boxes.  I keep them both updated whenever updates are offered, which is really the only change I can think may have happened.

Any help would be greatly appreciated.

---

### Post by newlinux on 2009-07-14
My first guess is something is wrong with your tuners. In this case it will setup recording rules, but won't actually record anything or list any upcoming recordings because no tuners are available to do the recording. Have you checked your backend logs? What does mythweb or the status screen in mythfrontend say about the availability of your tuners? Can you give us details on your hardware, like what tuners you are using?

I actually rarely update my backend after they are stable. Seen way too many things go wrong... and I don't feel like troubleshooting all the time.

---

### Post by killcast on 2009-07-14
Thanks for the quick response - I'll be home from work in an hour or so and post a more detailed reply.  Unavailable tuner is hopefully easy enough to fix.

---

### Post by killcast on 2009-07-14
UGH, yes, that's all it was.  I have the Hauppauge HVR-1600, and I guess the last update erased the driver info.  I re-installed the drivers from here:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Drivers]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Drivers")

And it worked fine.

I was all keyed up over losing MySQL on the one computer, I didn't stop to look outside of that scope of DB error.  Just glad I didn't do anything drastic like reinstall or something.  Thanks a bunch for the help.

---

### Post by newlinux on 2009-07-14
Yeah, you will probably need to repeat those steps anytime there is a kernel update. Glad you got the problem fixed easily.

---

