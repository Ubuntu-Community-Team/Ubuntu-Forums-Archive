---
title: "All Tuners are Busy with frontend."
date: 2016-03-11
forum: Mythbuntu
---

### Post by Jnetty99 on 2016-03-11
I have been trying to get MythTV on a single machine as a test to see if I should move from Windows to Linux.

But every time I try to Watch TV through the MythTV Frontend I get “All tuners are busy”. 

Maybe someone could help me or give me some ideas? 

Running Ubuntu 14.04.4 64bit on a Desktop and trying to get a Hauppauge HVR-950Q working (not 955q). 

TV tuner works fine through Kaffeine. 

This is what I done now multiple times even on a couple of VM’s to see if I could find the mistake. 

Install MythTV from terminal and setup the mysql password. 
Go to /etc/mythtv/config.xml and get password. 
Open mythtv backend setup through terminal or through the Dash search. 
Usually first thing it asks me “incorrect group membership” to allow my user account to be added to mythtv group. I say yes and log out and log in as asked. 
Re-lauch mythtv backend setup. 
During setup ‘Host’ I left it as default ‘localhost’ or ‘127.0.0.1’ but made no difference. 
Type in password and finish. 
I now go through the tuner setup. Add tuner, add video source (ATSC), I scan for channels and finish and exit out. 
Asked if want to run backend I say yes. Asked to run Mythfilldatabase I say yes. 
Open MythTV Frontend from Dash or terminal. 
Click Watch and error “all tuners are busy”. 

Thank you for your time.

---

### Post by uteck on 2016-03-13
I found a thread that said it was a V4L2 device, so look for that in the source list and give it a try.
I think the source is more a reference to the type of drive to use, and not specifically the device.

---

