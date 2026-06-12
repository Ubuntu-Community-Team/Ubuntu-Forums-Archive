---
title: "mythlink.pl not working: Unable to connect to mythbackend, is it running?"
date: 2014-06-23
forum: Mythbuntu
---

### Post by xmrkite on 2014-06-23
When I run mythlink.pl, it returns:
Unable to connect to mythbackend, is it running?

I'm using mythbuntu 14.04 on a fresh install. I'd love to get filenames I can understand for my recordings.

How can I get this fixed?

-Thanks for any help

---

### Post by blm-ubunet on 2014-06-24
mythlink.pl gets its dB credentials from ~/.mythtv/config.xml.
This path depends on the actual user invoking the cmd.
The BE runs as user "mythtv" & your desktop session could be different user therefore possibly different config.xml.
Try invoking mythlink as user "mythtv".

---

### Post by xmrkite on 2014-06-24
All the config,xml files are set to localhost and user and password mythtv

That includes the /home/mythtv/.mythtv/config.xml, /home/myhome/.mythtv/config.xml and /etc/mythtv/config.xml files

The frontend loads fine.

Any other ideas?

---

### Post by blm-ubunet on 2014-06-24
Did you try to run script as user "mythtv"?

- login session as "mythtv"
- switch to user "mythtv" with su -l in terminal
- set environment [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]MYTHCONFDIR[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]="/home/mythtv" variable for the terminal/script.
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]$MYTHCONFDIR[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by xmrkite on 2014-06-24
None of those things worked. I can't log on as mythtv as I think it's a system account. The odd thing is that my user can open mythfrontend just fine...should it also be able to run mythlink.pl fine?

---

### Post by blm-ubunet on 2014-06-25
This mythlink script is the one that came with mythtv install or something found on the internet?

Need to see log files (BE & script in terminal).

---

### Post by xmrkite on 2014-06-25
It's the one that came with the mythtv install. I'll try to see if I can find something in the logs.

---

### Post by khPWXxF on 2014-06-29
You say that the user/password set in /etc/mythtv/config.xml is mythtv/mythtv.
That contradicts my understanding of how a 14.04 Mythbuntu system is set up.  To recap on usernames and passwords with a straight Mythbuntu:

1. There is a login username - you chose the name and a password during installation.  Frontend runs under this username, and you can do any maintenance work from it.  Files owned by it are held in /home/youruser or (as a shorthand) ~

2.  There is also a user called mythtv.  Backend runs under this.  I don't know the password for this and have never logged in to it (nor root user either) - I use sudo if I need to do any maintenance.  However, you could I suppose login to it.

3.  To access the mysql database you need a username and password. I don't know whether the username must match a 'Linux' username but I suspect not.    On a 14.04 system the username for the mythtv application suite is 'mythtv' and the password is a random string (lots of Zs and qs on mine - I can't pronounce it!).  There are links from ~/.mythtv/config.xml and /home/mythtv/.mythtv/config.xml to a real file /etc/mythtv/config.xml which holds that database username and password and is read by programs like backend to get the user/password to access the database.     I'm very wary of using this user/password to access the database directly.

