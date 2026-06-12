---
title: "Mythfilldatabase Not Working after 0.25 to 0.27 Upgrade"
date: 2014-03-01
forum: Mythbuntu
---

### Post by martin41 on 2014-03-01
I have been running Mythbuntu since August without any issues.  I just recently in the last month upgraded from MythTV 0.25 to 0.27 and it appears my mythfilldatabase has stopped populating automatically through MythTV.  I can run it manually and when I do it gives me 16 days worth of guide material which is weird because when it was working automatically it was always 14 days.  Also as you can see below from MythWeb when I look at the Backend Status it says it ran on the 28th successfully and ended on the 27th.  Now the only reason it says 14 days is that it has been 2 days since I ran it manually.  I noticed that the mythfilldatabase.log has no entries since Jan 30 so I went into myth-setup and put the command --logpath /var/log/mythtv after my --dd-grad-all so the whole thing reads --dd-grad-all --logpath /var/log/mythtv and still no entry after it ran last.  I've looked around at other suggestions about deleting the tmp file after a manual run which I did and about setting it up as a cronjob.  I would really like to get it working through MythTV like it did before, can anyone help?  Thanks. 

Last mythfilldatabase run started on Fri Feb 28, 9:00 PM and ended on Thu Feb 27, 7:01 AM. Successful.
    There's guide data until 2014-03-15 02:00:00 (14 days).

---

### Post by martin41 on 2014-03-02
Okay a little more information I was able to dig up which may or may not be the problem if someone could help that would be great.  There are 3 config.xml files that I know about ~/.mythtv/config.xml, etc/mythtv/config.xml, and usr/share/mythtv/config.xml and they all to be a little different.  I thought I had symlinked all of these to the ~/.mythtv one back on January 22 but this doesn't appear to be holding up.  Does anyone think this is the problem?  Which config.xml is the correct one and could there be others I am missing?  Do I have to worry about the mysql.txt as well?  What would be the proper way to symlink these?  Any insight would be greatly appreciated, thanks.


**~/.mythtv/config.xml**

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>c582e4ab-473d-4092-a5f3-1202de33a035</MediaRenderer>
    </UDN>
  </UPnP>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>localhost</Host>
    <UserName>mythtv</UserName>
    <Password>KxQ7Q8Xn</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>

**etc/mythtv/config.xml**

