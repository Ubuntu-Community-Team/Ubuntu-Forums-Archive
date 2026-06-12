---
title: "Can't Connect to Backend"
date: 2012-11-02
forum: Mythbuntu
---

### Post by Morffinator on 2012-11-02
I've just been setting up mythtv and I am getting the error that it can't connect to the backend.

I have checked the ip multiple times and it is a combined frontend and backend machine. I have been able to setup the tuner in the backend with no issue at all.

When I go into the frontend machine and select live tv it immediately drops me back out to the menu.

I have no idea why this is happening so am hoping someone may be able to help as it is the only thing stopping me going live with this machine.

Thanks in advance for the help.

Edit:
I am getting the following when running ```
/usr/bin/mythbackend
```

```

/usr/bin/mythbackend
2012-11-02 21:35:55.412102 C  mythbackend version: fixes/0.25 [v0.25.3] [www.mythtv.org](www.mythtv.org)
2012-11-02 21:35:55.412127 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-11-02 21:35:55.412131 N  Enabled verbose msgs:  general
2012-11-02 21:35:55.412153 N  Setting Log Level to LOG_INFO
2012-11-02 21:35:55.412213 I  Added logging to the console
2012-11-02 21:35:55.412220 I  Added database logging to table logging
2012-11-02 21:35:55.412313 N  Setting up SIGHUP handler
2012-11-02 21:35:55.412392 N  Using runtime prefix = /usr
2012-11-02 21:35:55.412408 N  Using configuration directory = /home/media/.mythtv
2012-11-02 21:35:55.412634 I  Assumed character encoding: en_AU.UTF-8
2012-11-02 21:35:55.413111 N  Empty LocalHostName.
2012-11-02 21:35:55.413118 I  Using localhost value of HTPC
2012-11-02 21:35:55.439543 N  Setting QT default locale to en_AU
2012-11-02 21:35:55.439648 I  Current locale en_AU
2012-11-02 21:35:55.439721 E  No locale defaults file for en_AU, skipping
2012-11-02 21:35:55.443644 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-11-02 21:35:55.444101 I  Loading en_us translation for module mythfrontend
2012-11-02 21:35:55.444998 N  MythBackend: Starting up as the master server.
2012-11-02 21:35:55.451322 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.501449 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.551619 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.601738 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.651905 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.702018 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.752171 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.802287 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.852443 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.902554 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:55.952708 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.002823 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.052983 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.103093 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.153245 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.203354 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.253510 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.303619 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.353771 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.403879 W  DVBChan(5:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.403895 E  DVBChan(5:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-11-02 21:35:56.403909 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-11-02 21:35:56.403998 E  Problem with capture cardsCard 5failed init
2012-11-02 21:35:56.405267 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.455421 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.505529 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.555678 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.605786 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.655936 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.706046 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.756195 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.806306 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.856459 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.906569 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:56.956717 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.006860 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.057019 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.107129 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.157276 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.207385 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.257534 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.307641 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.357791 W  DVBChan(6:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.357812 E  DVBChan(6:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-11-02 21:35:57.357827 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-11-02 21:35:57.357866 E  Problem with capture cardsCard 6failed init
2012-11-02 21:35:57.359059 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.409165 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.459310 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.509418 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.559564 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.609672 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.659813 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.709922 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.760065 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.810175 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.860317 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.910425 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:57.960568 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.010676 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.060819 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.110960 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.161120 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.211303 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.261464 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.311574 W  DVBChan(7:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.311591 E  DVBChan(7:/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-11-02 21:35:58.311606 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
2012-11-02 21:35:58.311643 E  Problem with capture cardsCard 7failed init
2012-11-02 21:35:58.312804 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.362949 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.413091 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.463239 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.513355 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.563503 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.613617 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.663762 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.713878 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.764025 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.814144 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.864284 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.914402 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:58.964557 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:59.014677 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:59.064828 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:59.114948 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:59.165104 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:59.215317 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:59.265511 W  DVBChan(8:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2012-11-02 21:35:59.265536 E  DVBChan(8:/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-11-02 21:35:59.265552 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
2012-11-02 21:35:59.265594 E  Problem with capture cardsCard 8failed init
2012-11-02 21:35:59.265621 W  MythBackend: No valid capture cards are defined in the database.
2012-11-02 21:35:59.269422 I  Found 1 distinct programid authorities
2012-11-02 21:35:59.269854 I  New static DB connectionSchedCon
2012-11-02 21:35:59.287003 E  Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in use
2012-11-02 21:35:59.287067 E  MediaServer::HttpServer Create Error
2012-11-02 21:35:59.289157 E  Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in use
2012-11-02 21:35:59.289185 C  Backend exiting, MainServer initialization error.
2012-11-02 21:36:09.272427 I  Running housekeeping thread

```

