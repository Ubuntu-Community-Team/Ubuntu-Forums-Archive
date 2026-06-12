---
title: "MythFrontend can't connect to MythBuntu Backend"
date: 2008-08-23
forum: Mythbuntu
---

### Post by dvanbrunt on 2008-08-23
There are already threads on this, so I had my hopes up that I'd find a solution. Sadly, after doing all the things posted on the other forums, I still have a problem:

Combined MythBuntu backend/frontend (BE/FE) runs fine.
Myth Control Center (MCC) Shows that all servcies, including MySQL service are enabled.

[LIST]
[*]Local Backend IP address set to 192.168.2.55 in MythTV Backend Setup
[*]Master Backend IP address changed to 192.168.2.55 in MythTV Backend Setup
[*]Commented out the "bind-address" line in /etc/mysql/conf.d/mythtv.cnf
[*]Commented out the "bind-address" line in /etc/mysql/my.cnf
[/LIST]

On the Frontend (a different machine) I can ping 192.168.2.55 no problem. I can also have a remote MySQL session using the MythTV user login and password, no problem. The Frontend prefs are looking to IP 192.168.2.55, same as the BE, and the same user (mythtv) and password that work in terminal for a remote MySQL session. (that's the part that's different than prior posts-- I do know that the SQL database is open to other machines).

So the oddness is that when I try to run MythFrontend on the other machine, I get the error saying that it can't connect to the BE, and am I sure the IP is correct? 

Every mention of the IP, in the BE and the FE, matches that of the results of ifconfig and what I manually set that machine's IP to be. I can connect by telnet, VNC, and even remote SQL, so I know that IP is right.

Other odd behavior or circumance that may or may not be related. I had a failed attempt to get a MediaMVP running per instructions [here]("https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend"), (the problem was that the mediaMVP had to go through a switch, so couldn't get an IP for some reason, even tho the connection was good).  So that happened. When I tried to "turn off" the MySQL service using the MCC, MySQL was disabled entirely, even on the local BE/FE box. I had to re-enable the "service" to get a functioning BE at all... and doing that, for some reason reset the password for the mythtv user so I had to fix that whole mess too. Limitations of scripts, I suppose.

But anyhoo... now the BE/FE is working, all services are up and seem to be working OK by terminal, but the FE can't  connect.

Can anyone suggest anything else I might try?

PS: I'm a recent convert from KnoppMyth... and I like mythbuntu much better overall. Nice work, everyone.

---

### Post by stevanbt on 2008-08-27
Hi,
Have you copied the MySQL password from your BE/FE machine to your FE machine (in mythtv-setup)?

Thanks, Steve.

---

### Post by nwillis on 2008-08-27
Hi.  Just worked through a similar problem; have a couple of possible questions that _might_ help you. Have you set a PIN on the backend? Have you checked every instance of mysql.txt (the one in /etc/mythtv/, the one in your ~/.mythtv directory, the one in /home/mythtv/.mythtv, and so on), and ensured that they are all identical in terms of IP and password?

If you can connect with command line mysql, then it sounds like you don't have the exact same problem that I did, but those are potential hangups as well.  On the PIN for example, if you want to disable the usage of the PIN, it must be set to 0000 -- in my case, it was set to default 0, which is not the same thing.  Sure, using a simple "_ Enable PIN" checkbox in the MythBackend Setup UI instead would be 1,000,000% clearer, of course, but that's MythTV for you.

As for the multiple mysql.txts, even after plowing through the docs it's not easy to say which takes precedence over which in which circumstances, so they do all need to be the same. One might get read in (and work) when you launch Myth from your own user session, but another when Myth is launched automatically.  If you disabled and reenabled MySQL in MCC, there's a chance it rewrote the one in /etc/mythtv/.

Good luck!

---

### Post by volkswagner on 2008-08-27
To clarify the "Frontend" machine, in MCC what profile is selected?  Is it Frontend only (no backend)?

---

### Post by dvanbrunt on 2008-08-27
> **volkswagner said:**
> To clarify the "Frontend" machine, in MCC what profile is selected?  Is it Frontend only (no backend)?

Check. The Frontend does have the right password in the "setup" area. The Frontend is not mythbuntu, so there's not a "control center", but it's the same standalone, Mac oS X frontend that worked just fine when connecting to my backend when it was running KnoppMyth (I recently reformatted and installed MythBuntu, just for kicks). 

Since the migration, only MythWeb and serving remote frontends have not worked, as they had on KnoppMyth. Otherwise, I like it better. Sure would like to get this figured out, though!

---

### Post by DemonBob on 2008-08-27
Question, what is the version on the front end in question? 

Also what is the version of the mythtv backend, i believe in Mythbuntu 8.04 its suppose to be .21 

If the frontend is a lower version it will not work, due to protcol changes with communication. I would update the frontend to match the back end of mythtv

---

### Post by dvanbrunt on 2008-08-27
> **DemonBob said:**
> Question, what is the version on the front end in question? 

Also what is the version of the mythtv backend, i believe in Mythbuntu 8.04 its suppose to be .21 

If the frontend is a lower version it will not work, due to protcol changes with communication. I would update the frontend to match the back end of mythtv

I have tried both the .21 and the .21-fixes versions of the OS X client. Both fail with the same result. Thanks for the suggestion, though...

---

### Post by volkswagner on 2008-08-30
Are there any log entries.  On the backend check /var/log/mythtv/mythbackend.log, and on the frontend (assuming same folder location) mythfrontend.log?

Can you access the backend running the 8.04 live CD on a remote machine?

---

### Post by dvanbrunt on 2008-08-30
> **volkswagner said:**
> Are there any log entries.  On the backend check /var/log/mythtv/mythbackend.log, and on the frontend (assuming same folder location) mythfrontend.log?


I put "tail -n50 /var/log/mythtv/mythbackend.log" both before and after a connection attempt, and the log seems to just be an unending sea of the following:


> 2008-08-30 08:00:02.785 adding: MythBox as a client (events: 0)
2008-08-30 08:01:15.868 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 08:10:02.630 MainServer::HandleAnnounce Monitor
2008-08-30 08:10:02.634 adding: MythBox as a client (events: 0)
2008-08-30 08:16:15.947 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-30 08:20:02.442 MainServer::HandleAnnounce Monitor
2008-08-30 08:20:02.446 adding: MythBox as a client (events: 0)
2008-08-30 08:30:02.228 MainServer::HandleAnnounce Monitor
2008-08-30 08:30:02.230 adding: MythBox as a client (events: 0)
2008-08-30 08:31:16.028 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

Not sure if that's bad or good, but doesn't look related for all I know.

Could not find a frontend log on the Mac OS X version, and I don't have another machine to try the live frontend on. I may try installing BootCamp to see if I can boot the MacBook (it's a Core Duo) using the Live Frontend DVD. 