I have seen references to accessing the database with user=mythtv and password=mythtv.  A straight mythtv installation may or may not use that (I just don't know) but in a straight unadulterated mythbuntu environment it is wrong.

Is your password in /etc/mythtv/config.xml really set to 'mythtv'?

hth
Phil

---

### Post by xmrkite on 2014-06-29
So the default password was similar to what you describe, but I changed it to mythtv using directions from here:
[http://www.mythtv.org/wiki/User_Manual:Initial_Installation](http://www.mythtv.org/wiki/User_Manual:Initial_Installation)

I did this to be sure I was connecting. I am able to open a terminal and run: **mysql -u mythtv -p ** and can use mythtv as the password. This lets me in just fine. So I'm 100% sure that mythtv is also now the password for mysql user mythtv.

When I changed that password, I had to update those config.xml files to also say mythtv as the password. Please keep in mind that mythlink.pl did not work from the get go and this is why I changed the password to begin with.

What log file should I look at to find any errors?

---

### Post by xmrkite on 2014-06-29
Couldn't I just manually modify a few lines in that mythlink.pl file to specify the database connection info? I'm just not sure how to do this?

---

### Post by khPWXxF on 2014-06-30
Ok, so doesn't sound like a password issue.
Does --verbose give more?  See [http://www.mythtv.org/wiki/Mythlink.pl](http://www.mythtv.org/wiki/Mythlink.pl)
Phil

---

### Post by xmrkite on 2014-06-30
Ya, I tried that and there is no extra output. The exact same message appears.

---

### Post by blm-ubunet on 2014-06-30
FWIW..this script does not ship with mythtv, so you might have an old copy that does not understand config.xml
This is where I source these scripts..
[https://github.com/wagnerrp/mythtv-scripts](https://github.com/wagnerrp/mythtv-scripts)

This script (mythlink) does not run/work with python2.7 (in my ubuntu 14.04 upgraded from 12.04LTS).

---

### Post by xmrkite on 2014-06-30
Hmm, so what can I do for now then?

---

### Post by blm-ubunet on 2014-07-01
From further testing in the last 5 minutes.. the mythlink script from git does not run on my Ubuntu 10.04 python2.6 system.
And does not run on 14.04 lubuntu python2.7.

Both of these systems run git master mythtv 0.28.
I would guess my script errors are to do with changes in the language bindings in the source code & not the script.

So your error is not that the script does not work in python2.7.
Your error is in not connecting or finding dB credentials, so clearly different.

Check the version of your script & compare to the git.
You can checkout the git repo to your home folder..no compiling required.

mythlink.py -v
 Python scripts are just text files, you can cat them or view in editor.

---

### Post by xmrkite on 2014-07-01
> **blm-ubunet said:**
> 
mythlink.py -v
 Python scripts are just text files, you can cat them or view in editor.

Ok that gave the same error....very odd.

Also, I tried downloading mythlink.py from [https://github.com/wagnerrp/mythtv-scripts/blob/master/python/mythlink.py](https://github.com/wagnerrp/mythtv-scripts/blob/master/python/mythlink.py) and that did not work.

That gave an error on line 98.

---

### Post by blm-ubunet on 2014-07-02
A very important difference between mythlink.py from that git repo & your "perl" version is:
- yours is the original as written in perl & it does ship with mythtv (not what I said before).
- the git repo (linked previous) is a re-write in python
- the original perl script works here.

---

### Post by xmrkite on 2014-07-02
Ok, where can I download the original perl script just to make sure I have the correct one? I thought I had been using the original one, but maybe I'm wrong.

---

### Post by xmrkite on 2014-07-02
While looking at the mythlink.pl file, I noticed the date modified is 7-21-2013 and inside the file I noticed it says:

"Automatically detects database settings from mysql.txt"

BUT...mythbuntu does not have or use this file anymore as it uses an xml file. How the heck does this file connect? Could I change it to point to the correct xml file?

Why would they ship this and not have updated this old file that is for old myth installs? Also, my mythtv logs show nothing when I try to run the script.

---

### Post by blm-ubunet on 2014-07-04
From looking at the code ..(perl mythlink.pl).
There is no code reference to mysql.txt or config.xml.
It does not access mysql.txt (I don't have this file any more).
I don't think this code has changed in years.

I guess it connects to a running BE & accesses the dB thru' that.
A running BE always has dB connection.

---

### Post by xmrkite on 2014-07-04
Basically, i'm stuck with waiting for someone to update the code. Mine is a fresh install, it doesn't work. My backend is obviously running. Also, I noticed a bunch of the features in the mythtv control centre don't work either. Like backups, vnc, the remote etc. I had to set those up manually as the control center crashes a lot. I had considered going plain xubuntu and adding mythtv after all that, but I was able to get them all working, so that was easier.

But if I can't get this script to work, should I just do a complete reinstall after backing up the database? That is starting to sound easier at this point.

---

### Post by blm-ubunet on 2014-07-04
I don't see why re-installing would make any difference.

Do you have libmythtv-perl package installed?
If that was missing then the other (perl) scripts would fail as well.

---

### Post by xmrkite on 2014-07-04
Yes, it's installed. (2:0.27.2+fixes..20170702.7e34d53-0ubuntu0mythbuntu3)

---

### Post by blm-ubunet on 2014-07-04
It that the output from:
sudo dpkg -l libmythtv-perl
or
sudo dpkg -l libmythtv*
?

---

### Post by xmrkite on 2014-07-05
sudo dpkg -l libmythtv* produces:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version              Architecture         Description
+++-===============================-====================-====================-====================================================================
ii  libmythtv-perl                  2:0.27.2+fixes.20140 all                  A PERL library to access some MythTV features

---

