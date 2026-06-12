---
title: "Xbmc - Mythtv"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-04-09
I've setup my xbox with the xbmc mythtv plugin: 

[http://sourceforge.net/projects/xbmcmythtv/](http://sourceforge.net/projects/xbmcmythtv/) 

and it seems that the protocol is different as the xbox won't connect to the backend. 

What version of mythtv is in the repos? what protocol version is included in it?

The XBMC plugin is protocol version 31.

Do you use this plug in?

Cheers Dubstsar_04

---

### Post by barney_1 on 2007-04-09
The version of mythtv in the repos is 0.20.  That should be the same version of XBMC mythtv script you have installed (I am running 0.20.31 on xbmc).

You are probably having a mySQL permissions problem.  You see, the mythconverg database restricts access via ip addresses.  Try this on your mythtv box:

```
    $ mysql -u root mythconverg
    mysql> grant all on mythconverg.* to mythtv@"192.168.1.%" identified by "mythtv";
    mysql> flush privileges;

```

---

### Post by Dubstar_04 on 2007-04-09
I have tried this and it hasn't made any difference. the protocol version listed in the xbmc plugin is listed as 30, yet the name is 20.31. does this value need chaging to 31?

do you use this on your xbmc? if so does it work well? also when did you install your myth install as there has recently been an up date. I'm running feisty with the latest myth from the repos.

Anything else you can suggest? Thanks for your help.

---

### Post by superm1 on 2007-04-09
The protocol in the version of the repositories is indeed 31.
Can't comment on the version in the xbmc plugin though.  You can manually try to change the xbmc plugin to 31 if its 30, but no guarantees that will continue to work.

---

### Post by barney_1 on 2007-04-10
I'm running mythtv on an Edgy box.  Once you get the thing working, there's no reason to upgrade to a non-stable version.

---

### Post by Dubstar_04 on 2007-04-10
I had major problems with EDGY so I tried Feisty on the off chance that the problems would be solved and they were. Mythbox has been fine so far (2 weeks) just want to get the xbox sorted now for the bedroom. 

Weird thing when in the settings in the xbmc plugin it says they are wrong but when i go to the main xbmx myth menu it can see what is due to record and if it is recording at present, but nothing else will work, plus i can't connect at all if im using a openbox session, not even to view the videos folder!!

---

### Post by barney_1 on 2007-04-11
That makes it sound like a networking problem.  Is it possible you don't have your samba share set up correctly?  Try adding a shortcut in the "my videos" area of XBMC and see if you can view the .mpg files that mythtv has recorded.  If you can get them to play manually, then you know that you have the share set up correctly and it is the XBMCmythtv script settings that are the problem.

---

### Post by Dubstar_04 on 2007-04-11
when i'm logged into a gnome session the networking is fine i can access everything shared on my mythbox. however when i log into a openbox session i am unable to access the folders!!!

I was assuming that the samba sharing may not be started using an openbox session an that i needed to add somthing to my 'mythtv' session to make it work?!?

---

### Post by barney_1 on 2007-04-12
As I said:
> **barney_1 said:**
> Try adding a shortcut in the "my videos" area of XBMC and see if you can view the .mpg files that mythtv has recorded.

---

### Post by rolen on 2007-10-09
Not sure if you are still having this problem but i had similiar issue with Feisty and have just managed to solve it. What is looks like is that the mysql server that is installed hashes the passwords differently than the way the xbmc mythtv mysql python client does in order to fix it you have to change the hash of the password in the database. 

If you catch the exception being thrown in mythtv.py def initialise( self ): where it calls mysql.connect you get the error(can post the code change if you want)
Client does not support authentication protocol 

Followed the instructions in this page and it worked for me
[http://dev.mysql.com/doc/refman/5.0/en/old-client.html](http://dev.mysql.com/doc/refman/5.0/en/old-client.html)

Rob

---

### Post by rolen on 2007-10-10
Did some more testing with this, be very careful when changing the password to the old hash cause(pretty obvious now i think about it) the myth front end and backend(i think) rely on using the new hash, and this breaks them, so i am going to have to find another way around this.

Rob

---

### Post by mstorm on 2007-10-10
Thanks for the tip, worked like a charm (well, almost at least)

My only problem: "Test settings" kept telling me that it couldn't connect to the database, but once I exited and restarted MythTV everything seemed to work fine and running "test settings" again tells me all is ok.

What I did to get around the problems you were talking about, was to create a new user, which is a copy of the mythtv user, so that the Xbox can login using an old-style password, while the front/backends on my Ubuntu computer can login as usual.

---

### Post by dchurch24 on 2007-11-29
Hi, as I'm a complete noob when it comes to MySQL (and Linux really), I wonder if you might post easy to understand instructions on how to do this.

I have no experience with setting up users or copying them in MySQL.

I am having the exact same problem with the XBMC script.

---

### Post by dchurch24 on 2007-11-29
Well, I've created a user 'dave'@'localhost' and then I did:

set password for 'dave'@'localhost' = OLD_PASSWORD('password');

flushed it all, but I still get the same error.

Any clue?

---

### Post by dchurch24 on 2007-11-29
Dunce! (Smacks own head!)

I didn;t need localhost - I needed the IP of the xbox!

It's working now, apart from actually streaming live TV, but I think I have the share set up wrong.

---

### Post by barney_1 on 2007-12-04
I have liveTV steaming working.  Perhaps make sure you have checked out the latest copy of the cvs.

```
cvs -d:pserver:anonymous@xbmcmythtv.cvs.sourceforge.net:/cvsroot/xbmcmythtv login
 
cvs -z3 -d:pserver:anonymous@xbmcmythtv.cvs.sourceforge.net:/cvsroot/xbmcmythtv co -P xbmcmythtv
```

Then ftp that over to your box.

---