The only other thing I noticed is the config.xm. says "DBPort = 0" instead of the usual 3306... but changing this value in the setup screens didn't matter.

---

### Post by volkswagner on 2008-08-30
I assume Mythbox is the name of the mac frontend.  

For giggles try in backend setup, change mysql location to the loopback address or localhost.

My backend settings:

Mythtv Database = mythconverg
Mysql server = localhost

I have had trouble in the past using the actual ip address.

EDIT:  I think you really need to find the frontend logs.  You may have results running frontend from terminal with verbose on to see results/errors.

---

### Post by bmwman on 2008-08-30
In the backend setup right below where you specify the IP adress you need to specify PIN. Put 0000 for it and that shoul alloa any frontend to connect. Leave the real IP alone, don't use localhost. 

That's what solved my problem.

---

### Post by dvanbrunt on 2008-08-30
> **volkswagner said:**
> I assume Mythbox is the name of the mac frontend.  

For giggles try in backend setup, change mysql location to the loopback address or localhost.

My backend settings:

Mythtv Database = mythconverg
Mysql server = localhost

I have had trouble in the past using the actual ip address.

EDIT:  I think you really need to find the frontend logs.  You may have results running frontend from terminal with verbose on to see results/errors.

OMG... I made screenshots of every step of set up, so i KNOW this was right... In MCC, clicked on the "Launch MythTV Setup" and Lo and Behold, the IPs there had reverted back to 127.0.0.1... I checked my shots... yep, I had SET them, and SAVED them as the static IP on my system...

Changed them back, and the frontend connects and shows the library. Yay! 

HOWEVER, I only get audio, and a black screen.

Errr. Probably that's another thread.

No idea why that setting reverted. Perhaps after enabling and disabling a few features, like the "Diskless Frontend"...?? 

I don't know how to launch the OS X frontend "verbose" as you suggest. Will have to do some digging on that that one.

---

### Post by kwilliam on 2008-09-16
> **dvanbrunt said:**
> OMG... I made screenshots of every step of set up, so i KNOW this was right... In MCC, clicked on the "Launch MythTV Setup" and Lo and Behold, the IPs there had reverted back to 127.0.0.1... I checked my shots... yep, I had SET them, and SAVED them as the static IP on my system...

Changed them back, and the frontend connects and shows the library. Yay! 

HOWEVER, I only get audio, and a black screen.

Errr. Probably that's another thread.

No idea why that setting reverted. Perhaps after enabling and disabling a few features, like the "Diskless Frontend"...?? 

I don't know how to launch the OS X frontend "verbose" as you suggest. Will have to do some digging on that that one.

dvanbrunt, did you ever solve the black screen problem? I'm having a very similar problem, and managed to get to a sound-but-no-video stage after changing the IP addresses in the backend setup from 127.0.0.1 to the static network IP. I'm trying to use a frontend on a linux laptop, and it works if I log into the MythTV environment from log in, but if I run mythfrontend from KDE4 I get a black screen with sound for live TV or recordings. Also, I'm getting the error "X Error: BadAlloc (insufficient resources for operation) 11". Has the blank video problem got something to do with xorg.conf?

---

### Post by dvanbrunt on 2008-10-02
> **kwilliam said:**
> dvanbrunt, did you ever solve the black screen problem? I'm having a very similar problem, and managed to get to a sound-but-no-video stage after changing the IP addresses in the backend setup from 127.0.0.1 to the static network IP. I'm trying to use a frontend on a linux laptop, and it works if I log into the MythTV environment from log in, but if I run mythfrontend from KDE4 I get a black screen with sound for live TV or recordings. Also, I'm getting the error "X Error: BadAlloc (insufficient resources for operation) 11". Has the blank video problem got something to do with xorg.conf?

Sorry it took me so long to reply. Got lost in the "InBox"!

Yes, I solved the black screen problem by changing the "Playback" settings... it had been "CPU++" and I dropped it back to "CPU" and it worked fine from then on.

---

### Post by kwilliam on 2008-10-11
Oh hey! That worked for me too! (Actually I think it was on "High" and I changed it to Normal, but same concept.) It works with all the realtime KDE4 effects too.

---

