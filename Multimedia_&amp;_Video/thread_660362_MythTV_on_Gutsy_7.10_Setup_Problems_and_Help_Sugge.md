---
title: "MythTV on Gutsy 7.10 Setup Problems and Help Suggestions"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by Jim-BobH on 2008-01-06
Ubuntu-MythTV-post-1.txt

I am not a Linux geek. I am one of the many folks (I imagine) attracted not to the proposition of slaving away for weeks trying to find every last detail required to make a DVR out of a Linux computer, but rather to the idea of a nifty, free, TiVo-like device with additional wonderful capabilities, like true HD playback via DVI-to-HDMI with 5.1 sound, direct from the hard drive, or burning superior-quality DVDs (even Dual-Layer) on the same box.

Ubuntu and MythTV together promise that "mythical multimedia box" and more "for the rest of us" (non-Linux geeks), and with Gutsy (7.10) _almost_ delivers.

Here is my experience; please point out where I went wrong, and then let's proceed to help others avoid the same pitfalls; I don't see how to get the indicated fixes into the installer and/or documentation.


I did a standard 7.10 desktop install from CD, manually fixing the hang on no internet access, which when rebooted added IPv4 so now it works solidly.

I opened Synaptic Package Manager (SPM) and selected MythTV and did the Install. The automatic add of my User to the mythtv Group is impressive. I took the simplest path: no networked MythTV machines, backend and frontend on this box, etc.

However, when I start MythTV it finds no database. Further, ps-ef | grep mysql finds nothing (except of course the grep mysql process), even after a reboot. I presume this means MySQL server is not running, and I find no help anywhere on how to start it.

So I go back to SPM and search for some client or admin tool for MySQL, find a couple (MySQL Administrator and MySQL Query Browser) and install them, and of course they can't connect to a MySQL server that isn't running, so they can't start it either.

I am very confused about what command, User and Password to use to start the MySQL server in a Terminal (is it mysqld? what about safe?), and I find no help on that either.

So then I do the usual Googling, find some relevant stuff in forums like this, and try them, e.g. the page

[https://help.ubuntu.com/community/MythTV_Gutsy](https://help.ubuntu.com/community/MythTV_Gutsy)

NOTE: If the above instructions take precedence over what I did, then there should be some way of noting that so when the User does the normal thing and just tells SPM to add a new package, it should say at least something about checking the other instructions FIRST.

Also, on the page [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)

I think instead of the label "Install MythTV", it shoud say "Start the Mythbuntu Control Centre" from the System >> Administration Menu. Even so, I figured this out with help from Google and

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

and I got thru the succeeding screens OK, it seems, until I got to MythTV Configuration >> Launch MythTV Setup, and answer OK to closing the backend. I see a Terminal with hundreds of lines of text flying by which then closes without my having a chance to actually read any of it, tho I see many errors including "access denied" and "database not open".

Then I go to

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

and follow the troubleshooting tips, but when I get to

When you installed, did you set a root mysql password? If so, you need to

   sudo dpkg-reconfigure mythtv-database

I try that and get the following:

jim@roonwit:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for jim:
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: NO) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

(Notice that the fix to "Try:" on the last line is exactly the command we just ran to generate the error!)

and the first error I get _again_ points to mysql-server not running.

I try some more of the suggested fixes and get no further. The section that exactly matches the error I got, "Access denied for user 'root'@'localhost'", is no help, because all it does is confirm that mythbackend is not running (because, of course, MySQL is not running!).

I think I found the name of the MySQL Server (mysqld) so I try that:

jim@roonwit:~$ mysqld
080106 16:48:49 [Warning] Can't create test file /var/lib/mysql/roonwit.lower-test
080106 16:48:49 [Warning] Can't create test file /var/lib/mysql/roonwit.lower-test
080106 16:48:49 [Warning] One can only use the --user switch if running as root

080106 16:48:49  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
jim@roonwit:~$

so then I think I need to try to start it as the mythtv user or root or something and try man mysqld to see if I can learn _that_ (this is getting ridiculous) and after skimming 6168 lines of MAN output I give up on that idea.

Along the way, I tried running a few commands in Terminal, e.g.:

jim@roonwit:~$ mythtv-setup
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.

which again confirms mythbackend is not running (because MySQL is not running?).

When I run System >> Administration >> MythTV Backend Setup

I look at the MythTV Frontend screen, Database Configuration 1/2, and it says:

host name: localhost
database: mythconverg
user: mythtv
password: q954hdxW (not my real password)
database type; MySQL

None of the other Troubleshooting tips on

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

seem to be worth pursuing if the database is neither running nor set up, so now I'm stuck.

Any ideas?

Thanks for any help.

Jim

---

