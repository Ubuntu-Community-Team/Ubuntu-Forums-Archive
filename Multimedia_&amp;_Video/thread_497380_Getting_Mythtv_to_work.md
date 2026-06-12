---
title: "Getting Mythtv to work"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by alex_in_welly on 2007-07-10
Dear all,

I am struggling to get this mythtv lark to work propperly. I have gone through all of the walk-throughs countless times and i always end up with the same error. Upon starting up the frontend and trying to watch tv it says; 'Could not connect to master backend server is it running? Is the IP address set for it in the set up program correct?' Or something to that effect anyway.

When i checked my log file it came out with:

2007-07-10 10:38:13.071 Using runtime prefix = /usr
2007-07-10 10:38:14.832 New DB connection, total: 1
2007-07-10 10:38:14.947 Connected to database 'mythconverg' at host: localhost
2007-07-10 10:38:15.082 Current Schema Version: 1160
Starting up as the master server.
2007-07-10 10:38:15.777 New DB connection, total: 2
2007-07-10 10:38:15.935 Connected to database 'mythconverg' at host: localhost
2007-07-10 10:38:16.111 EITHelper: localtime offset 1:00:00 
2007-07-10 10:38:16.226 TVRec(2) Error: Problem finding starting channel, settin
g to default of '3'.
2007-07-10 10:38:16.287 ChannelBase(2) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2007-07-10 10:38:16.292 New DB scheduler connection
2007-07-10 10:38:16.407 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2007-07-10 10:38:16.530 Main::Starting HttpServer
2007-07-10 10:38:16.653 Main::Registering HttpStatus Extension
2007-07-10 10:38:16.934 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-07-10 10:38:16.936 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!

It as an Apaptec AVC-2410 that i am trying to get running. If anyone can offer any help then it will be most appreciated!!

Cheers, Alex

---

### Post by uputer on 2007-07-10
I'm a Mythtv noob.   Heck, I'm a Linux noob but I had some suggestions for you to try.

Did you run mythfilldatabase?  Also, try starting the mythbackend.  

See what happens.  

So:
$ mythfilldatabase --refresh-all
$ mythbackend

If it doesn't work, try to do it as root.

---

### Post by Saubazi on 2007-07-10
> **alex_in_welly said:**
> Dear all,

I am struggling to get this mythtv lark to work propperly. I have gone through all of the walk-throughs countless times and i always end up with the same error. Upon starting up the frontend and trying to watch tv it says; 'Could not connect to master backend server is it running? Is the IP address set for it in the set up program correct?' Or something to that effect anyway.

When i checked my log file it came out with:

2007-07-10 10:38:13.071 Using runtime prefix = /usr
2007-07-10 10:38:14.832 New DB connection, total: 1
2007-07-10 10:38:14.947 Connected to database 'mythconverg' at host: localhost
2007-07-10 10:38:15.082 Current Schema Version: 1160
Starting up as the master server.
2007-07-10 10:38:15.777 New DB connection, total: 2
2007-07-10 10:38:15.935 Connected to database 'mythconverg' at host: localhost
2007-07-10 10:38:16.111 EITHelper: localtime offset 1:00:00 
2007-07-10 10:38:16.226 TVRec(2) Error: Problem finding starting channel, settin
g to default of '3'.
2007-07-10 10:38:16.287 ChannelBase(2) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2007-07-10 10:38:16.292 New DB scheduler connection
2007-07-10 10:38:16.407 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2007-07-10 10:38:16.530 Main::Starting HttpServer
2007-07-10 10:38:16.653 Main::Registering HttpStatus Extension
2007-07-10 10:38:16.934 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-07-10 10:38:16.936 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!

It as an Apaptec AVC-2410 that i am trying to get running. If anyone can offer any help then it will be most appreciated!!

Cheers, Alex

I think you have a long way yet...firstly your card - is it analogue or DVB? Have you been able to run your card outside the mythtv? For DVB cards kaffeine is an excellent testbench - for analogue cards tvtime or xawtv. Once you have the card running and kicking proceed to myth.

Now you've got errors about video sources and so on. So you need to shutdown mythbackend and then
run mythtv-setup. Define your input cards and connect them to the correct video sources - tune the channels and then you might get forward.

It is difficult to judge from that log but are yoiu running mythfrontend on the same machine with backend?
If yes use 127.0.0.1 as the address. Furthermore, are you running the stuff under a user called "mythtv" or your own user?

---

### Post by superm1 on 2007-07-10
> **uputer said:**
> I'm a Mythtv noob.   Heck, I'm a Linux noob but I had some suggestions for you to try.

Did you run mythfilldatabase?  Also, try starting the mythbackend.  

See what happens.  

So:
$ mythfilldatabase --refresh-all
$ mythbackend

If it doesn't work, try to do it as root.
Ick a few words of advice here.
Only start mythbackend this way:
```
sudo /etc/init.d/mythtv-backend restart
```
Your asking for permissions problems otherwise

---