So obviously I have some issues to resolve there and would appreciate any help

---

### Post by PhilWig on 2012-11-02
Hi there,
  this looks important:
> MythBackend: No valid capture cards are defined in the database.
Have you set them up in the backend setup program?

I expect you'll need to say where are you, what signal are you trying to capture and what capture card(s) you are using in order to get a more specific reply. 
Phil

---

### Post by Morffinator on 2012-11-02
> **PhilWig said:**
> Hi there,
  this looks important:

Have you set them up in the backend setup program?

I expect you'll need to say where are you, what signal are you trying to capture and what capture card(s) you are using in order to get a more specific reply. 
Phil
Yes I have managed to setup the tuners and tune in channels.

Sorry I forgot to put that I am using a Sony PlayTV. And I am in Australia. I am trying to capture digital TV.

---

### Post by N00b-un-2 on 2012-11-02
I've run into issues like this with Myth before.  Typically when this kind of thing goes wrong it's one of two issues.  Either A) something got hosed in your mythbackend setup, or your MySQL database is messed up.  Unfortunately, there's no easy way to trouble shoot it aside from taking a very systematic approach.

First things first -- it looks like you need to run myth setup and initialize your tuner card by scanning for channels.  Once you're done doing that if the problem persists there are a couple things you can try.

Are you sure your TV tuner card can capture the digital TV signals in your area?  I have a TV tuner card (happuage) that can ONLY do digital but not analog, and only some of the digital channels because of incompatibilities with the broadcast format.  Some of the broadcast channels here in AZ are in some form of MPEG that my old tuner couldn't grab, but after upgrading to an HD HomeRun I had no such issues.

If it does turn out to be a MySQL issue, In my experience it's better to just nuke the whole database and rebuild it.  It's not hard to do and it ensures that it's configured right.

---

### Post by Morffinator on 2012-11-02
> **N00b-un-2 said:**
> I've run into issues like this with Myth before.  Typically when this kind of thing goes wrong it's one of two issues.  Either A) something got hosed in your mythbackend setup, or your MySQL database is messed up.  Unfortunately, there's no easy way to trouble shoot it aside from taking a very systematic approach.

First things first -- it looks like you need to run myth setup and initialize your tuner card by scanning for channels.  Once you're done doing that if the problem persists there are a couple things you can try.

I've run setup and I have scanned for channels which it picks up no problem.
> 
Are you sure your TV tuner card can capture the digital TV signals in your area?
Sure am. 
 > 
If it does turn out to be a MySQL issue, In my experience it's better to just nuke the whole database and rebuild it.  It's not hard to do and it ensures that it's configured right.
Okay so I am thinking it is MySQL issue so how would I blow away the MySQL database? Possibly I screwed it up whilst I was setting things up.

---

### Post by nickrout on 2012-11-02
Back up a moment. Your first post is confusing, you refer to a backend/frontend machine, but then you talk about going to the "frontend machine". So what exactly IS your setup?

Also your log (at the end) talks about 127.0.0.1 so if you DO have a separate backend and frontend, it will not work. You need to set the machine's externally accessible IP address (usually 192.168.x.y) in two places in the first screen of mythtv-setup on the backend.

---

