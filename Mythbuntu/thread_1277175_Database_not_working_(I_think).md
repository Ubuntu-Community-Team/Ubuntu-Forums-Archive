---
title: "Database not working (I think)"
date: 2009-09-28
forum: Mythbuntu
---

### Post by chipppy on 2009-09-28
Good Evening

I am running Mythbuntu 9.04 with the frontend and backend on a standalone machine
I have a problem with my DataBase (I think) not filling.

When I run Utilities/Setup => Video Manager or Music Tools => Scan For New Music, nothing is found.

I have checked the linking in the following
Mythfilldatabse Program: /usr/bin/mythfilldatabase
Directories that hold Videos: /var/lib/mythtv/hdd2/videos (second HDD for storing movies)
Music Settings =>General Settings =>Directories to hold Music: /var/lib/mythtv/music

these are all correct for where the actual videos and music are saved. I have also tried a video database fill after copying a couple of file to the var/lib/mythtv/videos (default file path) folders just in case that worked.

When I go Media Library => Watch Videos I can actually see all my videos and play them all without any problems. Unfortunately I cannot say the same for music. This one is causing a fair bit of grief from the wife.

I have everything else working fine.

I have tried the Repair Database in Mythbunutu Control Center. This has not helped.
It seems to me that the databases as not being filled and I am at a loss for what to try to fix this problem. I am down to a doing a clean rebuild but I have invested to many hours getting my HTPC working perfect to jump down this path. I want to fix this problem

I have attached a modified errorlog, I deleted some of the crap out though (the machine hardware details, multiple error message saying the same thing a couple of micro seconds apart).  This is to get the text file below the 19.5kb limit.  If you need the full errorlog please ask and I will cut and paste into a word doc or tar one up.

Anyone got any ideas what I can try next????
Any and all assistance is greatly appreciated.

Cheers
Chipppy

---

### Post by chipppy on 2009-09-28
I have tried to rip a new CD into the computer and then run a scan for new music.  I have thn run a gather logs and copied and pasted the full file on this thread in word format so that I didnt have to edit it for file size requirments.

I hope this helps 

cheers 
chipppy

---

### Post by chipppy on 2009-09-30
bump.  anyone able to assist?

Cheers
chipppy

---

### Post by chipppy on 2009-10-02
bump

---

### Post by ian dobson on 2009-10-03
Hi,

It looks as if your music_directories table is corrupt.

Can you try dropping the table and recreating it. The only other thing I can think of is that the value your trying to read ('timberland/shock value' ) contains a valid mysql keyword (value). Could you try renaming the directory.

I don't use myth music so I can't really have alot of experiance with it.

Regards
Ian Dobson

---

### Post by chipppy on 2009-10-03
Good Evening

how do I drop the table and recreate?  I dont understand what you are saying due to not understanding enough about databases.

In the mean time i will try the rename the directory and see what happens

Cheers 
chipppy

---

### Post by chipppy on 2009-10-03
Good Evening

OK some new stuff.

First 
I move the Timberland file and renamed it to something else.  The music error for Timberland in the errorlog above disappeared and was replaced by another file.
So the same symptons but a different file name.

Second
I tried the old reinstall various packages
mythdatabse
mythcontrols 
libid3....
etc
etc

updated the computer to see if it needed anything new.  Restart
The same thing symptons but I got the 'Enter IMBD' black popup on the video database back.  This is a know issue and I have an easy fix, but I have left it alone to try and fix the population problem.

I looked at the logs and hae now got a mysql database connection error.

