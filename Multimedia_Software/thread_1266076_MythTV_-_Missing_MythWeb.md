---
title: "MythTV - Missing MythWeb"
date: 2009-09-14
forum: Multimedia Software
---

### Post by badger_fruit on 2009-09-14
Following the guide found here --> [Ubuntu-8.10 Source Install - MythTV]("http://www.mythtv.org/wiki/Ubuntu-8.10_Source_Install")

I have noticed a few small things which I'd like to query here if I may ...

**1. The guide suggests creating a user for myth tv to run under:-**
> 
  creating the mythtv user

to run mythtv as its own user I created one (so the backend doesnt run as root)

sudo useradd mythtv
OK, done ... next line ...

> 
  mythtv database setup

You have to create a file for mythtv for databse connections ~mythtv/.mythtv/mysql.txt 
Problem ... when creating a user via shell, it does not create a home folder.
Now, I'm still a bit of a linux noob but when I tried this, it failed with "no such folder /home/mythtv" (or at least something similar).

To get around this I didn't bother with either of these steps, when I ran the myth-setup, it requested all this information from me anyway.  I suppose an alternative method would be to create the user using System > Admin > Users and Groups.


**2. MythWeb - where is it?!** Although the very same guide states at the beginning:-
> 
If you want mythweb as well - you need

 sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mysql
Although this was done, if I browse to my MythTV box I get the default apache "It works!" and of course, if I browse to MYTHV:6455, I get the Myth status page and NOT the expected MythWeb GUI.

Ok this is to be expected I suppose, the apache's conf.d folder had nothing relating to myth in there so figured it'll cover this later in the guide and sure enough, further down there's some additional tasks which read:-

> 
  mythweb

For mythweb I just created a symlink to the checked out mythweb in the /var/www:

sudo ln -s /usr/local/src/mythtv/mythplugins/mythweb /var/www/mythweb
# make sure data is writeable
sudo chown -R www-data /usr/local/src/mythtv/mythplugins/mythweb/data
OK, upon running the second command, I am told that "/usr/local/src/mythtv" does not exist; sure enough, a quick ls proves this.  Is there an additional package I need to install?  I copy/pasted the instructions from the guide to ensure nothing was missed out from the prerequesites.



**3. it may be wise to include in there somewhere about mythbackend needs to be manually run (unless the user creates the included init.d script that is!).**  I had such a headache earlier on trying to understand why nothing worked and that mythbackend doesn't seem to be installed as a service in Ubuntu (although I can't say I've used Mythbackend under any other distro to compare!).


Now, I will hold my hands up and admit I'm far from a hardened Linux user having only really tinkered with Suse for a year or so but I guess there's a number of people out there that the guide will help, but perhaps baffle or trip up along the way as it did with me.  Naturally, I don't want to edit the Wiki pages until someone with more experience in the Ubunutu 8.10 installation process can advise if what I am writing is my user-error or if indeed, there are small adjustments needing to be made.

Many thanks for reading through this, I hope that someone's able to offer some words of wisdom!

Rich

---

