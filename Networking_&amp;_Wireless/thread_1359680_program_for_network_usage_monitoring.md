---
title: "program for network usage monitoring"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by Esthellin on 2009-12-20
As for most people, they have a monthly limit on the amount of downloading they can do. I want a program of some sort which can show me how much I have downloaded (not my network traffic, which shows computer-computer 'talk' instead of only internet usage) during the day, and totals over the month.

So far, the network history built into the system monitor in jaunty shows a total sent/recieved, but it includes network traffic, which is not wanted. This gives me an incorrect value for what I have downloaded. Also, this number is reset if the computer is turneded off. I need to know the amount I download daily so I can see how close I am to my monthly limit.

Any suggestions?

Thanks much for the help :)

---

### Post by shredder12 on 2009-12-22
I had a similar issue..
And I went with [vnstat]("http://linuxers.org/article/monitor-your-internet-traffic-stats-using-vnstat") even though it gives the total network traffic data.. it ofcourse won't satisfy your needs but it manages the data pretty well. so it might give you a rough idea..

Just adding one more thing.- i think the "received bytes" of the network traffic is the amount of data downloaded..

---

### Post by Esthellin on 2009-12-28
> **shredder12 said:**
> I had a similar issue..
And I went with [vnstat]("http://linuxers.org/article/monitor-your-internet-traffic-stats-using-vnstat") even though it gives the total network traffic data.. it ofcourse won't satisfy your needs but it manages the data pretty well. so it might give you a rough idea..

Just adding one more thing.- i think the "received bytes" of the network traffic is the amount of data downloaded..

I haven't yet tested vnstat but I will be soon.
I suppose the most important value I need is the amoun of data downloaded per day, to keep track of download limits over the month. If it is including normal network traffic, it just means I have a bit more leeqay ;D.

Any ideas what programs have the feature of keeping track of daily, weekly, monthly usage?

---

### Post by iponeverything on 2009-12-28
I just discovered vnstat.. I too have bandwidth cap that I have to watch --  ppp0 is just my Internet traffic. Vnstat is pretty cool:

```

root@gateway:~# vnstat -d

 ppp0  /  daily

    day         rx      |     tx      |  total
------------------------+-------------+----------------------------------------
   23.12.     47.72 MB  |    8.14 MB  |   55.86 MB   %%%%:
   24.12.     51.42 MB  |    8.61 MB  |   60.02 MB   %%%%%:
   25.12.    173.55 MB  |   44.38 MB  |  217.93 MB   %%%%%%%%%%%%%%%%%%::::
   26.12.    196.25 MB  |   48.53 MB  |  244.78 MB   %%%%%%%%%%%%%%%%%%%%:::::
   27.12.    115.12 MB  |   17.89 MB  |  133.01 MB   %%%%%%%%%%%::
   28.12.     14.01 MB  |    3.33 MB  |   17.33 MB   %
------------------------+-------------+----------------------------------------
 estimated       29 MB  |       6 MB  |      35 MB

root@gateway:~# vnstat -w

        ppp0  /  weekly

                            rx      |       tx      |    total
        ----------------------------+---------------+--------------
          last 7 days    608.35 MB  |    132.92 MB  |    741.27 MB
            last week    584.07 MB  |    127.54 MB  |    711.61 MB
         current week     24.29 MB  |      5.37 MB  |     29.66 MB
        ----------------------------+---------------+--------------
            estimated       310 MB  |        64 MB  |       374 MB

root@gateway:~# vnstat -m

 ppp0  /  monthly

   month         rx      |      tx      |   total
-------------------------+--------------+--------------------------------------
  Dec '09     608.35 MB  |   132.92 MB  |   741.27 MB   %%%%%%%%%%%%%%%%%%::::
-------------------------+--------------+--------------------------------------
 estimated       684 MB  |      148 MB  |      832 MB




```

---

### Post by Esthellin on 2009-12-28
This program works great. All the numbers I need :D.

In the manual, it says the program can be run without sudo, however to update the databases, it says:

11:52{~/isaac/Documents/bcs} vnstat -u
Error:
Unable to write database "/var/lib/vnstat/wlan0".
Make sure it's write enabled for this user.
Database not updated.

