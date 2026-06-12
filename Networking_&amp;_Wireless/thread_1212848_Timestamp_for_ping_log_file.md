---
title: "Timestamp for ping log file"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by defcon3 on 2009-07-14
Hello, 

I am facing a seemingly simple, yet tricky task. I have some issues with the current ISP connection at home. Since I am away during the day, I cannot "capture" all outages. I thought it would be simple to have a ping run every 30 sec and log the activity on one of my machines at the office. However, the simple 
```

ping -T tsonly -i 30 my.machine.org 
```

does a plain file *without* the time stamp (date+time)

```
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15179ms

```

What I would like to achieve is to have a line for each ping, reading something like:

```
**2009-07-14 10:53** 64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=49 time=155 ms
```
 
or at least similar allowing to spot the times of downtime. I read the man page of ping but neither tsonly nor tsandaddr really do what I need. 

Do you know how this can be achieved? Thank you.

---

### Post by pedro_orange on 2009-07-14
You could just append the command date, to the string written to the log file :)

---

### Post by defcon3 on 2009-07-14
Like how? 

date & ping ... > log.txt ? 

Doesn't work. I need ping to feed the file continuously, with 

date; ping result
date; ping result
date; ping result

Surely, I want to utilise the ping delay option, so this is done every 30/60/120 seconds... 

Can you write down your idea of an appended command line for this? Thank you

---

### Post by nozyczek on 2009-11-21
> **defcon3 said:**
> 
 
... or at least similar allowing to spot the times of downtime ...

Try this:


```
#!/bin/ksh
LOG_LOCATION=/var/log/internet_down/
LOG_NAME=$(date +%y%m%d)_internet_down.out

server[1]=192.168.1.1
server[2]=www.google.com
server[3]=www.cisco.com

for i in 1 2 3
do
        pingDown=$( ping -c 1 ${server[$i]} | grep Unreachable)

        if [[ $pingDown = *Unreachable* ]]
        then
                time=$(date +%H%M:%S)
                date=$(date +%F)
                print $date $time "-" ${server[$i]} "is Down" >> $LOG_LOCATION$LOG_NAME
        fi
done
```


You may need to change 
LOG_LOCATION=/var/log/internet_down/
to a different location

---

### Post by karthick87 on 2011-05-05
The script is not working. Can you help ?

---

### Post by nozyczek on 2011-05-05
> **karthick87 said:**
> The script is not working. Can you help ?

What is the error message?

---

### Post by karthick87 on 2011-05-05
I just want to check it for only one IP ie.192.168.1.10  and i want to save the logs in my Desktop. So how i should change the script ?

---

### Post by karthick87 on 2011-05-08
Can anyone explain these two lines pls,
```

LOG_LOCATION=/var/log/internet_down/
LOG_NAME=$(date +%y%m%d)_internet_down.out

```

---

