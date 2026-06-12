---
title: "Mythtv installation problem"
date: 2009-09-26
forum: Mythbuntu
---

### Post by wbrokow1 on 2009-09-26
I have ubuntu 8.10 and am trying to install mythtv but when I run the mythtv program I get a mysql error.  It seems as though I can't access the database.  I ran the sudo apt-get install mythtv program and I know that the mysql database is running.
I checked.  If anyone has any guidance or a howto to follow I would appreciate it.

I am using a pv-350.

Thanks for any guidance

---

### Post by klc5555 on 2009-09-26
> **wbrokow1 said:**
> I have ubuntu 8.10 and am trying to install mythtv but when I run the mythtv program I get a mysql error.  It seems as though I can't access the database.  I ran the sudo apt-get install mythtv program and I know that the mysql database is running.
I checked.  If anyone has any guidance or a howto to follow I would appreciate it.

I am using a pv-350.

Thanks for any guidance

Did you run sudo mythtv-setup to do the initial mythtv and database setup? Or set them up from myth control center? You may wish to check the Mythbuntu 8.10 manual at [http://mythbuntu.org/installation_manual](http://mythbuntu.org/installation_manual)

---

### Post by wbrokow1 on 2009-09-26
I used the sudo apt-get install mythtv command.
I haven't seen the control center you describe .

---

### Post by wbrokow1 on 2009-09-27
The manual doesn't address the database errors.

---

### Post by klc5555 on 2009-09-27
> **wbrokow1 said:**
> I used the sudo apt-get install mythtv command.
I haven't seen the control center you describe .

To reiterate: Did you run sudo mythtv-setup to do the initial mythtv backend and and database setup? Until you do this, or until you install the myth control center and do your myth tv backend setup from there, you don't have any mythconverg database for mythtv to log into. Even though MySQL may be running. You may also wish to check using Synaptic to make sure you have all the mythtv packages installed. The critical ones are mythtv-frontend, mythtv-backend, mythcontrols, mythtv-common, and mythtv-database. Just doing an apt-get for "mythtv" may have omitted mythcontrols; it certainly omitted the various themes and plugins packages (which can all be added later if/when you want to use them)

When you run the mythtv-setup command, you should be confronted with an initial backend setup screen that looks like the one that begins Chapter Nine of the Mythbuntu Installation Manual. That's where you start.

The other good resource for the initial configuration of a new mythtv backend is on the mythtv wiki: [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

Beginning chapter 3 "configuring mythtv". 

There's a fair amount of software out there that's just install-and-play, without much reading and head-scratching involved. Whether for good or ill, mythtv is way outside that category. But once configured it's very powerful stuff.

---

### Post by wbrokow1 on 2009-09-27
Yes I ran the sudo mythtv-setup and that is where the database error occurs.  Do I need a username of mythtv to do this install?

Thanks for your patience.

---

### Post by klc5555 on 2009-09-27
> **wbrokow1 said:**
> Yes I ran the sudo mythtv-setup and that is where the database error occurs.  Do I need a username of mythtv to do this install?

Thanks for your patience.

As part of the package installation process, the "mythtv" user and the database setup for it, et al., should have been created. Since Ubuntu would prefer not to have most of the mythtv tasks handled by root. If they were not created, then you may have to do it manually.

The wiki's mythtv manual is written with fairly close attention to Ubuntu-specific peculiarities, so ch4 "Post Install Tasks" starting with "creating the mythtv user" [http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user)
can be followed without much change. The "mysql.txt" file can be cut-n-pasted from the wiki manual into /home/mythtv/.mythtv/mysql.txt

---

### Post by wbrokow1 on 2009-09-27
I received this error when I ran the apt-get install command for required packages:

bash:  libid3tag0-dev: command not found

Thanks for any help.

---

### Post by klc5555 on 2009-09-27
> **wbrokow1 said:**
> I received this error when I ran the apt-get install command for required packages:

bash:  libid3tag0-dev: command not found

Thanks for any help.

libid3tag0-dev is an exact match for the package name. You may have typoed, used incorrect syntax, or forgotten "sudo" when using "sudo apt-get install libid3tag0-dev"

You can also use synaptic to install the dependent packages as a group, or even install them individually from firefox (using firefox's gdebi plugin) from the Ubuntu package archive at packages.ubuntu.com

---

### Post by wbrokow1 on 2009-10-02
After installing all the packages I still get the mysql error.
The username mythtv is created.
mythtv-setup keeps going round and round in circles telling me it can't login to the database. So it goes through the routine of asking for usernames database name password etc.  All things 
that have been created. 

It sound like a permissions problem to me the inexperienced user.
I tried to cut and paste the exact error from the terminal window, but ctrl-C & ctrl-v don't seem to work.

Any ideas from anyone.  I really want this to work.

Thanks In Advance

---

### Post by drifting on 2009-10-02
That is exactly the problem I am having, I even went so far as to download another ISO, same result. Mythtv user cannot login to database, authentication failure.

Must have tried this a dozen times, tonight I even dug out another machine to try the install on, same effect.

Paul.

---

### Post by NinjaNumberNine on 2009-10-02
Is this your problem?
[http://ubuntuforums.org/showthread.php?t=1211669](http://ubuntuforums.org/showthread.php?t=1211669)
If so I can help fix it.

---

### Post by wbrokow1 on 2009-10-02
Yes, you had the same problem I have now.
What do I do?
Thanks

---

### Post by ConXtionS on 2009-10-02
Hi Bro
 
I started ubuntu about 5 days ago so I cant really help you with your problem except to tell you what I have done.
 
Early on my first day I got a WONDERFUL PRIVATE message from a guy who clearly knows more about ubuntu than I ever hope too.  One of his suggestions besides reading the noob guide was that if I was REALLY GOING to try Myth TV as a noob to do it on a fresh install using MYTHBUNTU.
 
I know there are lots of articles about how to share with windows and lord knows what else... However when I was having problems I remembered what the wise one told me.   I down loaded a program that wrote 0's across my whole drive (cuz I wasnt smart enough to format in ubuntu), then I downloaded MYTHBUNTU burnt the cd and only a couple days later, and LOTS AND LOTS of reading the dang thing just works.
 
SO, if I can help at all it is to say, start with the basics, you need a computer with a cdrom, I had a gig of ram so I used it, I had an old nvidia graphics card, I bought the haupperdingle 1600 and I bought a generic eithernet card.   I installed it all, and brought mybuntu up clean.... I went slow, and made sure I knew what I was supposed to type (who would of thought that video sources could possibly mean PROGRAM GUIDE?) and like I said... it worked.
 
Good Luck to you sir...
 
Jim

---

### Post by NinjaNumberNine on 2009-10-02
Here's something I posted a while back:

> [IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG]                 **Re: "Deleting UPnP client", then "No UPnP backends found"**             
                                                                Okay, you guys seem to use this strategy: "Don't reply for at least a day and maybe he'll figure it out himself without our help." Not sure I like it, but it DOES work. I got this thing fixed again by the following commands:
     
     ```
sudo apt-get remove libqt3-mt-mysql 
```
then, seing that the previous removed mythtv as well, I type
     
     ```
sudo apt-get install mythtv 
```
then get the mysql back by 
     
     ```
sudo apt-get install libqt3-mt-mysql 
```
 and what do you know, Now I run the MythTV Backend Setup and it still says no UPnP backends found but don't leave: I press enter, go through the 2 config screens, and BAM, MythTV Backend loads, and everything works great! 
I hope this helps someone, and I was just kidding about the strategy. There is great support here, even though sometimes a post is not answered for a while.

Thanks, everyone!Please post what happens here!

---

### Post by chipppy on 2009-10-02
Good Morning

Firstly 
And a big thanks as this thread has helped me to fix a problem I have had for months that is not directly related to you problems

Second
To answer a question from the last page

When in terminal use 
Cntrl + Shift + C  to COPY
Cntrl + Shift + V to PASTE.

you should see the pattern of the extra '+ Shift' when in terminal.  This will fix up tat part.  When pasting error message into forums watch the size of the different file types so that it is not to big to upload on the forum.

Personally I tink making a clean install of Mythbuntu is the easiest option for a newbie.  This will also be the most positive experience.

If you are running the one computer as a desktop at the moment, Gnome or KDE desktop version, and want to continue after the MythTV install may i suggest the following possibility.  This is what I did while still experimenting with Linux.  Now i have way to many computers riunning to many systems.

Save all you personal data to a portable harddrive (there cheap).
Write a list of all you favourite apps (programs)

Find a good guide on the web for the steps to get MythTV setup.  there are heaps of good step-by-step guides on the net with pictures that make the initial install super easy.

Do a Mythbuntu install from CD (this will format harddrive in process).
Setup MythTV as per you guide.
(You can get Mozilla from the XFCE desktop oncce you have completed the initial setup by pressing 'ESC' a few times.)
Test and be happy with you setup.

Go to Applications ==> System ==> Mythubutu Control Centre (I think, Im not on my Mythbuntu machine at the moment) here you can add in your favourite desktop eg Gnome or KDE.  pick one if you want but really XFCE is Ok and can do the job just aswell as any other desktop

Change to you favourite desktop and install all you favourite apps (programs)
Copy your saved personal data into the relevant storage directories and va-la one MythTV and desktop all up and running (this may take a few hours though)

Oh a small helpr here is a little guide to get you through the another harddrive install into MythTv as it is a good place to put all the video files to stop you main harddrive from filling up real quick and killing you desktop
[HTML]http://members.iinet.net.au/~chipppy/Mythbuntu/Add-Another-Harddrive.html[/HTML]

Any hope this helps some

Cheers
chipppy

---

### Post by ConXtionS on 2009-10-02
Hey... NO FAIR!!!!
 
What was your problem and how did you fix it?????
 
Im a noob so I need all the info I can get!!! lol
 
Thanks Sir
 
Jim

---

### Post by chipppy on 2009-10-03
Good Morning

My problem is to do with a corrupt fill within the system package.  One of the comments in this thread reminded me that I can just reinstall the complete package or a part of a package to fix the corruption problem.  Not really related to your problem with the database but just a remind to do the simple things before looking at the harder items.

Anyway look into the Mythbuntu path.

as a thought 9.10 is due out really soon with the 0.22 version of mythTv so if you install 9.04 be preparedfor some large changes in the 9.10 version.  also 9.10 is a LTS (Long Term Support) version so it is the best option for you as it will have the fixes for a few known 'issues' with MythTV

Anyway welcome to Linux. get in there, try, enjoy, learn.

Cheers
chipppy

---

### Post by drifting on 2009-10-03
Solved the problem for me, did yet another clean install, same issue no connection to database.
Installed PHPMyadmin and dropped the mythconverg database as well as the user, created the DB and user, went back to mythsetup and it now all works. There is something definitely screwy with the mythbuntu installer, and the same problem is also there on the latest Alpha.

Paul.

---

### Post by chipppy on 2009-10-03
Good Evening

That sound like where I have got my problem to with a database fill problem.
As my reinstall of packages didnt work completely.

I can get all my video to display but I cannot find any in the video manager also same problem with my music.

I know nothing about databases.

Could you step me though what I need to do (to do what you did to fix you problem)and I will try the same and see if it fixes my problem.

Cheers
chipppy

---

### Post by drifting on 2009-10-04
Oh dear, I am not an adept Linux user, I did lots of searching on here and on google, basically I installed PhpMyadmin, and then followed another link on recreating the user and database manually.

Really sorry would love to supply more detail, but might break more than I fix for you.

Good Luck.

Paul.

---

### Post by chipppy on 2009-10-05
Good Morning

I am back to this problem again with a small difference from earlier in this thread.  I had a primary HDD failure.  This meant a new HDD and a clean install of Mythbuntu 9.10 beta.  I have everything up and running and the system works except for this problem.  I think.
what is happening is that I am unable to get the video manager to find any movies (the same symptoms as I have previously in my 9.04 install).
So Utilities/Setup ==> Video Manager ==> no file found.

I have been through all the path for where videos are stored and all the common mistakes.  Believe me I have made all the common ones before and I have a notebook full of them to prove it.  I have been through all my notes to try and fix.

**Drifting** I understand the concern about breaking another person computer but at the moment I am on a clean install and there is nothing to break as it dosen't work at the moment.  If I do break the computer it just means a hours or so for another clean install to get back to where i am now.

Please can you post the links/web-pages/threads that you followed and I will give them a try and see if it can fix my problem.

cheers
chipppy

---

### Post by drifting on 2009-11-23
I am assuming you found out how? I have not been online for ages, so missed your post. If you still neeed help, more than happy to do what I can.

Regards Paul

---

