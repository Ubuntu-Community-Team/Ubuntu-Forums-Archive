---
title: "Seperate Frontend does not connect"
date: 2010-02-20
forum: Mythbuntu
---

### Post by lerrup on 2010-02-20
I am trying to reestablish a frontend on my laptop after reinstalling.  I cannot get the thing to work at all. It must be connecting as I do not get asked for the settings when it is started. Instead, nothing happens that I can see.  The log reads:

Starting mythfrontend.real..
2010-02-20 22:54:28.273 mythfrontend version: branches/release-0-22-fixes [23565] [www.mythtv.org](www.mythtv.org)
2010-02-20 22:54:28.273 Using runtime prefix = /usr
2010-02-20 22:54:28.273 Using configuration directory = /home/lerrup/.mythtv
2010-02-20 22:54:28.274 MediaRenderer::HttpServer Create Error

Anyone know what this means?

thanks

---

### Post by nickrout on 2010-02-20
run mythbuntu-control-centre

go to the mysql tab.

click test mysql connection

report back.

---

### Post by lerrup on 2010-02-21
Well,  I tried and there is no database connection  - the details are okay as far as I know.

Any ideas?

---

### Post by ian dobson on 2010-02-21
Hi,

1) Can you ping the backend system?
2) Have you changed the my.cnf (MySQL config) so that mysql accepts connections from any IP rather than just localhost. Just comment out the bind line in my.cnf with a #.

Regards
Ian Dobson

---

### Post by lerrup on 2010-02-22
I have now amended the mysql file.  I don't know how to ping the database to be honest, but the control centre says "fail" when I test the connection with the database.

---

### Post by ian dobson on 2010-02-22
Hi,

ok to ping the backend go to the terminal prompt on the frontend then type:-

ping IP_ADDRESS_OF_BACKEND

To edit your Mysql configuration just open the config file (/etc/mysql/my.cnf) with an editor you know how to use. Look for the line 
bind-address           = 127.0.0.1

and change to
#bind-address           = 127.0.0.1

Save the file and restart the backend and see it it works.

Regards
Ian Dobson

---

### Post by azmyth on 2010-02-22
I'd also check the db permissions to make sure the db doesn't just allow from the localhost

mysql -uroot
mysgl>SELECT user, host, db, select_priv, insert_priv, grant_priv FROM mysql.db;

If this looks okay, I'd then turn on the mysql log file on the backend. Edit the /etc/mysql/my.cnf file and uncomment the general_log_file and general_log and restart mysql and then try connecting from the remote FE and when it fails look at the /var/log/mysql/mysql.log on the backend to see what error you get. Once you figure it out turn the log file off as it'll suck too many resources to keep on.

---

### Post by TheMiz on 2010-02-23
I am having a similar problem...

I am trying to get a Live CD Frontend to work on my Macbook Pro.  I have a Frontend/Backend already setup.  I actually have it setup to be recognized by my PS3 as a media server, and that works pretty well, but I can't get the Live CD to work.

I have edited MySQL on the Main Backend (through Mythbuntu Control Centre) to enable ethernet interfaces.  And when I start "Mythbuntu Live CD Frontend" I go to a "Mythbuntu Live Session Configuration"  I enter in the password, and the IP address of the Backend, and Test connection, it says "Test Results: Successful"

Then I hit start session, and I get to the Database configuration pages.  There I set up the IP address, port, and password, and then I hit Finish, and it all freezes up.

I ran mythfrontend from the command line, and I got this:

```
2010-02-23 05:11:32.405 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-23 05:11:32.422 Using runtime prefix = /usr
2010-02-23 05:11:32.422 Using configuration directory = /home/ubuntu/.mythtv
2010-02-23 05:11:32.423 MediaRenderer::HttpServer Create Error
2010-02-23 05:11:32.424 Empty LocalHostName.
2010-02-23 05:11:32.424 Using localhost value of ubuntu
2010-02-23 05:11:32.424 Testing network connectivity to '192.168.0.102'
2010-02-23 05:11:32.445 New DB connection, total: 1

```It was frozen there for about 15 minutes before I ^C'ed out of it.

Any ideas about this?

------

Edit:
Well my problems were:

#1: the port was setup wrong.  On my Frontend/Backend machine, the backend says something about port 6543, so I tried setting the frontend to port 6543 instead of leaving it at the default port  in the database configuration page.
#2: the time zone on the laptop and the timezone on the Backend did not match.

Now The live CD is working on my Macbook.

---

### Post by lerrup on 2010-02-23
Thanks for your help-I can now get the database to connect in the mythbuntu-control-centre.


The frontend still won't start!

The says the same as previously, which is not really any help,and ends with:

2010-02-23 06:46:55.208 New DB connection, total: 1

?

---

### Post by nickrout on 2010-02-23
> **lerrup said:**
> Thanks for your help-I can now get the database to connect in the mythbuntu-control-centre.


The frontend still won't start!

The says the same as previously, which is not really any help,and ends with:

2010-02-23 06:46:55.208 New DB connection, total: 1

?

And then what happens? What do you see on the frontend screen?

---

### Post by lerrup on 2010-02-24
This is the problem, there is nothing on the screen at all.  

