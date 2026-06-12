---
title: "Frontend won't start"
date: 2010-11-13
forum: Mythbuntu
---

### Post by Colonelguf on 2010-11-13
I have a machine I was planning to use as a remote frontend. I installed Mythbuntu 10.04 and it worked. A few days later, I tried to use it again and the frontend wouldn't start. I decided to reinstall, and after reinstallation it gave me the language selection screen, then the screen where I enter the password for the backend, then nothing. When I start it from a terminal i get:

```

2010-11-13 14:28:19.512 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-11-13 14:28:19.512 Using runtime prefix = /usr
2010-11-13 14:28:19.512 Using configuration directory = /home/alesch/.mythtv
2010-11-13 14:28:20.382 Empty LocalHostName.
2010-11-13 14:28:20.382 Using localhost value of alesch-brmythtv
2010-11-13 14:28:20.382 Testing network connectivity to '10.0.0.252'
2010-11-13 14:28:20.403 New DB connection, total: 1

```then nothing happens.
I have no mythtv log files in /var/log.
When I open MCC and test db connectivity it connects OK.

Can anyone give me some pointers here?
Thanks

---

### Post by ArielEnter on 2011-12-24
Hi, I was having the same issue, and I found that I was doing something wrong: I was trying to use 6543 in the remote frontend as the port for the database server, but usually mysql uses 3306, so I was suppose to leave that blank (which tells the frontend to use the 3306 by default).

I started using 6543 because the frontend kept complaining about being unable to connect to the backend the first time I left it blank. Thank god I found where the log is and I found what was exactly happening. To read the log go to /var/log/mythtv/mythfrontend.log 

You got to run mythfrontend from the menu, otherwise if you run it from the terminal no log info will be generated.

Any way I found the following message there:

MythCoreContext: Connecting to backend server: 127.0.0.1:6543

And that told me that even though my remote frontend knew where to find the database, it didn't know where the backend was. So this is were the tricky part came. You are suppose to go to your backend computer and run mythtv-setup, to configure the backend on the general section and tell it not to use 127.0.0.1 as the master backend ip address but its actual ip adress in the network, which should be the same you use for the database address on your remote frontend. So basically you should replace all 127.0.0.1 on the backend to its actual ip.

Look here [http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4](http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4) in the Frontend-only configuration section.

To tell you the true I think mythtv could be a little more user friendly and recommend you the manual to do a remote connection. Oh well is just my opinion.

---

### Post by Colonelguf on 2011-12-25
> **ArielEnter said:**
> Hi, I was having the same issue, and I found that I was doing something wrong: I was trying to use 6543 in the remote frontend as the port for the database server, but usually mysql uses 3306, so I was suppose to leave that blank (which tells the frontend to use the 3306 by default).
 
I started using 6543 because the frontend kept complaining about being unable to connect to the backend the first time I left it blank. Thank god I found where the log is and I found what was exactly happening. To read the log go to /var/log/mythtv/mythfrontend.log 
 
You got to run mythfrontend from the menu, otherwise if you run it from the terminal no log info will be generated.
 
Any way I found the following message there:
 
MythCoreContext: Connecting to backend server: 127.0.0.1:6543
 
And that told me that even though my remote frontend knew where to find the database, it didn't know where the backend was. So this is were the tricky part came. You are suppose to go to your backend computer and run mythtv-setup, to configure the backend on the general section and tell it not to use 127.0.0.1 as the master backend ip address but its actual ip adress in the network, which should be the same you use for the database address on your remote frontend. So basically you should replace all 127.0.0.1 on the backend to its actual ip.
 
Look here [http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4](http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4) in the Frontend-only configuration section.
 
To tell you the true I think mythtv could be a little more user friendly and recommend you the manual to do a remote connection. Oh well is just my opinion.
 
Thanks for the info. Its been a while, but what I think I did was reinstall again and wipe out all the partitions. The first time I reinstalled I kept the Home partition, and that didn't work. I still don't know what the issue was that I had. Yeah, I agree that Mythtv is a little difficult to get set up correctly, but I seem to get it eventually.

---

