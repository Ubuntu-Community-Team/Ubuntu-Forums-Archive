---
title: "cant access my recordings after reinstalling mythbuntu"
date: 2008-11-15
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-11-15
so i had to reinstall my entire OS not too long ago. i have my recodings on a separate partition and my videos on a second hard drive. i have my videos HDD set to mount on /var/lib/mythtv/videos and mythtv sees them right away and i just had to re download all the data. but i also have my recordings partition set to mount on /var/lib/mythtv/recordings. using the file manager, i can navigate to the folder and see all my files there, but mythtv doesnt see them at all. it says there are no recordings. maybe myth is looking in the wrong folder? ive tried looking through all the settings but i cant find the place where you specify where your recordings are like you can with videos under the media settings menu. 

any ideas?

---

### Post by ian dobson on 2008-11-16
Hi,

run mythtv-setup and set the default storage group to point to the correct directory.

Did you also restore the mysql database? Mythtv uses a mysql database to hold information about the recordings etc.

Regards
Ian Dobson

---

### Post by gsrcrxsi on 2008-11-16
i added the path to the default storage group. but i still do not see them in mythtv. i didnt restore the database (i didnt know i could) i just reinstalled everything and repopulated the database with my video information, a PITA for ~150 dvds lol. 

so what now? do i have to restart the system for it to take effect?

---

### Post by ian dobson on 2008-11-16
Hi,

Do you see anything in the logs? 

Does the user who runs the backend/frontend have access to the recordings/video directory?

try going to the terminal and doing su "mythuser" the ls "your dir".

Regards
Ian Dobson

---

### Post by gsrcrxsi on 2008-11-19
yes i have access. i can browse to the files and open them with mplayer under the same user with thunar file manager. i have 2 machines, one is just a frontend, and one is a backend/frontend combo. same results with both.

what is su "mythuser" the ls "your dir" i dont quite understand what you want me to do

im 99% certain that if i were to record something new it would show up, but i want my old stuff there too.

---

### Post by oobe-feisty on 2008-11-19
you should of made a sql dump of your recordings prior to reinstalling

then restore the dump i wont go into detail as its now a moot point

the only solution is for you to run a script called /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz

unpack it make it executable and run it 

if you dont know how to do that then search google or mythtv wiki

---

### Post by gsrcrxsi on 2008-11-20
will that overwrite my videos stuff too?

---

### Post by Stevi on 2008-11-20
A few weeks ago I had the same question. Maybe [my old thread](http://ubuntuforums.org/showthread.php?t=895425) is also interesting for you.

---

### Post by oobe-feisty on 2008-11-20
> **gsrcrxsi said:**
> will that overwrite my videos stuff too?

no it wont it adds your recordings to myth database as you destroyed you old database hence the recordings no longer being present. 

you see just cause the files are there and your paths are correct doesn't mean your sql database knows the tv eps info from your old database as you destroyed it due to lack of planning and research 

the script as far as i know allows you to manually re enter each file adding title and description info which i can only assume is very tedious i can not walk you through the whole process as i have never needed it cause i already understand the basics of how the database works and have taken appropriate precautions such as db backups.

---

### Post by gsrcrxsi on 2008-11-20
thanks, but try to be less condescending next time...

---

### Post by oobe-feisty on 2008-11-21
> **gsrcrxsi said:**
> thanks, but try to be less condescending next time...


fair comment however it was not my intention to be condescending that link Stevi left will probably be more helpful i was merely pointing out i dont know the details of the operation and that it can be avoided altogether with research and planning

---

### Post by Chunder on 2008-11-22
Presume that permissions for the relevant directory are OK, and that you've updated the apparmor.d mysql file to allow access to the same?

This bit me a bit last night whilst upgrading to 8.10... may not be the same issue, but it took me ages to work out why mysqld wasn't running :(

---

