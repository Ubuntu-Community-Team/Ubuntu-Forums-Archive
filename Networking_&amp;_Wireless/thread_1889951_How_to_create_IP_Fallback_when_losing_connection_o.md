---
title: "How to create IP Fallback when losing connection on primary ip address"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by Digital-Sniper on 2011-12-02
Hello,

I am currently running Ubuntu 10.04.03 LTS and I run nagios on this machine and so I was thinking the other day since I have 3 DSL lines why not configure IP fallback that way I can always ensure that I am always getting updated regardless of an issue with one of the lines.  I have absolutely no idea how to configure this? or if in fact it is called IP Fallback? but I want to configure the adapter on this machine so that when there is an outage on one of the DSL lines it will immediately change its IP config to the other DSL line thats active.. etc etc.

Any help is much appreciated :D

---

### Post by collisionystm on 2011-12-02
a script that will constantly ping googles dns servers and switch interface configs if the ping fails 4 times in a row


Copy your /etc/network/interfaces file.

Make 3 copies of it and put it into your /opt folder

call them interfaces1 interfaces2 interfaces3

fill each of them out accordingly

Here is a script, i dont think it will work. maybe someone can fill in the missing pieces. It is one i found online a while back and I use it to monitor my servers. Except in mine it sends an email if the pings fail.

This is the only part I am not sure of 

>   if [ $count -eq 0 ]; then
cp  /opt/interface2 /etc/network/interfaces
service networking restartjust copy this whole thing into a file. you can set it to run in your crontab every few seconds. unless someone can make it a service


#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
cp  /opt/**interfaces3** /etc/network/interfaces
service networking restart
  fi
done

#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
cp  /opt/**interfaces2** /etc/network/interfaces
service networking restart
  fi
done

#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
cp  /opt/**interfaces1** /etc/network/interfaces
service networking restart
  fi
done

---

### Post by collisionystm on 2011-12-02
nevermind. fixed it. tested it. works lol.

This does need to be ran as root in order to set the interfaces file and restart networking

so when you crontab, do it with sudo

sudo bash

crontab -e



#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
cp  /opt/**interfaces3** /etc/network/interfaces
/etc/init.d/networking restart
  fi
done

#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
cp  /opt/**interfaces2** /etc/network/interfaces
/etc/init.d/networking restart
  fi
done

#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
cp  /opt/**interfaces1** /etc/network/interfaces
/etc/init.d/networking restart
  fi
done

---

### Post by collisionystm on 2011-12-02
This could help if you want to make it a service

[http://ubuntuforums.org/showthread.php?t=922666](http://ubuntuforums.org/showthread.php?t=922666)

---

### Post by collisionystm on 2011-12-02
I spiced it up a bit. lets have it send you an email to notify you it switched to a new line

#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
if [ $count -eq 0 ]; then
cp /opt/interfaces3 /etc/network/interfaces
/etc/init.d/networking restart
echo "This occured at $(date)" | mail -s "Switched to new DSL line 3" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]
fi
done

#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
if [ $count -eq 0 ]; then
cp /opt/interfaces2 /etc/network/interfaces
/etc/init.d/networking restart
echo "This occured at $(date)" | mail -s "Switched to new DSL line 2" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]
fi
done

#!/bin/bash
HOSTS="8.8.8.8"
COUNT=4
for myHost in $HOSTS
do
count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
if [ $count -eq 0 ]; then
cp /opt/interfaces1 /etc/network/interfaces
/etc/init.d/networking restart
echo "This occured at $(date)" | mail -s "Switched to new DSL line 1" [EMAIL="myemail@domain.com"]myemail@domain.com[/EMAIL]
fi
done

---

### Post by collisionystm on 2011-12-02
you will need to install mailutils if you want email function

sudo apt-get install mailutils

---

### Post by Digital-Sniper on 2011-12-05
collisionystm,

I can't thank you enough.  That was by far the fastest and best reply I have ever gotten in any forum.  You made my day.


CASE CLOSED.......THANKS........:popcorn:

---

### Post by collisionystm on 2011-12-05
> **Digital-Sniper said:**
> collisionystm,

I can't thank you enough.  That was by far the fastest and best reply I have ever gotten in any forum.  You made my day.


CASE CLOSED.......THANKS........:popcorn:


Your welcome! I had some fun doing it :D

---

