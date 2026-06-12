---
title: "myth box all of a suden freezing up, no logs"
date: 2008-12-17
forum: Mythbuntu
---

### Post by netslacker on 2008-12-17
So my main myth recording box is all of a sudden freezing up once a day for no reason at all.  I've searched log files and can't seem to find any errors anywhere.  It will freeze up now almost daily and when it does, I have to hard reset the box to get it back up.

Anyone have any ideas where to even start looking?  I would say that this is a heat related issue but fans seems to be fine and the box has run for months w/o problem until this past week.

Any suggestions are appreciated...

AMD 5000+
Kingston 2GB ram
Silverstone LC20M
Seagate 750GB
GIGABYTE GA-MA78G-DS3H
BIOSTAR VP7202GL26 GeForce 7200GS

---

### Post by uMuppet on 2008-12-17
What state is it in when it locks up?  Is it recording?
Do you have any cron jobs running?  Anything in /etc/cron.daily that might not be working.  
Is Mythfilldatabase set to run daily?  Could it be a problem.

---

### Post by netslacker on 2008-12-17
it is idle when it dies.  Usually in the afternoon.

mythfilldatabase occasionally runs w/ a segfault but it is at 1am.

I turned off mythcommflag to see if that was a problem since I had it setup to run during this time but there is no difference in the freezes if it runs or not.

My only daily cron job that I setup is a restart to see if a daily restart of the box would help it, but it doesn't.

---

### Post by netslacker on 2008-12-17
I see this message around 8am on every day (syslog):

```
Dec 15 08:03:10 mythtv syslogd 1.5.0#1ubuntu1: restart.
```

but it is usually preceded and trails by a number of these:
```
Dec 15 08:21:11 mythtv -- MARK --
```

While that shows up in the morning, the system does not actually restart, it just ends up frozen some time later.  Not sure what is producing this message.

---

### Post by klc5555 on 2008-12-18
> **netslacker said:**
> I see this message around 8am on every day (syslog):

```
Dec 15 08:03:10 mythtv syslogd 1.5.0#1ubuntu1: restart.
```

but it is usually preceded and trails by a number of these:
```
Dec 15 08:21:11 mythtv -- MARK --
```

While that shows up in the morning, the system does not actually restart, it just ends up frozen some time later.  Not sure what is producing this message.

Is the AMD CPU running hot? Is its cooler working? Is the fan on the Nvidia still running? (Or worse, is it one of those bleeping fanless heatsink jobs?) The case fans all working? Most of the time when I've had a previously stable box start to lock up frequently for no discernable reason, something has gone wrong on the thermal front.

The second thing which has tended to go wrong, from the hardware perspective, is the power supply. Particularly if the power supply was on the smallish side to begin with for the load being put on it, it doesn't take much for the power it's supplying to your system to go out of spec. Could cause lockups, spontaneous reboots, and a variety of other errors that tend to resemble failing RAM errors. 

Thirdly, good RAM does occasionally go bad, but not often. Your troubleshooting should first rule out everything that makes heat and everything that has moving parts. 

Anyway, that's where I'd start looking.

Good luck!

---

