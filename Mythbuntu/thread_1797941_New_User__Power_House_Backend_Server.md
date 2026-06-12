---
title: "New User / Power House Backend Server"
date: 2011-07-05
forum: Mythbuntu
---

### Post by boreese on 2011-07-05
I just discovered Mythbuntu over the last few days and have decided to build a backend server first. The frontend system/s look easy....
 
While I have the system built, there is an issue I cannot resolve.
When the system boots, the Mythbuntu screen appears with 4 or 5 red dots under it.
Never goes beyond this screen but the drives are busy..
 
Is this because there are no video capture cards in it?
The CTRL-ALT-F keys do not work.. The Myth Web site does work...
 
The system is / will be
Dell PowerEdge 2600
Dual 2.4 512K 80532K Processors
1 gig ECC memory (looking to go to 4 or 8 gig)
1 gig network
Raid5 Boot (6 147gig scsi drives (1 hotspare, 5 for Raid / Data)
 
If all goes well with the system I will be adding a pair of 1.6T chapparel's in a Raid5 configuration.
 
Some might call is over kill, I call it fast and redundant....
 
Any ideas on why I do not get the desktop?

---

### Post by boreese on 2011-07-06
Just ordered
Hauppauge 1199 WinTV HVR-1600 Internal PCI Dual TV Tuner/Video Recorder with IR Receiver and Blaster
 
Is there anyone that can help me with my configuration issues?

---

### Post by klc5555 on 2011-07-06
The "power house" aspect is best dedicated to the frontend. It takes a reasonable amount of CPU horsepower (and especially a decent or better NVidia video card --ATI is much less-well supported) to smoothly display HD video and such. 

The backend's requirements are actually quite modest, though obviously the more disk storage space for recordings the better. Preferably on drives/partitions that do not have the OS on them. In case at some point you need to wipe/reinstall the OS, your recordings will reman safe. Make frequent backups of the database, and store a copy wherever the bulk of your recordings are kept. If your recordings are safe during an OS meltdown, then their metadata should be kept safe as well.

The Hauppauge 1600's configuration information with mythtv (a bit out-of-date) may be found here: [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

The linuxtv.org info for the card may be found here: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)

Your older 1199 model of the 1600 may have product code "74031" [not the same as the brand-new "74301", which requires a patch to the cx18 driver] stamped on the tuner. This product code "74031" the wiki indicates does not support QAM. Pay no attention to this --it appears to be a Windows-specific issue. I have a model 74031, and also for good measure a 74551: they both do QAM perfectly on Linux with reasonably current drivers (i.e. around August 2010 or later).  

Can't help you with the lirc remote-control configuration for the 1600 card --I gave up on it and began using an IguanaIR transponder, which is a bit quirky on Ubuntu though it works flawless on, for example, Slackware.

For most of your mythtv-specific configuration needs, consult the wiki: [http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)   
particularly the user manual for configuration details.

---

### Post by David Grigor on 2011-07-06
I see no reason to go beyond 2g memory for a dedicated machine.  With frontend & backend running and transcoding at the same time, still never see close to 2g used. Usually closer to the 600m-700m range.

I personally never felt the need to Raid the OS drive. I can rebuild it from scratch pretty quickly as long as sql backup is stored elsewhere.  Raid the media drives could be worth it though.

---

### Post by boreese on 2011-07-07
Thank you everyone for the response / answers.
 
The biggest question I had was, does the backend server (not a combo system) require the capture card there-by then giving me the desktop I am looking for?
 
 
The reasion for the power on the backend server is bcause I plan to install 3 input cards (if the first one works as it should) and 3 output cards.
 
While not knowing this OS, I like the idea of large amounts of ECC memory in a server setup. While the server motherboard will handle the ECC and memory issues (if there ever is one), I do not like the idea of memory going bad and having the system fall to its knees untill I can get to it.
 
The current raid5 boot is for testing.... The other side is if a drive does fail, I do not have to rebuild.... The raid will pull the hotspare and all I have to worry about is replacing the dead drive...

---

### Post by klc5555 on 2011-07-07
> **boreese said:**
> 

