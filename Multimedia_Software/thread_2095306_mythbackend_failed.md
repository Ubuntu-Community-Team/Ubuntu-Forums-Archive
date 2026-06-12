---
title: "mythbackend failed"
date: 2012-12-16
forum: Multimedia Software
---

### Post by kr651129 on 2012-12-16
I'm trying to get mythbackend working for xbmc and it keeps failing.  MeTV works fine but for whatever reason I'm getting the following

```

2012-12-16 13:27:14.515693 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2012-12-16 13:27:14.663364 E  InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2012-12-16 13:27:14.663381 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-12-16 13:27:14.663409 E  Problem with capture cardsCard 1failed init
2012-12-16 13:27:14.664559 E  TVRec(2): Problem finding starting channel, setting to default of '3'.
2012-12-16 13:27:14.664715 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:14.714932 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:14.765076 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:14.815217 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:14.865366 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:14.915497 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:14.965706 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.015924 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.066127 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.116340 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.166541 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.216679 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.266911 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.317048 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.367253 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.417389 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.467593 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.517743 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.567955 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.618159 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
                        eno: Device or resource busy (16)
2012-12-16 13:27:15.618177 E  DVBChan(2:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-12-16 13:27:15.618190 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-12-16 13:27:15.618224 E  Problem with capture cardsCard 2failed init
2012-12-16 13:27:15.618244 W  MythBackend: No valid capture cards are defined in the database.
2012-12-16 13:27:15.619631 E  Scheduler: No channel sources defined in the database

```

I've checked the permissions and I've added myself to the mythtv group.  Anyone know anything that I might be missing?

---

### Post by BicyclerBoy on 2012-12-16
Did this BE ever work ? i.e. did you use/try mythfrontend ?

Have you run mythtv-setup ?
The error suggests you did not connect the video source to the actual tuners..

Note it can be cleaner to stop mythbackend before running mythtv-setup.
With the more recent upstart job: 
sudo service mythtv-backend stop

Restart after using mythtv-setup

---

### Post by kr651129 on 2012-12-16
I've tried the frontend and it complains that there are no tuners.  I've tried the mythtv-setup but I get what looks to be a terminal and it just hangs.  When I exit it ask's me if I want to start the backend and if I want to fill the DB which makes no sense to me since the setup just hangs.

---

### Post by BicyclerBoy on 2012-12-16
Maybe the theme  or GUI size is messed up

mythtv-setup -O ThemePainter=opengl -v all
mythtv-setup --geometry 1440x900 -O Theme=terra -v all

Try all the cmd option together.

I repeat..
Did the BE ever work?
Have you ever run mythtv-setup (successfully) ?

The very recent XBMC has cmyth plugin, are you trying to use that **exact** plugin ?

---

### Post by kr651129 on 2012-12-18
I started over on a fresh install of Ubuntu 12.10 x64 and it's doing the same thing.  I'm not sure I would call running the setup successful.  I did make a little more progress, on the setup this time around I was able to see the card in the GUI with no errors.  But I'm still getting the same errors as listed in the first post when trying to start the BE.  It seems that the setup will only work for each user once before defaulting to the terminal where it hangs.  I did try the other themes as suggested and neither worked.  I'm about ready to give up on this project :/

---

### Post by BicyclerBoy on 2012-12-18
My guess is that mythtv-setup has not locked up but it is not able to make the GUI visible or it can not stop mythbackend service..

Did you try in terminal ?:
$ sudo service mythtv-backend stop
before launching
$ mythtv-setup -v all

(need to run "sudo service mythtv-backend start" to continue to use mythtv)

(your backend service might have diff name mythbackend)

---

### Post by kr651129 on 2012-12-19
Thanks, still not working though.  When I do a pgrep for myth I get a process ID even after running sudo service mythtv-backend stop so I tried to kill the PID.  Even when I do that myth still creates a new process.  I finally got back into the setup by letting it kill the backend via the prompt.  Now when I go to add my card I'm getting the following

```
DVB DTV vapture card (v3.x)
DVB Device: /dev/dbn/adapter0/frontend0
Frontend ID: Could not get card info for card /dev/dvb/adapter0/frontSubtype: Unknown error
....
```

In the xterm that mythtv-setup opens I'm getting

```

E FE_GET_INFO ioctl failed (/dev/dvb/adapter0/frontend0)

```

Here's that directory

```

 ls /dev/dvb/adapter0 -al
total 0
drwxr-xr-x  2 root root     120 Dec 18 23:14 .
drwxr-xr-x  3 root root      60 Dec 18 23:14 ..
crwxrwxrwx+ 1 root video 212, 1 Dec 18 23:14 demux0
crwxrwxrwx+ 1 root video 212, 2 Dec 18 23:14 dvr0
crwxrwxrwx+ 1 root video 212, 0 Dec 18 23:14 frontend0
crwxrwxrwx+ 1 root video 212, 3 Dec 18 23:14 net0

```

I chmoded them all to 777 just for now to make sure it wasn't a permissions issue.

---

### Post by BicyclerBoy on 2012-12-20
The original problem could be:
- other process hogging the tuner h/w. (MeTV ?)
- multiple backend processes (tuners are opened for exclusive access)
- no video sources defined
- video source not connected to any tuners
- tuners detected as wrong type..

I would try to determine how mythbackend is launched (in your install).

Changed my mythtv installs to use up-start jobs long ago..& the service stop command posted previous could be of no use.

---

### Post by kr651129 on 2012-12-20
Thanks I'll take a look into all that when I get home.  I did try to install Mythbuntu 12.04 x64 last night with no success.  I'm running into the same type of errors.  It looked like mythbackend isn't starting at boot.  I exited the FE and ran myth-setup, it saw the card, I added it, on exit it asked if I wanted to start the BE I said yes, it gave out a PID.  pgrep showed nothing and I though I'd try and run the FE incase the BE process name was somthing odd, it said could not connect to the backend and that the device (tv card) was busy.  Here's my thought process and maybe you can tell me where I might be going wrong.

-BE won't start at boot
-FE says device is busy only after a myth-setup, will not do this on a cold boot
-BE see's the card but isn't running

With all that said I think it's gotta be a error with the backed startup but I can't find a core dump but I've pretty much narrowed it down to the backend crashing somehow..I just can't figure out where or why.  Are there any other backends you would suggest?

---

### Post by BicyclerBoy on 2012-12-20
Confirm with ps -ax or gnome-system-monitor that backend is not running..

Open 2 terminals:
In one terminal:
mythbackend -v all

In other terminal:
mythfrontend -v all

It is likely *buntu is using old /etc/init.d/ scripts to start BE.
It should still work.
The log files are likely in /var/log/mythtv/*

Make sure your user is a member of "mythtv" group.

FYI:
I use upstart-job & syslogging on 10.04 & 12.04.
There are good examples on mythtv.org wiki
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
(note you have to decide between logpath/file or syslogging.)

[http://www.mythtv.org/wiki/Simple_rsyslog_Configuration](http://www.mythtv.org/wiki/Simple_rsyslog_Configuration)
note you can use rsyslog or syslog-ng etc.

Logpath/file logging of 0.25 FE did not work properly for user /= "mythtv".

---

### Post by kr651129 on 2012-12-21
Thanks for all the help, still isn't working.  I reinstalled Ubuntu 12.04 x64 and went with tvheadend + xbmc, it took about 15 minutes and everything is working now.

---