### Post by Morffinator on 2012-11-02
> **nickrout said:**
> Back up a moment. Your first post is confusing, you refer to a backend/frontend machine, but then you talk about going to the "frontend machine". So what exactly IS your setup?
It is a combined backend/frontend machine. I would have meant going into the frontend interface of the machine.
> 
Also your log (at the end) talks about 127.0.0.1 so if you DO have a separate backend and frontend, it will not work. You need to set the machine's externally accessible IP address (usually 192.168.x.y) in two places in the first screen of mythtv-setup on the backend.
Being a combined backend/frontend machine I have left it as 127.0.0.1

---

### Post by nickrout on 2012-11-02
> **Morffinator said:**
> It is a combined backend/frontend machine. I would have meant going into the frontend interface of the machine.

Being a combined backend/frontend machine I have left it as 127.0.0.1
OK then what do you mean "I have checked that IP multiple times" ?

Also as the messages say that it is trying to open adapter1 - so you have two capture crads (the numbering is 0 based). Have you set up BOTH capture devices and bound them BOTH ot the same video source?

---

### Post by Morffinator on 2012-11-02
> **nickrout said:**
> OK then what do you mean "I have checked that IP multiple times" ?
That I have made sure it hasn't changed from that.
> 
Also as the messages say that it is trying to open adapter1 - so you have two capture crads (the numbering is 0 based). Have you set up BOTH capture devices and bound them BOTH ot the same video source?
The output I posted first up shows it trying to open adapter0 first then adapter1. It is a dual tuner and both have been setup to the same video source.

---

### Post by nickrout on 2012-11-02
> **Morffinator said:**
> That I have made sure it hasn't changed from that.

The output I posted first up shows it trying to open adapter0 first then adapter1. It is a dual tuner and both have been setup to the same video source.Hold on I just re-read your first post.

Do NOT run mythbackend from the commandline. Start it properly as a service.```
sudo service mythtv-backend start
```

---

### Post by Morffinator on 2012-11-02
> **nickrout said:**
> Hold on I just re-read your first post.

Do NOT run mythbackend from the commandline. Start it properly as a service.```
sudo service mythtv-backend start
```
I only ran it the way I did before to check what was going on.

I've done what you said but it still hasn't improved.

---

### Post by nickrout on 2012-11-02
> **Morffinator said:**
> I only ran it the way I did before to check what was going on.

I've done what you said but it still hasn't improved.

You check what is going on via the logs in /var/log/mythtv. STarting it as user media (which you seemed to have done) is quite different to starting the service which will start it as user mythtv.

What are the ownership and permissions on /dev/dvb/adapter0/frontend0 ?

should be ```
crw-rw----+ 1 root video 212, 3 2012-09-29 00:44 /dev/dvb/adapter0/frontend0
```

Are any other processes holding the device open?

```
lsof|grep frontend0
```

---

### Post by nickrout on 2012-11-02
I find the logs in this forum hard to read with the scrolling text box and much of the meat off to the right.

> 2012-11-02 21:35:59.287003 E  Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in use
2012-11-02 21:35:59.287067 E  MediaServer::HttpServer Create Error
2012-11-02 21:35:59.289157 E  Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in use
2012-11-02 21:35:59.289185 C  Backend exiting, MainServer initialization error.


Indicates to me that something already has the mythtv ports (6544 and 6543) open - are you sure mythbackend wasn't already running - I can't think what else would have grabbed those ports.

mythbackend starts automatically on boot, so unless you stopped it before you ran mythbackend, it will probably already have been running in which case finding that the dvb devices and ports were already in use would make perfect sense.

May I suggest you restart the machine so we are back to square one, then try ```
ps aux|grep backend
```and post the results.

---

### Post by Morffinator on 2012-11-03
> **nickrout said:**
> You check what is going on via the logs in /var/log/mythtv. STarting it as user media (which you seemed to have done) is quite different to starting the service which will start it as user mythtv.

What are the ownership and permissions on /dev/dvb/adapter0/frontend0 ?

should be ```
crw-rw----+ 1 root video 212, 3 2012-09-29 00:44 /dev/dvb/adapter0/frontend0
```

