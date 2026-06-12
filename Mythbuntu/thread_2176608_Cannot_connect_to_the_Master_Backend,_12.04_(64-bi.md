---
title: "Cannot connect to the Master Backend, 12.04 (64-bit)"
date: 2013-09-25
forum: Mythbuntu
---

### Post by JP_Rockagetty_III on 2013-09-25
I really need your help, this is very overwhelming.  I've been running Linux for a while (mostly Mandrake/Mandriva), and I'm familiar with a lot of concepts. But I need your help.

I am installing Mythbuntu 12.04 that I downloaded within the last 2 weeks.  The new machine is both front end and back end (for now at least).  Here's what I have:

Intel DH77EB board, i3-3245 processor, 2 GB of 1333 RAM
3 TB SATA drive
ASUS PCE-N15 wireless card (RTL8188 or 8192 chipset)
(wired Ethernet will happen soon)

HDHomeRun Dual
I have both the single-bay Gray-Hoverman antenna and a half-wave dipole for RF Channel 11 (29.8 inch "T" shape).  Signal strength on all the OTA stations I watch is over 90%.


Basically, I've gotten the firmware updated on the HDHomeRun Dual.  I can view channels (no sound yet) in HDHomeRun Config GUI (viewing on a monitor connected to the DH77EB).

When I start the MythTV front end, I frequently get the message (every time I change tabs) that "Could Not Connect to Master Backend".  Please help me fix this.  I don't want to use Windows.

The HDHomeRun Dual gets the address 192.168.1.103 from my WRT-54GL (I have fancy DD-WRT firmware but zero real networking knowledge).  The wireless card (in my combination front-end and back-end) is assigned 192.168.1.133.

Please help me connect to the master backend.  The master backend package is installed (of course).  The "local backend" and the "master backend" both are set to 192.168.1.133 in the setup.  I set the port for 6543 for master backend, which seems to be correct (it was blank the first time I ran the setup).

So why won't it connect?

---

### Post by JP_Rockagetty_III on 2013-09-25
Okay, I changed the "local backend" and the "master backend" to 127.0.0.1 and rebooted (then, a second time, I chose "restart").

Kept the master backend port at 6543.  It still will not connect.

When I choose <CTRL> <ALT> <F2> and log in, I typed "/usr/bin/mythbackend-setup", and got many lines of output including:

Could not get inputs for the capturecard.
Perhaps you have forgotten to bind video
sources to your card's inputs?

I also saw:

Mythbackend: No valid capture cards are defined in the database.

When I start the mythbackend from the XFCE desktop, I am asked to start the mythfilldatabase, and we see "Downloading DataDirect Feed".  Then I see

"content-type missing in HTTP_POST, defaulting to application/octet-stream"
(I see that about 10 times) and then soon after,
"timed out".

After the "content-type missing" message repeats like 10 times in a row, the process starts again, and soon the "content-type missing" message repeats another 10 times.


Please help me.  Thanks in advance!

---

### Post by e_james on 2013-09-25
I am very much a beginner both with Linux and MythTV but I am slowly learning some of the useful things to do or not do. I am thinking I might start some sort of howto thread with a list of my discoveries and any helpful comments from others. In the meantime these are some of the things I have learned so far.

I successfully installed the latest MythBuntu 12.04 on my eeePC X101CH netbook and I was able to watch TV and make a recording (using an HDHomerun tuner). Unfortuately there is some sort of bug associated with mythlogserver which keeps throwing up error messages and, with the help of apport, can fiil your root partition with error logs. I did find out that the combined frontend / backend setup is not quite standalone. The frontend won't connect to the backend (or so it says) unless the PC is connected to a network. Of course it will be connected to a network if you are using HDHomerun tuners.

In order to learn more and find a path through the confusion of so many settings, I installed Lubuntu 13.04 instead. Everything seemed to be in order. Next I installed MySQL from the repository and verified as far as I could understand that it was working correctly.

Next step - install only MythTV backend and deal with any problems arising from that. The instructions are not very clear about the distinction between a backend and a master backend. My conclusion is that the master backend has the mysql database and therefore, if there is only one backend on the system, it must be the master. So I installed the master software as well. Next problem - the backend setup goes into an endless loop - select country, database configuration, country, database, country, database etc. The trouble is that the application uses the whole screen - there's no obvious way out. In addition, if you try to kill the loop, it restarts itself. After some research I found that ctrl-alt-right gets me to another desktop and I can then look for solutions. Apparently the backend installer doesn't configure the mythtv user in the database correctly. The database setup details on this page 

[http://www.mythtv.org/wiki/User_Manual:Initial_Installation](http://www.mythtv.org/wiki/User_Manual:Initial_Installation)

are helpful. I followed the relevant instructions and got out of the loop.

I have now arrived at the point where I can run MythTV backend setup. I was able to set up the HDHomerun tuner and scan for channels etc. but the backend wouldn't run properly. Apparently at startup it does various hardware checks and exits if it's not happy. Given that I don't know any network that is currently using IPV6, why does the backend expect to find working IPV6 hardware? I disabled IPV6 and got the backend running (sort of). 

So I installed the frontend and eventually I was able to make a recording. 

When I exit backend setup, it says "start backend?" - answer "yes", "run mythfilldatabase?" - answer "yes" but the backend actually fails to start. More IPV6 problems apparently - something about a duplicate address. I haven't sorted that one yet, but I can start the backend with the command "mythbackend". The terminal is then committed to running that command but MythTV works. 

I am still getting error messages about mythlogserver. Another problem to solve. I saw one suggestion about disabling mythlogserver. I might try that.

---

### Post by JP_Rockagetty_III on 2013-09-26
I bought a subscription to SchedulesDirect, but I still get the message.  Perhaps the database was never created? Maybe I need to create some text files with settings?  A firewall issue perhaps?  I would think the initial Mythbuntu setup would have made sane choices.


Could I share the /home/mythtv directory using Samba?  I could use the Media Center part of my Win 7 on the Quad-core Athlon (main computer, I am using it now) to record TV. I would choose a Windows app to use the SchedulesDirect information.  Then I could store the programs on the new Intel i-3 3245 box using Samba, just as if Mythbuntu put them there.  I hate to have two computers running all the time, the bill for electricity will go up.  But I could get what I want, without another Windows license.

(Windows 7's Media Center comes with its own program guide, but I'll use the Schedules Direct info with a third-party app, probably "NextPVR".)

HDHomeRun and Mythbuntu REALLY "raised the standard" for minimum documentation.  I'll let you know how it works.  Any more ideas, please let me know.

---

### Post by JP_Rockagetty_III on 2013-09-28
1.  Can I hire somebody to come to the house and put this straight?  Does Canonical offer e-mail support?
2.  Would the latest release (13.whatever) be more likely to give me success?
3.  Can I get a master list of important settings, and the files they are in, and the location of those files?
4.  Can I get a list of what the settings files do, so I can match this up with what little I know about networking?

---

### Post by e_james on 2013-09-28
I have been trying to get to grips with linux and mythtv since around 2006. There is a certain type of question which will usually get a straightforward answer along the lines of "yes", "no" or "do this...". It appears that most readers of forums like this prefer to avoid lengthy conversations with detailed advice. They don't always say it but there is an implication that you are not really trying to live in their world of linux. RTFM etc. For myself, at this time, I refuse to go to "linux school". By that I mean spending weeks or even months learning the command line and all the utilities that use it. If you type "man xxx.." for whatever command you think might be useful, you get a comprehensive summary of all the options and maybe one or two examples. If you're not already familiar with the command, it's usually more confusing than helpful. I believe that I could grow to understand linux piece by piece if I had the equivalent of someone looking over my shoulder at times saying "No, don't do that, do this ..."

To attempt to answer your questions -
1. Hire somebody? - probably not. Email? - you could try the mythtv-users mailing list. I already have.
2. Latest release? - you probably already have it.
3. and 4. I stumbled across this about 2 days ago. It will probably answer some of your questions.

[https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit?pli=1](https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit?pli=1)

More later.

---

### Post by e_james on 2013-09-30
Some comments and suggestions. 

With MythTV, because the master backend server is central to the system,  it is also the source of most of the problems. If the master backend  isn't running nothing else will work properly. Probably the most  important component for the master backend operation is the mysql  database mythconverg. If mysql isn't running, the backend won't start. 

First priority is to verify that mysql is running    [http://www.cyberciti.biz/faq/how-to-find-out-if-mysql-is-running-on-linux/](http://www.cyberciti.biz/faq/how-to-find-out-if-mysql-is-running-on-linux/)
If mysql is running and the backend won't start check the backend log  file. I am using Lubuntu 13.04 which has PCManFM as a file manager. So I  go to /var/log/mythtv and open mythbackend.log with leafpad. (Remember I  come from Windows XP and gui is the way I think.) I look at the end of  the file where entries are marked with the time of my last attempt to  start the backend and there is a message along the lines of "failed to  connect to database". As previously mentioned I got out of the initial  setup loop by applying the parts of the following commands that seemed  to be necessary

mysql -u root -p
create database mythconverg;
create user 'mythtv'@'%' identified by 'mythtv';
create user 'mythtv'@'localhost' identified by 'mythtv';
set password for 'mythtv'@'%' = password('mythtv');
set password for 'mythtv'@'localhost' = password('mythtv');
connect mythconverg;
grant all privileges on *.* to 'mythtv'@'%' with grant option;
grant all privileges on *.* to 'mythtv'@'localhost' with grant option;
flush privileges;
exit;

Unfortunately that apparently wasn't enough. I could start the  backend manually but it wouldn't start automatically - couldn't connect  to database. I found that the logon details for the mythtv user are  stored in /etc/mythtv/config.xml and there it was - the wrong  password!!!. So I edited the file to the correct password and now the  backend starts automatically. PCManFM has a handy feature "Open current  folder as root". I find it quite useful.

In the course of my investigations I have belatedly realised that MythTV is designed around the assumption that most of the PCs involved, especially the backends, will be used exclusively for MythTV. That's not the way I usually think about software. I now have a general purpose PC with MythTV apparently running as intended. There are many things still to explore such as storage locations and plug-ins, but it's a start. I realise that some of my procedures are unusual, inefficient and probably hazardous but the netbook is only a testbed until I learn enough to decide how to implement a complete working system.

JP_Rockagetty_III
I notice the error message "No valid capture cards are defined in the database" in one of your posts. I assume you attempted to set up the HDHomerun tuners. In my own case I had no difficulty with that so I would have expected the same for you. Perhaps the details were never saved which would suggest a problem with the database.

---