Full errorlog report [COLOR="Blue"]**[http://mythbuntu.pastebin.com/f3936b1c9]("http://mythbuntu.pastebin.com/f3936b1c9")**[/COLOR]

Anyone able to assist here.?
Should I do a reinstall of the backend?

Cheers
chipppy

---

### Post by ian dobson on 2009-10-04
Hi,

Looks as if the sql datbase is really screwed up or mysql is having problems starting early enough.

Are you using a fixed IP address for your backend or are you getting the IP address through DHCP?

Regards
Ian Dobson

---

### Post by chipppy on 2009-10-04
Good Evening

Mt Mythbuntu box is a standalone with the front and back ends both on the one box.  i am not sure about the answer.  How do i find out.

In the mean time I have been doing some reading on the web in relation to a google search for 'mythtv database not connecting'.

First I worked through
[B][COLOR="SeaGreen"][http://www.mythtv.org/docs/mythtv-HOWTO-22.html]("http://www.mythtv.org/docs/mythtv-HOWTO-22.html")
section 22.4[/COLOR][/B]

/usr/local/share/mythtv/mysql.txt doesnt exist.  Infact /usr/local/share doesnt even have the mythtv folders

There is a copy in /home/mythtv/.mythtv/mysql.txt
I have attached a copy for you to read.
I did notice this line #'d out in relation to your not enough time for mysql to start up.
```
#WOLsqlReconnectWaitTime=0
```

Moving onto the **MySQL not connecting correctly** section I found  the file in the correct location and it has the 
```
bind-address		= 127.0.0.1
```
I have attached a copy as well for you to look through.  (I renamed the copy my.txt and my.cnf is an invalid file type for upload)

I tried the mysqlcheck -r -umythtv -p<password> mythconverg in terminal and got the following.  (I replaced the <password> with the password for mysql.  The *********** is the hide the password that I use incase this is a nono to enter into threads)
Where it has Enter password I have assumed that it is asking for the mysql password and not my root passowrd (which are different)
```
chipppy@chipppy-htpc:~$ sudo mysqlcheck -r -umythtv -p ****** mythconverg
[sudo] password for chipppy: 
Enter password: 
mysqlcheck: Got error: 1045: Access denied for user 'mythtv'@'localhost' (using password: YES) when trying to connect
chipppy@chipppy-htpc:~$ 

```

There is also mention that the/var folder is to full because of log files.  How do I check if the folder is full or not and if there are infact to many log file which ones are safe to delete?
kern.log.0 is 331MB
messages.0 is 54MB
both need root authroity to delete

moving onto a new webpage for trouble shooting
**[COLOR="SeaGreen"][http://www.mythtv.org/wiki/Troubleshooting:Mythbackend_will_not_start_after_upgrade]("http://www.mythtv.org/wiki/Troubleshooting:Mythbackend_will_not_start_after_upgrade")[/COLOR]**

This one refers to other locations for the mysql.txt and guess what i found in /etc/mythtv/mysql.txt but another mysql.txt.  It reads the same, so i saved a copy to my desktop and deleted it.

I read through a couple of other thread here and there and I see mention of a manual delete of the user and re-entering for mysql through PHPmyadmin fixed the same sort of problem.  Do you know how to do this as I know nothing about PHPmyadmin.

Moving onto troubleshooting webpages
**[COLOR="SeaGreen"][http://www.bramkortleven.be/?p=131]("http://www.bramkortleven.be/?p=131")[/COLOR]**

I read through and ran a ```
find / -name mysql.txt
```
```
/usr/share/mythtv/mysql.txt
/home/chipppy/Desktop/mysql.txt
/home/chipppy/.mythtv/mysql.txt
/home/mythtv/.mythtv/mysql.txt

```

/usr/share/mythtv/mysql.txt        was a broken link and wouldnt open.  Deleted this one
/home/chipppy/Desktop/mysql.txt    is the one on my desktop whcih I will rename before further testing
/home/chipppy/.mythtv/mysql.txt    was a broken link and wouldnt open.  Deleted this one
/home/mythtv/.mythtv/mysql.txt     is the work copy that I am reasonable sure is the one that I need to keep.

that is the cuurent state of play.  I am now going to do some testing and heres hoping.  I will post results soon.

Cheers
chipppy

---

