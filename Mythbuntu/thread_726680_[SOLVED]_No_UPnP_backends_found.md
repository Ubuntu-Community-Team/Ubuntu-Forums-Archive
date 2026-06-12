---
title: "[SOLVED] No UPnP backends found"
date: 2008-03-16
forum: Mythbuntu
---

### Post by larsolav on 2008-03-16
Hi. I have a single combined frontend/backend machine running Mythbuntu 7.10. Today as I was playing a movie using mythvideo, the system would not respond to the remote control nor the wireless key board. I could see the red light of the remote receiver illuminate as I pressed buttons on the remote, but nothing happened. I then SSH into the machine and did a reboot. That was probably a mistake, but I did not know what else to do...
After reboot, the normal things happen, but as the screen turns the Mythtv wavy blue, I get a screen where I can select a language from a list, then I get an error message saying **"No UPnP backends found"**
I then press OK (both keyboard and remote work), and get a second screen, with 
> Database Configuration 1/2
       	Hostname: [was empty, so I entered &#8220;localhost&#8221;]
		Port: [empty]  	
Database name: mythconverg
	User: mythtv
	Password: EBGPhVR&#8221;                      [ Password same as in mysql.txt]

Then a second screen:
> Database Configuration 2/2
Use custom identifier for frontend preferences [unchecked]
Enable Database Server Wakeup [unchecked]

After clicking finish I get the black MythBuntu screen.

So I downloaded the updates thinking that may fix stuff, but it didn't.

I checked to see if the backend was running:
> husebo@MythBox1:~$ ps -p `cat /var/run/mythtv/mythbackend.pid
>
and it is not...

I then tried to export my recorded data in case I need to redo the whole system:
> husebo@MythBox1:~$ sudo mysqldump -u mythtv -p mythconverg recorded > recorded.sql
Enter password: [enter password from mysql.txt]
mysqldump: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect

Then tried the same with a bogus mysql password:
> husebo@MythBox1:~$ sudo mysqldump -u mythtv -p mythconverg recorded > recorded.sql
Enter password: [enter bogus password]
mysqldump: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect


Does this mean the mysql password changed on me? Am I screwed?

tried to restart mysql:
h> usebo@MythBox1:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ]
 * Starting MySQL database server mysqld                                 [fail]


Backend log does not shed any light either, no entries from the last 10 or so hours....

Frontend log is also of no help here...

What do I do next? Really don't want to loose all the recording information for my kid's PBS shows...

Thanks for any help!

---

### Post by superm1 on 2008-03-17
Look at the mysql logs, and see why its not starting.

---

### Post by larsolav on 2008-03-17
The directory /var/log/mysql/  only has files with names like mysql-bin.00061 etc and one mysql-bin.index file.

the mysql.log file in /var/log/ is completely empty, and has a time stamp of 7:25 AM, way before any problems...

any other place I should look?

---

### Post by larsolav on 2008-03-17
However, I did while looking at some of the other logs I found this:

deamon.log:
> Mar 16 13:50:21 MythBox1 gdm[5730]: WARNING: Can't write to /home/husebo/.Xauthority: No space left on device 
Mar 16 13:50:24 MythBox1 mysqld[5289]: 080316 13:50:24 [Note] /usr/sbin/mysqld: Normal shutdown
Mar 16 13:50:24 MythBox1 mysqld[5289]: 
Mar 16 13:50:26 MythBox1 lircd-0.8.2[4068]: removed client
Mar 16 13:50:26 MythBox1 mysqld[5289]: 080316 13:50:26 [Warning] /usr/sbin/mysqld: Forcing close of thread 297  user: 'mythtv'
Mar 16 13:50:26 MythBox1 mysqld[5289]: 
Mar 16 13:50:26 MythBox1 mysqld[5289]: 080316 13:50:26 [Warning] /usr/sbin/mysqld: Forcing close of thread 2

I then checked the disk space:

> husebo@MythBox1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  8.8G     0 100% /
varrun                506M  204K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  132K  505M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/mapper/vg-lib    1.2T  642G  559G  54% /var/lib
overflow              1.0M   16K 1008K   2% /tmp


looks like /dev/sda1is full...
what is safe to delete? When I installed Mythbuntu I did the three partions, and added harddrives using LVM

Thanks!

---

### Post by superm1 on 2008-03-17
Woah that's crazy that so much got filled.  My gut says look at those logs sizes and find the big and old ones.

---

### Post by larsolav on 2008-03-17
Yes, it is a bit wild...


Hmmmm, lets file this in the Dunce file. Looks like that when I was uploading some video posters not found on IMDB, I also happened to copy over an ISO file of a ripped DVD to the folder that holds the posters.... Got rid of that file and now everything works just fine. Well. almost. I can see the recordings, but not my videos, but I have seen the posts about deleting mythDVD and updating mythvideo. Will go check the posts now. 

Anyway: Thanks superm1 for the help, without your suggestion too look into those other logs I would not have seen that error message about "No space left on device" and would not have checked the disk space! You guys are so helpful!

Thanks!

---

### Post by foxhenchman on 2008-10-13
Hello everyone,

I'm a brand new linux user trying to get mythtv to work on my system.  unfortunately I don't know linux at all and am very unfamiliar with command lines (I'm working on it...).  I have ubuntu and installed mythtv in the apps add/remove section.  I got the No UPnP backend message, then it goes to the config screen and everything was prefilled (local host, mythconverg, prefilled login and password), but then says database not found?.

I installed the backend by typing mythtv-setup in the terminal.  It seemed to install a backend, but that didn't change anything.  Can someone help an ignorant linux user like myself?

I've got an ATI TV Wonder HD 650 (PCI) card.  Is that even compatible?

Thanks.

---

### Post by mrand on 2008-10-13
> **foxhenchman said:**
> Hello everyone,

I'm a brand new linux user trying to get mythtv to work on my system.  unfortunately I don't know linux at all and am very unfamiliar with command lines (I'm working on it...).  I have ubuntu and installed mythtv in the apps add/remove section.  I got the No UPnP backend message, then it goes to the config screen and everything was prefilled (local host, mythconverg, prefilled login and password), but then says database not found?.

I installed the backend by typing mythtv-setup in the terminal.  It seemed to install a backend, but that didn't change anything.  Can someone help an ignorant linux user like myself?

I've got an ATI TV Wonder HD 650 (PCI) card.  Is that even compatible?

Thanks.Howdy,

First off, I would suggest not responding to a topic which says [solved] in the header.  It will see very little traffic.

Second, mythtv-setup can't be installed via mythtv-setup that I'm aware of.  Mythbuntu-control-center will, however.  If you are a new user, I'd suggest using it.  Go ahead and open a new thread with the specific problems you are having (error messages from either your shell window, or from /var/log/mythtv).

Have fun,

[INDENT]Marc[/INDENT]

---

### Post by mrand on 2008-10-13
> **foxhenchman said:**
> Hello everyone,

I'm a brand new linux user trying to get mythtv to work on my system.  unfortunately I don't know linux at all and am very unfamiliar with command lines (I'm working on it...).  I have ubuntu and installed mythtv in the apps add/remove section.  I got the No UPnP backend message, then it goes to the config screen and everything was prefilled (local host, mythconverg, prefilled login and password), but then says database not found?.

I installed the backend by typing mythtv-setup in the terminal.  It seemed to install a backend, but that didn't change anything.  Can someone help an ignorant linux user like myself?

I've got an ATI TV Wonder HD 650 (PCI) card.  Is that even compatible?

Thanks.Howdy,

First off, I would suggest not responding to a topic which says [solved] in the header.  It will see very little traffic.

Second, mythtv-setup can't be installed via mythtv-setup that I'm aware of.  Mythbuntu-control-center will, however.  If you are a new user, I'd suggest using it.  

Sounds like either the backend or mysql are not installed or configured properly.

Go ahead and open a new thread with the specific problems you are having (error messages from either your shell window, or from /var/log/mythtv).

Have fun,

[INDENT]Marc[/INDENT]

---

### Post by lproe on 2009-11-29
How is this solved?????

I don't get this post.

---

### Post by larsolav on 2009-11-30
> **lproe said:**
> How is this solved?????

I don't get this post.

My original problem back then was solved by me discovering I had copied over an ISO file (7 or so Gigabytes) to my operating system partition of 10 Gb, thereby maxing out the system partition. No operating system works well on a full disk... I deleted the ISO file and problem was solved. Superm1 was awesomely helpful in getting this Linux newbie to fix his problem.

Are you looking for a solution to "No UPnP backends found" error message? I have seen other posts here on that message, but that resulted from a different problem.

---