it is as follows:
```

media@mythtv:/dev/dvb/adapter0$ ls -l
total 0
crw-rw----+ 1 root video 212, 0 Nov  3 14:23 demux0
crw-rw----+ 1 root video 212, 1 Nov  3 14:23 dvr0
crw-rw----+ 1 root video 212, 3 Nov  3 14:23 frontend0
crw-rw----+ 1 root video 212, 2 Nov  3 14:23 net0

```

> 
Are any other processes holding the device open?

```
lsof|grep frontend0
```
Nothing comes up.

---

### Post by Morffinator on 2012-11-03
> **nickrout said:**
> I find the logs in this forum hard to read with the scrolling text box and much of the meat off to the right.



Indicates to me that something already has the mythtv ports (6544 and 6543) open - are you sure mythbackend wasn't already running - I can't think what else would have grabbed those ports.

mythbackend starts automatically on boot, so unless you stopped it before you ran mythbackend, it will probably already have been running in which case finding that the dvb devices and ports were already in use would make perfect sense.

May I suggest you restart the machine so we are back to square one, then try ```
ps aux|grep backend
```and post the results.
Just rebooted and this is the output of the request:
```

media@mythtv:~$ ps aux|grep backend
mythtv    2179  0.5  1.1 1544996 48176 ?       Sl   15:01   0:00 /usr/bin/mythbackend --syslog local7 --user mythtv
media     2444  0.0  0.0   8112   924 pts/2    S+   15:02   0:00 grep --color=auto backend
media@mythtv:~$ 

```

---

### Post by nickrout on 2012-11-03
> **Morffinator said:**
> Just rebooted and this is the output of the request:
```

media@mythtv:~$ ps aux|grep backend
mythtv    2179  0.5  1.1 1544996 48176 ?       Sl   15:01   0:00 /usr/bin/mythbackend --syslog local7 --user mythtv
media     2444  0.0  0.0   8112   924 pts/2    S+   15:02   0:00 grep --color=auto backend
media@mythtv:~$ 

```OK so mythbackend is running. Now is there still a problem?

---

### Post by Morffinator on 2012-11-03
> **nickrout said:**
> OK so mythbackend is running. Now is there still a problem?

Yep their is still a problem being that the frontend part is still reporting it isn't connected to the backend and that the tuners are still reporting that their issue of not being available.

The tail end of the mythfrontend log gives me:

```


tail /var/log/mythtv/mythfrontend.log
Nov  3 15:23:52 mythtv mythfrontend[2012]: E CoreContext mythcorecontext.cpp:441 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Nov  3 15:23:52 mythtv mythfrontend[2012]: C CoreContext mythmiscutil.cpp:513 (checkTimeZone) Unable to determine master backend time zone settings.  If those settings differ from local settings, some functionality will fail.
Nov  3 15:23:53 mythtv mythfrontend[2012]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on mythtv' type '_mythfrontend._tcp.' domain: 'local.'
Nov  3 15:23:56 mythtv mythfrontend[2012]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Nov  3 15:23:56 mythtv mythfrontend[2012]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on mythtv'
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext mythraopdevice.cpp:82 (Cleanup) RAOP Device: Cleaning up.
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext mythairplayserver.cpp:260 (Cleanup) AirPay: Cleaning up.
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
Nov  3 15:23:58 mythtv mythfrontend[2012]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.

```

The mythtv-setup log gives me:
```


media@mythtv:~$ tail /var/log/mythtv/mythtv-setup.log
Nov  3 14:17:14 mythtv mythtv-setup[5669]: I CoreContext videosource.cpp:573 (Load) XMLTVConfig::Load: Running 'tv_find_grabbers baseline'.
Nov  3 14:17:16 mythtv mythtv-setup[5669]: I CoreContext videosource.cpp:591 (Load) XMLTVConfig::Load: Finished running tv_find_grabbers
Nov  3 14:17:16 mythtv mythtv-setup[5669]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Nov  3 14:17:33 mythtv mythtv-setup[5669]: W CoreContext diseqc.cpp:359 (Load) DiSEqCDevTree: No device tree for cardid 1
Nov  3 14:17:33 mythtv mythtv-setup[5669]: W CoreContext diseqc.cpp:359 (Load) DiSEqCDevTree: No device tree for cardid 3
Nov  3 14:18:30 mythtv mythtv-setup[5669]: I CoreContext mythdbcon.cpp:422 (getStaticCon) New static DB connectionDataDirectCon
Nov  3 14:18:30 mythtv mythtv-setup[5669]: I CoreContext channelscan/channelimporter.cpp:246 (DeleteUnusedTransports) ChanImport: Found 0 unused transports.
Nov  3 14:20:11 mythtv mythtv-setup[5669]: E CoreContext checksetup.cpp:68 (checkStoragePaths) No Storage Group directories are defined.  You must add at least one directory to the Default Storage Group where new recordings will be stored.
Nov  3 14:21:05 mythtv mythtv-setup[5669]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Nov  3 14:21:05 mythtv mythtv-setup[5669]: E CoreContext mythcorecontext.cpp:441 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address

```