Is this because I am manually updating instead of letting itself do the updates?

Also, the totals are off. From the System monitor, it has a higher download and upload. This may be due to download before the program. But the "--sync" option supposeduly should fix that, but doesn't.

---

### Post by iponeverything on 2009-12-28
> **Esthellin said:**
> This program works great. All the numbers I need :D.

In the manual, it says the program can be run without sudo, however to update the databases, it says:

11:52{~/isaac/Documents/bcs} vnstat -u
Error:
Unable to write database "/var/lib/vnstat/wlan0".
Make sure it's write enabled for this user.
Database not updated.

Is this because I am manually updating instead of letting itself do the updates?

Also, the totals are off. From the System monitor, it has a higher download and upload. This may be due to download before the program. But the "--sync" option supposeduly should fix that, but doesn't.

It fills the database with via cronjob that runs every 5 minutes and to print the data from the database, you don't need be root. But if you need to do the "-u" you need sudo. If can change the polling to every minute instead of every 5 by editing the vnstat file cron.d/.

Also, System monitor is looking at everything not just one interface.

---

### Post by Esthellin on 2009-12-28
Ah I see. I manage to figure out how to edit the cron.d file. Posting here for other users reference:

# /etc/cron.d/vnstat: crontab entries for the vnstat package
# old line rechecks files every 5 minutes. new line checks every minute
# 0-55/5 *      * * *   root    if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi
0-59 *  * * *   root    if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi

The lower line (as written in the comment) will make the database be updated every minute instead of every five. I commented out the other line in case anything dies :P.

Is there a way of chanign system monitor to show these different interfaces?

Side question: what are the different interfaces (what is the difference between eth0, wlan0 etcetera)?

Thankyou for the prompt anwers

---

### Post by iponeverything on 2009-12-29
> **Esthellin said:**
> Ah I see. I manage to figure out how to edit the cron.d file. Posting here for other users reference:

# /etc/cron.d/vnstat: crontab entries for the vnstat package
# old line rechecks files every 5 minutes. new line checks every minute
# 0-55/5 *      * * *   root    if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi
0-59 *  * * *   root    if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi

The lower line (as written in the comment) will make the database be updated every minute instead of every five. I commented out the other line in case anything dies :P.

Is there a way of chanign system monitor to show these different interfaces?

Side question: what are the different interfaces (what is the difference between eth0, wlan0 etcetera)?

Thankyou for the prompt anwers

use "ifconfig" to see the active interfaces on machine and use "iwconfig" to see the wireless interfaces. 

eth0, eth1, etc. are generally the wired Ethernet connections, but not always.

lo -- this is the loopback interface, in essence the machine uses this to talk to itself.

wlan0, irda0, ppp0 .. are wireless, infra-red, ppp

There is no hard and fast rule dictating what what an interface is based on the name, it's usually depends on the dude that wrote the driver.

You can add additional databases to vnstat using:

```
sudo vnstat -u -i <interface>

```

---

### Post by shredder12 on 2009-12-29
> **Esthellin said:**
> 
In the manual, it says the program can be run without sudo, however to update the databases, it says:

11:52{~/isaac/Documents/bcs} vnstat -u
Error:
Unable to write database "/var/lib/vnstat/wlan0".
Make sure it's write enabled for this user.
Database not updated.


This is because the files /usr/bin/vnstat and /var/lib/vnstat need root permissions..
you can fix this  by changing the permissions..
```
sudo chmod o+x /usr/bin/vnstat
sudo chmod o+wx /var/lib/vnstat
```

I hope that will work..

---

### Post by iponeverything on 2009-12-29
> **shredder12 said:**
> This is because the files /usr/bin/vnstat and /var/lib/vnstat need root permissions..
you can fix this  by changing the permissions..
```
sudo chmod o+x /usr/bin/vnstat
sudo chmod o+wx /var/lib/vnstat
```

I hope that will work..

More often that not there is a good reason that file ownerships and permissions are the way they are. The vnstat binary is already executable by anyone and the default for the databases is that it is already readable by anyone. 

Making the database writeable by "others" opens up an easy path for privilege escalation if a blackhat managed to compromise a regular account on the machine.

---