The biggest question I had was, does the backend server (not a combo system) require the capture card there-by then giving me the desktop I am looking for?
 
 
The reasion for the power on the backend server is bcause I plan to install 3 input cards (if the first one works as it should) and 3 output cards.
 


I'm not sure I can parse your question correctly. But I can say that the backend owns and runs the tuner cards. Also the database and associated scheduling. A backend-only system doesn't even need X beyond configuring the backend itself, which can't be done in text mode. It doesn't need much memory beyond the OS requirements --say 1.0-1.5 Gb. And for recording HD (not playback, of course) just about any CPU available over the last 10 years will work fine. If you use the analog side of your HVR-1600, it will require more CPU horsepower to encode an analog stream (despite hardware encoding) than will be required to record an HD or SD digital stream. 

What the backend needs is fast read/write to disk and plenty of hard disk space. HD broadcasting moves about 6.6 Gb per hour onto your disks (2.2Gb/hr for analog, 1Gb/hr for SD). You start getting 2 or 3 HD streams going simultaneously, and you'll probably be happier if mythtv is not trying to put them all onto the same disk at the same time. Also with several HD streams coming in, you could end up moving an awful lot of data for the old-fashioned PCI bus. You can alternatively have multiple networked backend machines: my usual setup uses 3 backends, each with 2 (in one case 3) tuner cards and I avoid recording more than 2 simultaneous HD streams on a backend.

I'm not sure what you mean by "3 output cards".


But as far as CPU horsepower and massive amounts of memory, the only reason you'd possibly need this on a backend-only myth machine is if you were using the machine as a normal desktop or workstation while running its mythtv backend functions in the background. Otherwise, the CPU horsepower should go wherever the HD recordings are being displayed. If the machine is a combined backend/frontend, then it needs the CPU/GPU horsepower for its frontend functions. But even here, main memory beyond 4 Gb is likely wasted.

---

### Post by boreese on 2011-07-08
I received the new capture card yesterday and installed it.
I also did a fresh install of MythBuntu.
 
Still only getting the Mythbuntu name on the system screen with 5 red dots.
None of the F key terminals work.... They did durring the install.
 
It is installed as a backend server... no frontend
When I log into the mythweb site on the machine, I see:
 
**[COLOR=#dedede][FONT=Arial]No TV Configured[/FONT][/COLOR]**

[COLOR=#dedede][FONT=Arial]MythTV is intended to run with TV settings configured. Your installation does not appear to have been fully configured for TV viewing (there are no channels). If you intend to use MythTV's TV functionality, please finish configuration via mythtv-setup before using MythWeb. [/FONT][/COLOR]
[COLOR=#dedede][FONT=Arial]MythWeb is capable of functioning without TV settings, but so much of its interface is designed to make the TV process as smooth as possible that you will likely find many nonfunctional links to TV functionality. Don't be surprised to find "unknown module" messages when you follow links. [/FONT][/COLOR]
 
MythTV-setup?
All I get is mythweb.

---

### Post by klc5555 on 2011-07-08
Well, clearly the machine boots, or you wouldn't get the mythweb http server. I'm surprised that you're getting mythweb, since on a normal boot Network Manager shouldn't start up networking on a Ubuntu machine until after X starts and the desktop loads.

Don't know why you're not seeing a desktop. It could be an X or display driver issue.  But the forum members will need some actual information:  what version of mythbuntu you're trying to configure, what display adapter the machine has, what display driver you loaded during the install, what sort of information dmesg and the logs (like syslog and the usual Xorg logs (under /var/log/) are giving you during the startup. That sort of thing.

This type of information can be got to by ssh-ing into the machine, since the machine appears to have networking, or the machine can be recovery-booted to a command prompt by hitting the escape key as Grub is starting after the bios info loads at boot and getting into the Grub recovery menu. 

If the X server is actually running (but your display adapter is just giving you a blank screen) you may be able (depending on what the client is running)also to ssh into the machine and use graphical-mode  tools to obtain diagnostic info by using "ssh -Y" 

The message that mythweb was giving you was a reminder that the mythtv backend (with tuner card info, etc.) needs to be configured before the mythbackend daemon will start. Once you have X and a desktop, this configuration can proceed either from a virtual terminal by running "sudo mythtv-setup", or from the mythbuntu control center.

---