From ```
 dmesg
ls -l /dev/dvb
```
I get:
```

[    9.569854] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[    9.782979] DiB0070: successfully identified
[    9.808045] Registered IR keymap rc-dib0700-rc5
[    9.808246] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/rc/rc1/input15
[    9.808526] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/rc/rc1
[    9.808765] dvb-usb: schedule remote query interval to 50 msecs.
[    9.808771] dvb-usb: Sony PlayTV successfully initialized and connected.

```

---

### Post by nickrout on 2012-11-03
> **Morffinator said:**
> Yep their is still a problem being that the frontend part is still reporting it isn't connected to the backend and that the tuners are still reporting that their issue of not being available.

The tail end of the mythfrontend log gives me:

```


tail /var/log/mythtv/mythfrontend.log
Nov  3 15:23:52 mythtv mythfrontend[2012]: E CoreContext mythcorecontext.cpp:441 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Nov  3 15:23:52 mythtv mythfrontend[2012]: C CoreContext mythmiscutil.cpp:513 (checkTimeZone) Unable to determine master backend time zone settings.  If those settings differ from local settings, some functionality will fail.
Nov  3 15:23:53 mythtv mythfrontend[2012]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on mythtv' type '_mythfrontend._tcp.' domain: 'local.'
Nov  3 15:23:56 mythtv mythfrontend[2012]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Nov  3 15:23:56 mythtv mythfrontend[2012]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on mythtv'
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext mythraopdevice.cpp:82 (Cleanup) RAOP Device: Cleaning up.
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext mythairplayserver.cpp:260 (Cleanup) AirPay: Cleaning up.
Nov  3 15:23:57 mythtv mythfrontend[2012]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
Nov  3 15:23:58 mythtv mythfrontend[2012]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.

```

The mythtv-setup log gives me:
```


media@mythtv:~$ tail /var/log/mythtv/mythtv-setup.log
Nov  3 14:17:14 mythtv mythtv-setup[5669]: I CoreContext videosource.cpp:573 (Load) XMLTVConfig::Load: Running 'tv_find_grabbers baseline'.
Nov  3 14:17:16 mythtv mythtv-setup[5669]: I CoreContext videosource.cpp:591 (Load) XMLTVConfig::Load: Finished running tv_find_grabbers
Nov  3 14:17:16 mythtv mythtv-setup[5669]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Nov  3 14:17:33 mythtv mythtv-setup[5669]: W CoreContext diseqc.cpp:359 (Load) DiSEqCDevTree: No device tree for cardid 1
Nov  3 14:17:33 mythtv mythtv-setup[5669]: W CoreContext diseqc.cpp:359 (Load) DiSEqCDevTree: No device tree for cardid 3
Nov  3 14:18:30 mythtv mythtv-setup[5669]: I CoreContext mythdbcon.cpp:422 (getStaticCon) New static DB connectionDataDirectCon
Nov  3 14:18:30 mythtv mythtv-setup[5669]: I CoreContext channelscan/channelimporter.cpp:246 (DeleteUnusedTransports) ChanImport: Found 0 unused transports.
Nov  3 14:20:11 mythtv mythtv-setup[5669]: E CoreContext checksetup.cpp:68 (checkStoragePaths) No Storage Group directories are defined.  You must add at least one directory to the Default Storage Group where new recordings will be stored.
Nov  3 14:21:05 mythtv mythtv-setup[5669]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Nov  3 14:21:05 mythtv mythtv-setup[5669]: E CoreContext mythcorecontext.cpp:441 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address

```