The frontend manages to grab the sound (the laptop has pulseaudio running) and mythfrontend also appears in the list of running apps.  It does not appear in the taskmanager/taskbar (it is the same in gnome or KDE so the problem isn't there...)

---

### Post by lerrup on 2010-02-26
Running from konsole gives the output on the attached file.

But no sign of the frontend...

---

### Post by nickrout on 2010-02-26
what command are you running to get that output?

---

### Post by Lepy on 2010-02-26
I'm actually having the same problem after a new install and a restore of my old database, except I've been mainly talking to myself. 
For my long post see: [http://ubuntuforums.org/showthread.php?t=1414529](http://ubuntuforums.org/showthread.php?t=1414529)

Read and attempt the multiple systems portion of the Chapter 6 docs: [http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)
Remember to issue the mysql commands from the main backend for now.
After this, the test connecting in mythbuntu control centre should work.

I was still having frontend connection issues after this even though the test connection worked. It turns out that even though I had the ports set to 6543 in mythtv-setup on the main backend, they weren't working. A portscan showed 6543 as open but unknown. I changed all the mysql.txt and config.xml references of DBPort=6543 to DBPort=3306 (default mysql port). 

This successfully connected the frontends, but they still sometimes fail with a hang at MediaRenderer::HttpServer Create Error. If I ^C and run the mythfrontend.real -v all command a few more times, it will eventually start.

I hope this can help you at least connect the frontends some of the time. Hopefully we can solve this hang at MediRenderer.

---

### Post by lerrup on 2010-02-27
thanks- it turns out it was running on port 3306 as well.

Odd.

Does this need to be reported as bug?

---

### Post by nickrout on 2010-02-27
what bug? mysql's default port is 3306.

mythtv's backend runs on port 6543.

do not confuse the two!

---

### Post by Lepy on 2010-02-27
Yes very odd and made me waste a bit of time trying to sort it out. It may very well be a bug, but I won't rule out that I messed something up during the database restore. 

The only things I changed were the mysql root and mythtv database password.

Are your ports set to something different in mythtv-setup?

---

### Post by nickrout on 2010-02-27
It is not a bug! mysql runs on 3306. mythbackend runs on 6543. Thats how it should be.

---

### Post by Lepy on 2010-02-27
I understand that mysql and the mythbackend run on different ports, but after the install/restore, why can I no longer access the mythbackend mysql database through port 6543, even though I have that port set in the mythtv-setup -> General?

Does mythfrontend by default connect using port 3306? It seems that using port 3306 causes the frontend to start up much slower and creates this hang at MediaRenderer::HttpServer Create Error.

---

### Post by lerrup on 2010-02-28
Also, all the documentation I found says that you need to use port 6543 and no 3306, that's why 6543 is the default.

So it seems to me that either that's wrong or there is something goes wrong when you have a database that is restored, as I did when I reinstalled mythtv on the backend.  Previously, it had connected on 6543.

Odd, hey?

---

### Post by nickrout on 2010-02-28
> **Lepy said:**
> I understand that mysql and the mythbackend run on different ports, but after the install/restore, why can I no longer access the mythbackend mysql database through port 6543, even though I have that port set in the mythtv-setup -> General?

Does mythfrontend by default connect using port 3306? It seems that using port 3306 causes the frontend to start up much slower and creates this hang at MediaRenderer::HttpServer Create Error.


What is it you are finding hard to understand? you have nnever been able to contact mysql on port 6543. It always runs on 3306. the backend runs on 3306, the mysql daemon rins on 3306.

---

### Post by lerrup on 2010-02-28
> **nickrout said:**
> What is it you are finding hard to understand? you have nnever been able to contact mysql on port 6543. It always runs on 3306. the backend runs on 3306, the mysql daemon rins on 3306.

I think the confusion comes from the fact that I have never had to change the port to get a frontend connected before now.

Oh, that and all the documentation saying that you should use 6543 to connect...

---

### Post by nickrout on 2010-02-28
> **lerrup said:**
> I think the confusion comes from the fact that I have never had to change the port to get a frontend connected before now.

Oh, that and all the documentation saying that you should use 6543 to connect...

It can only be because you set it that way in the first place, which I assume you did by accident.

mythtv-setup sets the port that the backend runs on, the default is 6543.

when you start the frontend for the first time, or if it is unconfigured, you set it up so it knows where to find the database that the frontend connects to to get the rest of it's settings. As it can't connect to a database without knowing where the database is (chicken/egg) it saves this info in mysql.txt and/or config.xml. mysql runs on 3306 and this is where you set that.

If you got the mythtv-setup screen confused with the frontend initial setup screen you may have put the wrong number somewhere.

---

### Post by kickinthethroat on 2010-08-15
> **nickrout said:**
> 

If you got the mythtv-setup screen confused with the frontend initial setup screen you may have put the wrong number somewhere.

This is what I did, and this thread helped me sort it out.  My frontend wasn't connecting, so the first thing I did was type the port 6543 into the DB port field, which isn't correct.  Turns out the DB password changed, which is the real reason why it wasn't connecting, so I changed that, but it still didn't connect because I put the 6543 into the wrong area!  Fixed now though, thanks.

---