<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>KxQ7Q8Xn</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>
      </DefaultBackend>
    </MythFrontend>
    <UDN>
      <MediaRenderer>{5c528c4c-2108-44fd-a6b1-c625dfa57dd</MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>

[B]
usr/share/mythtv/config.xml
[/B]
<Configuration>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>127.0.0.1</Host>
    <UserName>mythtv</UserName>
    <Password>mythtv</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>

---

### Post by Dave_Alverson on 2014-03-03
I don't think the config.xml would cause a problem.  If you look in your backend log, you should see something like this:
```
Using configuration directory = /home/mythtv/.mythtv
```
which will tell you where the backend is getting its config.xml from (or at least looking first).

When I first upgraded to 0.27, mythfilldb wasn't running for me -- I think there was a problem with the use grabber suggested time option. (I am using Schedules Direct.)  I turned off that option and made sure my min hour and max hour were reasonable.

---

### Post by aelfric55 on 2014-03-06
There seems to have been a number of mythfilldatabase-not-automatically-downloading-schedules-direct problems lately, and as often as not they appear to have been occurring with longer established systems rather than simply with mythtv upgrades or new installs. I've been experiencing it myself over the last month on a long-stable mythtv 0.25.3 system that began being unable to automatically retrieve schedules direct data.

I suspect if you enable mythfilldatabase logging by adding and specifying the  "--logpath" option, you'll discover that you have errors in the data grabbing and data downloading lines of the log whatever time of day or night mythfilldatabase automatically attempts to run. Manually running mythfilldatabase from a terminal, on the other hand, will work without errors any time of the day or night.

There has been a bit of traffic about mythfilldatabase on the gossamer threads mail list and on the schedules direct forums in recent weeks, but without any resolution or even solid agreement that there's an issue, let alone whose issue it is. The schedules direct folks seem to believe that if there is an issue, it must likely be peak-hours network congestion or network issues at the user's end. The mythtv devs seem to believe that there may be the use of obsolete/incorrect mythfilldatabase options (i.e. anything other than --dd-grab-all), mal-formed schedules direct account names (the use of email addresses with "@" as the username) --similar to the bug of a couple of years ago that happened when QT 4.7.1 started to be used-- ...or permissions problems with files in the /tmp directory, or, again, peak hours congestion or user networking issues.

So for the time being I recommend just getting in the habit of running mythfilldatabase manually every few days. At least until whatever problem there may be upstream, if there even is such a problem, begins to get itself sorted out. My personal belief means nothing here, but I suspect something has been changed a bit on the schedules direct end, just because older mythtv installations seem to be having the same mythfilldatabase difficulties as new installations.

---

### Post by itlarson2 on 2014-03-07
I'm using cron myself.  

I've had a lot of weirdness since I switched to .27 myself.  My system is a new install with a restored database from my previous install which ran .25.  Here's just a few issues I've had:
 -Programs that show up in the schedule with only "DTV program" for the title.
 -Programs that have descriptions that clearly are from other shows.
 -After every update I have to log into mysql and reset the mythtv database password before the front-end can connect to the back-end.
 -The dialog box that keeps telling me "Ubuntu has experienced an error" that never goes away.
 -And most recently, programing conflicts where none should exist. 

In short, if you are thinking of upgrading to .27, don't.

---

### Post by martin41 on 2014-03-10
Sorry for my late reply as I was in China all last week on business.  I am going to implement some of the suggestions listed below and see how it goes over the next few days.

-I will use the time start and end option instead of Data Direct suggested time to run mythfilldatabase

-I've also implemented this the new 40-mythtv.conf file which seems to have changed with .26 and above ([http://www.mythtv.org/wiki/Simple_rsyslog_Configuration](http://www.mythtv.org/wiki/Simple_rsyslog_Configuration)) to see if it fixes my logging issue.

---

### Post by martin41 on 2014-03-16
I think this is mostly solved and I will document what I've done and then end it with one final question that I hope someone can answer.

-I set mythbackend to update with specified time instead of the Schedules Direct suggested time.

-My command options are as followed to allow for logging (--dd-grab-all --syslog local7) per [[COLOR=#dd4814]http://www.mythtv.org/wiki/Simple_rsyslog_Configuration[/COLOR]]("http://www.mythtv.org/wiki/Simple_rsyslog_Configuration") for MythTV 0.26 and above.  Now I am running this from a script because I wanted an easy way to modify the command line and using a script allowed me to do so through SSH.  I believe it should work by entering the command options into the backend directly.

The one odd thing I have not been able to figure out is why when I look at the MythWeb Backend Status it will say something like "There's guide data until 2014-04-01 02:00:00 (16 days)."  But when I look at the System Status in the frontend it will say there is data until "2014-03-31 10:00PM" so the two are always four hours apart but the frontend one is the one that is always correct, I never have data until 2:00AM.  Is this just a bug or is there a way to fix it so both reflect the correct guide data amount?

---

### Post by HughR on 2014-03-23
> **martin41 said:**
> 
The one odd thing I have not been able to figure out is why when I look at the MythWeb Backend Status it will say something like "There's guide data until 2014-04-01 02:00:00 (16 days)."  But when I look at the System Status in the frontend it will say there is data until "2014-03-31 10:00PM" so the two are always four hours apart but the frontend one is the one that is always correct, I never have data until 2:00AM.  Is this just a bug or is there a way to fix it so both reflect the correct guide data amount?

What timezone are you in?  Could this be the difference between your timezone and UTC (formerly Greenwich Mean Time)?

(I have to say that this thread makes me wish to stay with .25.)

---

### Post by martin41 on 2014-03-26
I think you may have hit the nail on the head since I am in the eastern time zone and it is showing 4 hours ahead. I have no idea how to fix this though.

---