From ```
 dmesg
ls -l /dev/dvb
```
I get:
```

[    9.569854] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[    9.782979] DiB0070: successfully identified
[    9.808045] Registered IR keymap rc-dib0700-rc5
[    9.808246] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/rc/rc1/input15
[    9.808526] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/rc/rc1
[    9.808765] dvb-usb: schedule remote query interval to 50 msecs.
[    9.808771] dvb-usb: Sony PlayTV successfully initialized and connected.

```
Exactly what message are you seeing and where are you seeing it? Tell us what you see from the moment mythfrontend is started.

what is the contents of ~media/.mythtv/mysql.txt (assuming you are using 0.25) or config.xml (if you are using 0.26)

It is OK to start mythfrontend from the commandline for the media user and the entire contents of the output could be useful.

---

### Post by Morffinator on 2012-11-03
> **nickrout said:**
> Exactly what message are you seeing and where are you seeing it? Tell us what you see from the moment mythfrontend is started.
I see it as soon as the machine loads the Frontend interface after a reboot. Perhaps it is loading too soon.

The message is this:
> 
Could not connect to the master backend service. Is it Running? Is the IP address set for it in MythTV-Setup correct?

> 
what is the contents of ~media/.mythtv/mysql.txt (assuming you are using 0.25) or config.xml (if you are using 0.26)

It is OK to start mythfrontend from the commandline for the media user and the entire contents of the output could be useful.
The config.xml is:
```

<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>9dWU7ywA</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>6543</DBPort>
      </DefaultBackend>
    </MythFrontend>
    <UDN>
      <MediaRenderer>{c287f6c6-b6ea-46c8-9646-98ab1314af5</MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>

```