### Post by Jim-BobH on 2008-01-11
Today, for about the third time since my MythTV install and last post, I powered up the BuntuBox, and this time, for the first time, my login screen was changed to be one from Mythbuntu, and it showed (which my regular login did not) the 2 Win XP logins that I imported on this box (it's dual-boot) when I installed Gutsy a few weeks ago. Hm-m-m-m.

Well, anyway, I enter my Gutsy UserID and password, and it comes up in Mythbuntu, and it still needs the Configuration, so it takes me to the first backend setup page and still does not connect to the database.

I don't know if this story will help anyone figure out what is going on, but there it is just in case.

Jim

---

### Post by Scorpuk on 2008-01-11
Just as a quick question did you click on Launch MYthTV Setup during your installation and setup the tuner card(s) as per [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop) ?


Unfortunately Linux is still not 100% fo rthe uninitiated. Installing softwar estill requires a little poking around to see how others did it as **S**ynaptic **P**ackage **M**anager will not always give you 100% pointers to installing the software you have selected.


Heck at times I even get frustrated when I install something from SPM and it just says completed and I have no idea how to run the program as it hasnt added it to the applications menu. :-)


Anywho back to your problem. :D


If you haven't setup your tuner cards it might be best to uninstall mythtv with a removal option and reinstall. (This would be through SPM by right clicking on the one you installed you should get an option to uninstall and completely remove)


If you then follow the instructions at [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop) then you should be good to go.


Goodluck and let us know how ya get on. 


Good or bad. :lolflag:

---

### Post by Jim-BobH on 2008-01-11
Thanks for the ideas, Scorpuk!

Yes, I agree. I also have had to figure out lots of missing steps, how to run an installed package, etc. as you mention.

Here's what I did:

Mark everything myth... for Complete Removal, Apply, search for it afterwards, gone.

Mark everything mysql... for Complete Removal, Apply, search for it afterwards, gone.

Follow instructions on

[https://help.ubuntu.com/community/My...ontend_Desktop](https://help.ubuntu.com/community/My...ontend_Desktop)

I install from the first link, then choose System >> Administration >> Mythbuntu Control Centre (MCC) (which step is missing from the instructions, BTW) then choose the first main step,  System Roles, choose Primary backend, Frontend, and Ubuntu desktop, Apply.

Note: the first time I did this, it did the "LIRC ... setup your remote" and the "generate random password" windows, but not this time.

It does some encouraging installing/setup then I get the "Update information" window:

MythTV-Database reconfigure required

The mythtv-database package was upgraded or installed, but was unable to contact a MySQL server.
If you were in the process of dist-upgrading, this is normal as mysql-server is stopped for a portion of the upgrade.
If this is a fresh package installation, verify that mysql-server is installed and running.  Once you have verified the server is running, you can reconfigure the package by running 'sudo dpkg-reconfigure mythtv-database'.
If your root password or location of the MySQL server are non standard, you can also update them via 'sudo dpkg-reconfigure mythtv-database'.

This is where I tried to do what it said before, and could not cuz I don't know anything about MySQL and there is no help in the Mythbunto installation instructions.

Anyway, right at this point a started a Terminal and did this:

jim@roonwit:~$ ps -ef | grep mysql
root     15518     1  0 18:36 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql    17129 15518  0 18:36 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root     17133 15518  0 18:36 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
jim      17186 17161  0 18:39 pts/0    00:00:00 grep mysql
jim@roonwit:~$ 

so now it appears that the MySQL database _is_ running. It's mysqld, not "mysql-server" as the instructions say, isn't it?

So now, again, I try to follow instructions, so I d the following (taking all the recommended actins, passwords etc.):

jim@roonwit:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for jim:
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: NO) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
jim@roonwit:~$ 

so now it seems I am again back where I was.

But, anyway, I go on tho the second Main topic in MCC, "MythTV Configuration", and push the button "Launch MythTV Setup", as I did before, which I believe means I answer "yes" to your question, "Just as a quick question did you click on Launch MYthTV Setup...?". So, I do it again this time.

I get the exact same response I originally posted. Same Terminal opens, apparently the same zillion errors fly by, and the same "Myth could not connect to database" situation on the MythTV Frontend screen, "Database Configuration 1/2".

Well, at least we're consistent.  :(

Do you know anyone who can answer the other questions in my first post, about MySQL or about how we get these problems and suggested improvements to e.g. the setup instructions communicated to those who can update them?

Thanks again for your help.

Jim

---

### Post by Scorpuk on 2008-01-12
I am puzzled as there should be no need to faf around with mysql.

Anywho onto what I should have asked you in the first place: 

What is the spec of your box? In particular capture card (TV)? :-)

---

