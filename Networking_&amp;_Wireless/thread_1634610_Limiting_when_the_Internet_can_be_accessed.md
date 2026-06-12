---
title: "Limiting when the Internet can be accessed"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by MysteryPig on 2010-11-30
I have a teenage daughter that understands Ubuntu, but not so much the terminal, and she does not know the superuser password. Unfortunately, she regularly goes on the Internet during the nighttime and in the early morning. What I am attempting to do is prevent anyone from going onto the Internet during the night (11 PM - 5:30 AM) unless they know the superuser password or a fair bit about the terminal.

I have already tried some commands, however all of them can be bypassed by restarting the computer. ex. sudo ifconfig eth0 down

Any ideas would be greatly appreciated.




For additional information on my Internet:

My Internet connection is relatively slow, so I would prefer if the solution does not hinder it any further. It is slow because there is no high-speed in my area, and I am forced to use Xplorenet -> "Fixed Wireless". I do not have a router.

---

### Post by uncaspi on 2010-11-30
You could set up a cron job to issue a firewall command to close port 80 (your internet port). The roule for cron must be set in /etc/cron.daily and the crontab file. Seach google or see man cron. The same for the firewall roule. man iptables

---

### Post by cybergnome on 2010-11-30
Many routers have this capability within their settings, and of course, that makes sure that no other machines use your connection to defeat a setting on a specific machine.  Kids are great at getting others to help them out. :-(

---

### Post by SeijiSensei on 2010-11-30
> **uncaspi said:**
> You could set up a cron job to issue a firewall command to close port 80 (your internet port). The roule for cron must be set in /etc/cron.daily and the crontab file. Seach google or see man cron. The same for the firewall roule. man iptables

I thought of that, too, though I'd have cron bring eth0 up or down on schedule, but that's not impervious to reboots.  You could set up a cron job to run every minute though, so even if you reboot, the interface would be brought up or down within a minute of rebooting.

---

### Post by uncaspi on 2010-11-30
I agree. It's not cron.daily the best to use, but cron.hourly and per minute.

---

### Post by MysteryPig on 2010-12-01
Thanks for replying. Can you help me out with the command(s) I will need to make this possible?

---

### Post by uncaspi on 2010-12-01
It's 10 years since I used a cron job so I can't remember the syntax. For firewall you should use ufw instead of iptables due to it's easier to start and stop the firewall. iptables requires reboot every time you make a change to the rules. Google ufw +ubuntu and crontab

---

### Post by SeijiSensei on 2010-12-01
> **SeijiSensei said:**
> I thought of that, too, though I'd have cron bring eth0 up or down on schedule, but that's not impervious to reboots.  You could set up a cron job to run every minute though, so even if you reboot, the interface would be brought up or down within a minute of rebooting.

OK, here's an overview, but I'm going to leave some details to you.

As root using sudo, create and edit the file /usr/local/sbin/monitor_time.  This will be a script to manage bringing the network up or down.  You'll need to read up on how to set up a static IP configuration in Ubuntu by editng /etc/network/interfaces.  Once it's configured, the up/down script might look something like this:

```

#!/bin/bash
# script to control access to network by time-of-day

# enter parameters here
START='0700'  # start permitting access in 24-hour clock time
STOP='2130'
INT='eth0'    # interface name; usually eth0 for wired, wlan0 for wireless

####  nothing else to configure ####

# check if network up
NET_CHECK=$(/sbin/ifconfig $INT | grep 'inet addr')

TODAY=$(date +%D)
TSTART="$START $TODAY"
TEND="$STOP $TODAY"

STIME=$(date +%s --date=$TSTART)
ETIME=$(date +%s --date=$TEND)
NOW=$(date +%s)

# check to see if networking is permitted
if [ $NOW -ge $STIME -a $NOW -le $ETIME ]
then
    # permissible time; check if already up; if not, restart
    if [ "$NET_CHECK" = "" ]
    then
        /etc/init.d/networking start
    fi

else
     # not allowed now; disconnect if needed
     if [ "$NET_CHECK" != "" ]
     then
         /etc/init.d/networking stop
     fi

fi

exit 0

```

Save this file, then use "sudo chmod u+x /usr/local/sbin/monitor_time" to mark it executable by the root user.

This is just off the top of my head; it may need some additional futzing.  The "date +%s" commands transform the date strings into time in the "Unix epoch" which is measured in seconds since midnight 1/1/1970.  Expressing dates this way makes it easy to compare them numerically.

Then it's not much more than seeing whether we're in the allowed period or not.  If we are, and the network is down, we bring it up.  If networking is not allowed, and the network is up, we bring it down.  Otherwise the script does nothing.

Now, edit /etc/crontab and add the line

```

* * * * * root /usr/local/sbin/monitor_time

```

This will run the script once each minute.  Most of the time it does nothing so it won't really add any noticeable overhead.  If you want to reduce the frequency of checking, replace the initial star in the crontab rule with "*/5" to check every five minutes, "*/10" for every ten, etc.

---

### Post by MysteryPig on 2010-12-01
Thank you very much for all the help.

Ok, so I found this pretty complicated, but I did manage to create the new file using gksudo nautilus named "monitor_time" in /usr/local/sbin, and I copied and pasted what you wrote into it, and adjusted the START to 0430 and STOP to 2100. Also, I followed the instructions for editing crontab, and now /etc/crontab looks like (not sure if this is right):

> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
*/5 * * * * root /usr/local/sbin/monitor_time
#


The only other thing I was uncertain about was  how to "set up a static IP configuration in Ubuntu", and why I would need to do that.


*I have a dynamic IP btw

---

### Post by grahammechanical on 2010-12-01
Why not set her up as a user who does not have Internet access? During the day you can let her use the computer in a guest session. I am assuming that during the day you are able to have supervision of her internet activities. It is while you are asleep that is the problem. I am assuming.

The great thing about Ubuntu is that you cannot change the system settings unless your know the administrator password. The one you used when you first installed Ubuntu. 

Are you set up for automatic login? Change it. Then you can login. Your daughter can login under her user name or she can be given a guest session by you which you can supervise.  Do not have wireless networking set up to connect automatically. Remove Available to all Users from the connection.

Regards.

---

### Post by SeijiSensei on 2010-12-01
> **MysteryPig said:**
> The only other thing I was uncertain about was  how to "set up a static IP configuration in Ubuntu", and why I would need to do that.

*I have a dynamic IP btw

OK, DHCP it is.  Edit as root the file /etc/network/interfaces as follows:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


```

This enables you to use "sudo ifup eth0" and "sudo ifdown eth0" to control the interface.

This was news to me until I read [this part of the server manual]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") just now.  So I'm going to revise the script above like this:

```

# check to see if networking is permitted
if [ $NOW -ge $STIME -a $NOW -le $ETIME ]
then
    # permissible time; check if already up; if not, restart
    if [ "$NET_CHECK" = "" ]
    then
        ifup $INT
    fi

else
     # not allowed now; disconnect if needed
     if [ "$NET_CHECK" != "" ]
     then
         ifdown $INT
     fi

fi

```

My approach grants control over the network interface to the root user and removes it from the control of the logged-in user.  It's premised on the computer obtaining its IP address before someone logs in.  That's not the case for Ubuntu desktop; the user initiates the network connection using an applet. 

So as grahammechanical points out, removing the NetworkManager applet from the user's interface makes it harder for a naive user to connect to the network.  I've advocated that solution in other postings myself.  Still there's nothing to prevent the ambitious teenager from figuring out how to create a network connection herself.  Reinstalling NetworkManager is one possibility, but there are certainly other ways.

If all you want to do is control access by time-of-day, then cybergnome's suggestion is the simplest.  Use your router to control access.  If it doesn't offer that option, I'd spend the $50 or less to get a decent router that can run an open-source firmware like [DD-WRT]("http://www.dd-wrt.com/site/index") or [tomato]("http://www.polarcloud.com/tomato").

---

### Post by MysteryPig on 2010-12-02
> # check to see if networking is permitted
if [ $NOW -ge $STIME -a $NOW -le $ETIME ]
then
    # permissible time; check if already up; if not, restart
    if [ "$NET_CHECK" = "" ]
    then
        ifup $INT
    fi

else
     # not allowed now; disconnect if needed
     if [ "$NET_CHECK" != "" ]
     then
         ifdown $INT
     fi

fi


I enter this into monitor_time or /etc/network/interfaces?

---

### Post by SeijiSensei on 2010-12-02
> **MysteryPig said:**
> I enter this into monitor_time or /etc/network/interfaces?

It replaces the nearly identical block of code in the original monitor_time script.  All I did was replace the commands for "/etc/init.d/networking" with "ifup/ifdown".  This limits the effects of the script to just the Ethernet interface.

---

### Post by Spyderkid on 2010-12-02
You could just go into the browser type the I.P of your router (usually 192.168.0.1) and then just change the schedule so it switches the router off at lets say 11:00pm and turns it on at 7:00am also this would save alot of energy (and therefore money).

---

### Post by MysteryPig on 2010-12-02
Spyderkid: I do not have a router.

SeijiSensei: what part of the code do I need to edit?


Thanks for all the help.

---

### Post by SeijiSensei on 2010-12-02
> **MysteryPig said:**
> Spyderkid: I do not have a router.

Are you doing NAT firewalling on another box, or is the Ubuntu box directly on the Internet?  If so, are you running a firewall?

> SeijiSensei: what part of the code do I need to edit?

I'll reproduce the entire script with the changes inserted:

```

#!/bin/bash
# script to control access to network by time-of-day

# enter parameters here
START='0700'  # start permitting access in 24-hour clock time
STOP='2130'
INT='eth0'    # interface name; usually eth0 for wired, wlan0 for wireless

####  nothing else to configure ####

# check if network up
NET_CHECK=$(/sbin/ifconfig $INT | grep 'inet addr')

TODAY=$(date +%D)
TSTART="$START $TODAY"
TEND="$STOP $TODAY"

STIME=$(date +%s --date="$TSTART")
ETIME=$(date +%s --date="$TEND")
NOW=$(date +%s)

# check to see if networking is permitted
if [ $NOW -ge $STIME -a $NOW -le $ETIME ]
then
    # permissible time; check if already up; if not, restart
    if [ "$NET_CHECK" = "" ]
    then
        ifup $INT
    fi

else
     # not allowed now; disconnect if needed
     if [ "$NET_CHECK" != "" ]
     then
         ifdown $INT
     fi

fi

exit 0

```

I also added double quotes around the --date= parameters.  I don't think they earlier version would have worked correctly without them. The contents of TSTART and TEND have embedded spaces between the time and date.

---

### Post by MysteryPig on 2010-12-02
So your saying that the ONLY thing that I need to edit from the text you just gave me is 0700 and 2130 to my desired blocked times?

---

### Post by MysteryPig on 2010-12-03
This works perfectly. Thank you very much for your time.

---

### Post by SeijiSensei on 2010-12-04
> **MysteryPig said:**
> This works perfectly. Thank you very much for your time.

Wow, it really works as advertised?  I have to admit I didn't subject the script to much in the way of testing. :D

You're welcome, MysteryPig.

---

