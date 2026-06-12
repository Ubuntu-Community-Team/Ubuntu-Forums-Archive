---
title: "Timezone and time goes wrong"
date: 2008-10-14
forum: Mythbuntu
---

### Post by JugeHuge on 2008-10-14
i'm having problems with timezone and time. 

i have set correct timezone from date and time settings but when i exit date and time and go back to check if everything is allright. Has been reverted back to earlier setting. It always revert back no matter what. 

Another problem is that time doesn't seems to sync from servers even it set from date and time settings to automatic. Clock gets once in a week to about 15min late and i have to go and manually sync with server.

I have tried to google the matter but haven't found real solution.
I'm using Mythbuntu 8.04.1

---

### Post by klc5555 on 2008-10-14
> **JugeHuge said:**
> i'm having problems with timezone and time. 

i have set correct timezone from date and time settings but when i exit date and time and go back to check if everything is allright. Has been reverted back to earlier setting. It always revert back no matter what. 

Another problem is that time doesn't seems to sync from servers even it set from date and time settings to automatic. Clock gets once in a week to about 15min late and i have to go and manually sync with server.

I have tried to google the matter but haven't found real solution.
I'm using Mythbuntu 8.04.1

On most of my machines I've set up a little netdate script to run daily as a cron job and this seems to do the trick.

For a description on how to do this see [http://www.loblolly.net/~rddecker/helppages/MiniHOWTOS/systemclock/systemclock-twoclocks.htm](http://www.loblolly.net/~rddecker/helppages/MiniHOWTOS/systemclock/systemclock-twoclocks.htm)
in particular section 2.5 and following on netdate, and setting the required permissions.

Good luck! :)

---

### Post by JugeHuge on 2008-10-15
Thanks for the link. Have to try out that if it would solve my problems with time..

---

### Post by JugeHuge on 2008-10-21
Hello i tried out that guide and it was quite useful.
netdate wasn't available so i used ntpdate instead.
I made script so that it will sync clock every hour but now i'm facing another problem. Sometimes time could be late about 3-4min in hour and when i look cron.log. It shows that script is runned hourly and if i run it manually. It will update.. 

So is there somekind of time correction functionality that linux try to adjust time if the clock was late or early?? 

here is example output of the script:
```
The current System date and time is
ti 21.10.2008 21:03:21 +0300
the CMOS/Hardware clock date/time is
ti 21. lokakuuta 2008 21:03:31  -0.027557 seconds
21 Oct 21:03:30 ntpdate[24352]: step time server 192.36.143.150 offset 10.466214 sec
The System and CMOS/Hardware clock date/time will be set to:
ti 21.10.2008 21:03:40 +0300

```

Funny that my script has been runned earlier at Oct 21 20:58:01 juge-desktop /USR/SBIN/CRON[24276]: (root) CMD (/sbin/setdate  > /dev/null)
so in 5min system clock is 19 sec late and HW clock is 9 sec. :confused:

---

### Post by ian dobson on 2008-10-21
Hi,

Why not just use ntpd (the deamon version of ntpdate), it includes an automatic slew correction for the clock after running for a while.

Regards
Ian Dobson

---

### Post by anonymousdog on 2008-10-21
+1
Once you set your time source (e.g., ntp.ubuntu.com, [one of] the ntp server pool[s], or a master time server for your LAN [itself probably synched with an internet source]), you're done...never worry about it or experience time/date drift issues again.

Also, if your DHCP server can do it (e.g., isc-dhcpd or dnsmasq) set the 'option ntp-servers <authoritative local or internet ntp server>;' (or similar).  Your DHCP clients will pick up the time server setting, and you'll never have to configure it anywhere else (for DHCP clients).

---

### Post by JugeHuge on 2008-10-23
> **ian dobson said:**
> Hi,

Why not just use ntpd (the deamon version of ntpdate), it includes an automatic slew correction for the clock after running for a while.

As far as i know mythbuntu uses by default ntpd when you set from date and time settings configuration to keep synchronized with internet servers.

For some reason this won't work as i described my problem in first post..

---

### Post by anonymousdog on 2008-10-23
Is the ntp service enabled on that machine.  This always "just works" (TM) for me.

---

### Post by newlinux on 2008-10-23
```
sudo /etc/init.d/ntp status
```

I had an  install that for some reason didn't run it or start it, I don't remember which... but installing it has always worked for me too...

---

### Post by anonymousdog on 2008-10-23
Which always makes me beg the question (and invite flames), "Why doesn't Ubuntu have a 'service' command (probably just an alias) like Red Hat distros?"...saves a lot of typing.  In Red Hat (ES, Fedora Core, CentOS, etc.) that's just 'sudo service ntp status'.

---

### Post by newlinux on 2008-10-23
> **anonymousdog said:**
> Which always makes me beg the question (and invite flames), "Why doesn't Ubuntu have a 'service' command (probably just an alias) like Red Hat distros?"...saves a lot of typing.  In Red Hat (ES, Fedora Core, CentOS, etc.) that's just 'sudo service ntp status'.

install sysvconfig and you can have your service command back :)

---

### Post by JugeHuge on 2008-10-24
> **anonymousdog said:**
> Is the ntp service enabled on that machine.  This always "just works" (TM) for me.

Yes it is.. This leads to question that there might have been situation when ntp service was stopped for some reason..

I reverted back to use Time and Date settings configuration on sync on internet servers. I also enabled logging /etc/ntp.conf so when time goes out of sync i'm hoping that ntp.log might reveal something.

---

### Post by anonymousdog on 2008-10-24
> **newlinux said:**
> install sysvconfig and you can have your service command back :)
Very cool!  I did not know that.

---

### Post by newlinux on 2008-10-24
> **anonymousdog said:**
> Very cool!  I did not know that.

I don't think all the "service" flags work in debian based distros, but the basic ones do.

---

### Post by anonymousdog on 2008-10-24
It all depends on what flags the init script will take.  I've noticed that many lack "restart", "condrestart", and "status" in Mythbuntu.  Those are pretty much standard (along with "start" and "stop") in Red Hat rpms.

Does sysvconfig actually change the way Ubuntu handles startup or just add some SysV-style tools?

---

### Post by newlinux on 2008-10-24
Yeah, I know that is true with service specific calls with service, but I also know some non service specific flags don't work though. When I had it installed before I couldn't do:

```

sudo service --status-all

```

Maybe that was because some init scripts don't have a status option...
I'm pretty sure it just adds some SysV style tools, but I don't know for sure.

---