and from starting from the commandline:
```

media@mythtv:~$ mythfrontend
QGtkStyle was unable to detect the current GTK+ theme.
2012-11-03 17:55:00.116619 C  mythfrontend version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org
2012-11-03 17:55:00.116648 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-11-03 17:55:00.116653 N  Enabled verbose msgs:  general
2012-11-03 17:55:00.116680 N  Setting Log Level to LOG_INFO
2012-11-03 17:55:00.116732 I  Added logging to the console
2012-11-03 17:55:00.116759 I  Added syslogging to facility local7
2012-11-03 17:55:00.116766 I  Added database logging to table logging
2012-11-03 17:55:00.116875 N  Setting up SIGHUP handler
2012-11-03 17:55:00.116995 N  Using runtime prefix = /usr
2012-11-03 17:55:00.117010 N  Using configuration directory = /home/media/.mythtv
2012-11-03 17:55:00.117205 I  Assumed character encoding: en_AU.UTF-8
2012-11-03 17:55:00.117745 N  Empty LocalHostName.
2012-11-03 17:55:00.117754 I  Using localhost value of mythtv
2012-11-03 17:55:00.139221 N  Setting QT default locale to EN_US
2012-11-03 17:55:00.139306 I  Current locale EN_US
2012-11-03 17:55:00.139352 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-11-03 17:55:00.146827 I  Starting IO manager (write)
2012-11-03 17:55:00.146935 I  Starting IO manager (read)
2012-11-03 17:55:00.147013 I  Starting process signal handler
2012-11-03 17:55:00.147108 I  Starting process manager
2012-11-03 17:55:00.247396 I  ScreenSaverX11Private: XScreenSaver support enabled
2012-11-03 17:55:00.248407 I  ScreenSaverX11Private: DPMS is disabled.
2012-11-03 17:55:00.256144 N  Desktop video mode: 1920x1080 60.000 Hz
2012-11-03 17:55:00.271852 I  Listening on TCP 127.0.0.1:6547
2012-11-03 17:55:00.271934 I  Listening on TCP [::1]:6547
2012-11-03 17:55:00.272045 I  Listening on TCP [fe80::21d:7dff:fed1:a7a%eth0]:6547
cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory
2012-11-03 17:55:01.241113 E  RAOP Conn: Failed to read key from: /home/media/.mythtv/RAOPKey.rsa
2012-11-03 17:55:01.241136 E  RAOP Device: Aborting startup - no key found.
2012-11-03 17:55:01.244482 I  Loading en_us translation for module mythfrontend
2012-11-03 17:55:01.251966 I  LIRC: Successfully initialized '/dev/lircd' using '/home/media/.mythtv/lircrc' config
2012-11-03 17:55:01.252135 E  JoystickMenuThread: Joystick disabled - Failed to read /home/media/.mythtv/joystickmenurc
2012-11-03 17:55:01.259076 E  CECAdapter: Failed to load libcec.
2012-11-03 17:55:01.260021 I  Binding to UDP 127.0.0.1:6948
2012-11-03 17:55:01.260148 I  Binding to UDP [::1]:6948
2012-11-03 17:55:01.260280 I  Binding to UDP [fe80::21d:7dff:fed1:a7a%eth0]:6948
2012-11-03 17:55:01.296775 I  Using Frameless Window
2012-11-03 17:55:01.296832 I  Using Full Screen Window
2012-11-03 17:55:01.424288 I  Using the Qt painter
2012-11-03 17:55:01.582014 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-11-03 17:55:01.652224 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-11-03 17:55:01.652239 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-11-03 17:55:01.652905 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-11-03 17:55:01.652915 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-11-03 17:55:01.744139 N  Registering Internal as a media playback plugin.
2012-11-03 17:55:01.774901 W  No plugins directory /usr/lib/mythtv/plugins
2012-11-03 17:55:01.811792 N  Found mainmenu.xml for theme 'Mythbuntu'
2012-11-03 17:55:01.921819 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-11-03 17:55:01.922844 I  Using protocol version 72
2012-11-03 17:55:02.180492 I  Bonjour: Service registration complete: name 'Mythfrontend on mythtv' type '_mythfrontend._tcp.' domain: 'local.'
2012-11-03 17:55:10.904204 I  Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on mythtv'
2012-11-03 17:55:10.904501 I  RAOP Device: Cleaning up.
2012-11-03 17:55:10.904524 I  AirPay: Cleaning up.
2012-11-03 17:55:10.904554 I  Deleting UPnP client...
2012-11-03 17:55:12.265565 I  Waiting for threads to exit.

```

---

### Post by nickrout on 2012-11-03
I can't actually see anything that leaps out at me in that log. Does the frontend work at that point?

---

### Post by Morffinator on 2012-11-03
> **nickrout said:**
> I can't actually see anything that leaps out at me in that log. Does the frontend work at that point?

I can get into the frontend but live tv doesn't work. It doesn't complain there are no tuners it just says drops me staight back to the menu.

I can see guide data as well.

I really not sure. Might be time to re-load a different version of Mythbuntu just to check.

---

### Post by nickrout on 2012-11-03
> **Morffinator said:**
> I can get into the frontend but live tv doesn't work. It doesn't complain there are no tuners it just says drops me staight back to the menu.

I can see guide data as well.

I really not sure. Might be time to re-load a different version of Mythbuntu just to check.Can you see recordings? videos? 

If your system is new and hasn't scheduled any recodrings yet, schedule the next thing that is on and see if it records.

---

### Post by Morffinator on 2012-11-03
> **nickrout said:**
> Can you see recordings? videos? 

If your system is new and hasn't scheduled any recodrings yet, schedule the next thing that is on and see if it records.
Yeah it is a new machine. I can schedule but it doesn't record anything.

---

### Post by nickrout on 2012-11-03
> **Morffinator said:**
> Yeah it is a new machine. I can schedule but it doesn't record anything.OK you probably need to gather some backend log data around a point where the recording starts.

---

### Post by Morffinator on 2012-11-06
Sorry about the delay in replying. Have been busy with work but the good news is I have fixed the issues with the tuner and all is working. (well except Samba).

The issue was that I hadn't put the firmware /lib/firmare and the backend and frontend are talking.

Thanks for the assistance.

---

