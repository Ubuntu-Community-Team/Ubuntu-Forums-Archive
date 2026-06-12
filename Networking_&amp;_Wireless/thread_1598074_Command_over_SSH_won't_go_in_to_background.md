---
title: "Command over SSH won't go in to background"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by buee on 2010-10-16
Ok, so this one baffles me.  I'm trying to get a script to do internal speed tests on demand.  I'm using iperf.  The bash commands are below.

```
#!/bin/bash

set -ax

desktoppath="/home/buee/Desktop"
iperfserver=192.168.111.230
killfile="/home/buee/Desktop/Kill.txt"

echo 
echo "Please input the customer's name..."
read customer
clear

ssh buee@$iperfserver < $killfile
ssh buee@$iperfserver "iperf -s"
sleep 2
xterm -e "iperf -c $iperfserver -t 20 -i 2 -r -d > $desktoppath/$customer"
sleep 2
kill `ps aux | grep iperf | awk '{print $2}' | head -1`
ssh buee@$iperfserver < $killfile

ssh buee@$iperfserver "iperf -s -u" &
sleep 2
xterm -e "iperf -c -u $iperfserver -t 20 -i 2 -r -d >> $desktoppath/$customer"
sleep 2
kill `ps aux | grep iperf | awk '{print $2}' | head -1`
ssh buee@$iperfserver < $killfile

exit 0
```

The first portion:

```
ssh buee@$iperfserver < $killfile
ssh buee@$iperfserver "iperf -s"
sleep 2
xterm -e "iperf -c $iperfserver -t 20 -i 2 -r -d > $desktoppath/$customer"
sleep 2
kill `ps aux | grep iperf | awk '{print $2}' | head -1`
ssh buee@$iperfserver < $killfile
```

works beautifully, no issues at all.

But the second part:

```
ssh buee@$iperfserver "iperf -s -u" &
sleep 2
xterm -e "iperf -c -u $iperfserver -t 20 -i 2 -r -d >> $desktoppath/$customer"
sleep 2
kill `ps aux | grep iperf | awk '{print $2}' | head -1`
ssh buee@$iperfserver < $killfile
```

Gives me this:

```
+ ssh buee@192.168.111.230 'iperf -s -u'
+ ssh buee@192.168.111.230 'bg 1'
------------------------------------------------------------
Server listening on UDP port 5001
Receiving 1470 byte datagrams
UDP buffer size:   112 KByte (default)
------------------------------------------------------------
bash: line 0: bg: no job control
+ sleep 2
+ xterm -e 'iperf -c -u 192.168.111.230 -t 20 -i 2 -r -d >> /home/buee/Desktop/Test'
+ sleep 2
++ ps aux
++ grep iperf
++ awk '{print $2}'
++ head -1
+ kill 3420

```

The only difference between the iperf command in portion A and portion B is B has a -u switch in there that will test with UDP protocol.  I figured since I got some output, I'd try sending the command to the back.  This process will not go to the background.  I tried tacking a '&' to the end of it, I tried following it up with a 'bg 1' through SSH immediately after, I tried "iperf -s -u && bg" as well as "... && bg 1", I tried opening it in a different terminal window on the remote machine, I tried opening it on a different bash shell on the remote machine, nothing seems to help.  The following command issued on the local machine completes in less than a second, but it doesn't make sense because it's not picking up a server on the other side of the connection, it should at least have a few seconds to timeout, not just proceed.  Any ideas?

---

### Post by buee on 2010-10-16
Here's the script:

```
#!/bin/bash

set -ax

desktoppath="/home/buee/Desktop"
iperfserver=192.168.111.230
myip=192.168.111.152
killfile="/home/buee/Desktop/Kill.txt"

echo 
echo "Please input the customer's name..."
read customer
clear

ssh buee@$iperfserver < $killfile
ssh buee@$iperfserver "iperf -s" &
sleep 15
xterm -e "iperf -c $iperfserver -t 20 -i 2 -r > $desktoppath/$customer"
sleep 30
cat $killfile
ssh buee@$iperfserver < $killfile

ssh buee@$iperfserver < $killfile
ssh buee@$iperfserver "iperf -u -s -D" &
sleep 15
[B]iperf -c $iperfserver -t 20 -i 2 -r -u >> $desktoppath/$customer &
sleep 60[/B]
kill -9 `ps aux | grep iperf | awk '{print $2}' | head -1`
ssh buee@$iperfserver < $killfile

cat $killfile
xterm -e "iperf -s" &
sleep 10
ssh buee@$iperfserver "iperf -c $myip -t 20 -i 2 -r" >> $desktoppath/$customer
sleep 30
ssh buee@$iperfserver < $killfile
sleep 10
cat $killfile
sudo kill -9 `ps aux | grep xterm | grep -v grep | awk '{print $2}' | head -1`
sudo kill -9 `ps aux | grep xterm | grep -v grep | awk '{print $2}' | head -1`
sudo kill -9 `ps aux | grep xterm | grep -v grep | awk '{print $2}' | head -1`

exit 0
```

Now my only problem is with the output of those commands to the file on my Desktop.  It seems to not finish the output.  And at the end of the command in section 2, which is bolded, has pertinent information at the very end, jitter, packet loss, etc.  I did expand the sleep commands thinking maybe the processes were getting killed early, but there was absolutely no change, not even an extra line.  Any thoughts on that one?

---

