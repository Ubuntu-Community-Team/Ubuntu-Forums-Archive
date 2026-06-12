---
title: "Help with Setting Up MythBuntu"
date: 2010-02-06
forum: Mythbuntu
---

### Post by rcaca0 on 2010-02-06
Okay really dumb questions.  Sorry but I am a newbie in Linux.  
 
I have Mythbuntu loaded up on one of my older computers.  Everything seems to work on the OS side but I have no clue after that what I should do to set up Media part.  
 
What is the Front End and Back End?  Is the Front the OS and the Back the media center?  I don't think this is right since on the OS when I go to the Front end it takes me to the set up for the media center.  
 
Information on my computer:
 
Motherboard with onboard video and sound: Biostar M7SUA with video set at 64 MB
Ram: 512
Hard drive: WD 80 GB IDE
TV Tuner: PCHDTV HD-5500
Video source: Time Warner Cable
 
When I run the lswh command the OS seems to see everything including the tv tuner.  
 
How do I set up Mythbuntu?  Or I think the part I don't know is Mythtv.  I have no idea what to set up and how.  Does anybody know of some instructions?  
 
 
On the TV tuner, I untared the drivers and loaded them (I think).  I used the command tar zxvf <filename> in the directory where it was at (on the desktop).  On the instructions for the card it them mentions to use the command dmesg | grep cx88 and see if you see a message mentioning the HD5500.  I think I see this, I am just not too sure if I loaded the driver when I untared it.  It then talks about moving the Tools folder on the cd to the hard drive then run a Make command.  I did this but the Make command does not work.  
 
 
Thanks in advance,
R

---

### Post by ncpokrt on 2010-02-07
I don't actually use Mythbuntu.  I use Ubuntu with MythTV and Mythbuntu Control Centre as installed packages. So I can't give you Mythbuntu specific advice.  But I might be able to clear some things up for you.

Mythbuntu is an operating system that integrates MythTV and makes installation easier.  The Mythbuntu Control Centre is where you need to go to set up your system.  Each of the tabs on the right allows you to set up individual aspects of the system such as a remote control, MySQL, etc.  

MySQL is the database that keeps track of your recordings.  I strongly recommend that you allow Myth to set up the password.  If you put in your own password, you can have a lot of permission problems.

The Backend runs all of the time in the background.  It automatically records programs, streams live tv, etc.  It is the heart of the system.

The Frontend is GUI that lets you set up recordings, view what you have recorded and a bunch of other stuff.  

I hope that helps.

---

### Post by 4dognight on 2010-02-07
You should read the manual.

[http://www.mythbuntu.org/wiki/installation-guide](http://www.mythbuntu.org/wiki/installation-guide)

---

### Post by rcaca0 on 2010-02-09
Just wanted to thank ncpokrt for explaining the front and back end and 4dognight for the manual. I don't have it completed just yet but I am a lot further along. 
 
Thanks again,
R

---