### Post by thefoolisme on 2008-01-12
I have been having the EXACT same problem as Jim-bob, and with the same results.  I CANNOT get MythTV up and running.  You can't do anything until it's talking to MYSQL, and it just won't do it.  Does anyone else have suggestions?  I've been through all the same "how-to" and troubleshooting pages as Jim-Bob, with no result.  What sucks is I've been at this for days, and now my trial for Schedules Direct is expiring, and I haven't been able to try it out.  I don't want to pay $20 if I can't get mythtv running.
 HELP!!!!!!

---

### Post by Jim-BobH on 2008-01-12
OK, here's more info:

I cannot connect to mysql as mysql root.

I have not set a mysql root password; it is still shown as blank in the screens I walk thru with

sudo dpkg-reconfigure mythtv-database

Now MySQL is definitely running, but I can't connect and apparently this is why Mythbuntu backend cannot start, and why the MythTV Frontend screen, Database Configuration 1/2, says "Myth could not connect to database":

jim@roonwit:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
jim@roonwit:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
jim@roonwit:~$ 

Note that MySQL is running on its default port (3306):

jim@roonwit:~$ ps -ax |grep [m]ysqld
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 5021 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 5061 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 5062 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
jim@roonwit:~$ 

BTW, what is wrong with ps -ax (see Warning above)?

BTW2, I have no tuner card installed yet, but that is irrelevant to this current problem, right, Scorpuk (or anyone)?

I think next I will Completely Uninstall everything Myth... and everything MySQL... then install MySQL alone by the normal means (Synaptic Pkg Mgr) and get it running, _then_ try installing Mythbuntu according to the instructions on

[https://help.ubuntu.com/community/My...ontend_Desktop](https://help.ubuntu.com/community/My...ontend_Desktop)

IHTH

Jim

I

---

### Post by Scorpuk on 2008-01-13
Can you try the following:


1. Completely uninstall and remove everything to do with mythubuntu and mysql (as you said you were going to)

2. Start Synaptic Package Manager (SPM)

3. Locate and select Mythtv-backend-master. 

4. Allow all dependencies to be installed

5. Apply and Install

6. Make sure you note down the password you are given for the mythtv database.

7. Goto System -> Administration and select MythTV Backend Setup.

8. Go through each of the setup options in turn. IE 1, 2, 3, etc. Follow the instructions for MythTV setup here: [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop).   (Scroll down until you see the picture of the mythtv backend setup screen and then follow from there)

9. Once this stage is complete you now need to install the frontend.

10. Start SPM, if not already running

11. Locate and select mythtv-frontend.

12. Allow all dependencies.

13. Apply and install.

14. Goto Applications -> Accessories and Select Terminal

15. Type mythfrontend  (We are doing it this way as any problems will get reported to the terminal window, so you can cut n paste to this forum ;))

16. Select your country (If asked)

17. Enter the info for your backend. IE 127.0.0.1 (btw 127.0.0.1 is the same as localhost) and the mysql database password you were given during the backend install.  If you have forgotten you can find it here : /etc/mythtv/mysql.txt

18. Hopefully you are now watching live TV.

19. Additional items can now be installed to MythTV through SPM. IE mythvideo, mythdvd, mythtv-themes, mythweb, mythmusic, etc. Some of these may have been automatically installed during mythubuntu. No idea as I have never installed mythubuntu and always use the above method. :D   (just search on SPM for myth to see all the available options)


Goodluck ;)

---

### Post by rjs82vette on 2008-01-17
My installation did not create the database...... I had to manually create it in MYSQL...

cant access it if it not there......

---

### Post by Jim-BobH on 2008-02-12
Sorry, I've been away and not working on this.

I don't know how or why, but mysql is now clearly running when I boot Ubuntu; maybe this is cuz I did the complete uninstall and re-install:

jim@roonwit:~$ ps -ef | grep sql
root      5094     1  0 Feb03 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     5134  5094  0 Feb03 ?        00:00:04 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5135  5094  0 Feb03 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
jim@roonwit:~$ 

However, I still get the same error when I choose Applications >> Sound & Video >> MythTV Frontend, on the page after I choose English I get "could not connect to database" with the settings previously reported.

So now I have some basic needs as I am pretty much a noob on this; sorry:

1. What tools do I have to use to determine _why_ MythTV Frontend cannot connect to the database? I have already followed all the suggestions previously posted, and have the same results.

2. I have no tuner card installed. I have e-mailed PCHDTV twice and sent them my name  and contact info and a photo of the card but they don't reply and I don't remember the model number so I cannot tell you what it is, and it doesn't matter at this point anyway, right? Anyway I think I just attached a pic; maybe someone on this forum is more helpful that the seller ...

BTW, I sure wish I could set this forum to e-mail me when someone posts to this thread ...

Thanks again for any help.

Jim

---

### Post by Jim-BobH on 2008-02-12
One more try on the PCHDTV tuner card pic ...

---

